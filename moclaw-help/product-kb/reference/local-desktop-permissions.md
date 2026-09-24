---
id: moclaw.reference.local_desktop_permissions
title: Local Desktop 权限
type: reference
product_area: local_desktop
audience: support
status: verified
owner: product
last_reviewed_at: 2026-07-29
source_paths:
  - maxgent/client/desktop/docs/moclaw-desktop.md
  - maxgent/client/webapp/src/lib/desktop-downloads.ts
  - maxgent/client/webapp/src/modules/app-shell/components/desktop-download-overlay.tsx
  - maxgent/client/webapp/src/modules/settings/components/desktop-section-view.tsx
  - maxgent/client/webapp/src/platform/browser/browser-host.ts
  - maxgent/client/desktop/electron/main/capabilities/config-store.ts
  - maxgent/client/desktop/electron/main/capabilities/local-capability-service.ts
  - maxgent/client/desktop/electron/renderer/main/electron-local-desktop-client.ts
  - maxgent/client/desktop/runtime/src/capabilities/fs.rs
  - maxgent/client/desktop/runtime/src/capabilities/bash.rs
applies_to:
  plans: [trial, pro]
  environments: [local, test, prod]
  platforms: [desktop]
---

# Local Desktop 权限

## 可用性

Local Desktop 只由 Electron Desktop 宿主提供。能力请求经受信任的 preload IPC 进入
Electron main，再由 main 调用 Rust sidecar。Desktop 不监听浏览器或移动端连接。

桌面尺寸的浏览器 Web App 只提供 Desktop 安装包入口，不运行本地能力。AI Cloud Computer
Viewer 从 Chat 顶部 Header 右侧的 Cloud Computer 入口打开；Desktop 本地能力设置位于
**Settings > Local Tools**。

本地能力只有在 runtime 宣告对应 capability 后才可用。Desktop 正在运行时，单次能力调用
仍可能超时；超时不等于用户拒绝了操作系统权限。

## 能力边界

| 能力 | 用户含义 | 权限边界 |
|---|---|---|
| `browser.navigate` | 本地浏览器自动化 | 默认使用隔离模式；本地 Chrome 需要远程调试，只控制专用自动化标签页。 |
| `fs.read` 等文件能力 | 本地文件操作 | 固定使用当前 Desktop 用户的 Home 作为根目录，并继续执行路径、符号链接、文件大小和操作系统权限检查。 |
| `clipboard.read` | 读取本地剪贴板 | 剪贴板可能包含敏感信息。 |
| `bash.run` | 执行本地命令 | 在支持的平台上默认开启，开启后命令直接执行；起始工作目录必须位于 Home。 |

这些能力彼此独立。Bash 可以在 **Settings > Local Tools** 中关闭或重新开启。Local
Browser、本地文件、剪贴板和 Bash 不能合并成一句“已获得本地访问权”。

## 本地文件边界

1. Rust runtime 会规范化并检查每个请求路径。
2. 固定文件根目录是当前 Desktop 用户的 Home；范围外路径直接失败，没有产品确认框可以
   临时扩大该范围。
3. 读取、列表、搜索和信息查询会先 canonicalize 完整目标再做边界检查。
4. 写入已有符号链接目标会被拒绝；写入检查目标父目录。
5. 删除和移动会 canonicalize 父目录，但不跟随最后一级符号链接，因此操作链接条目本身；
   删除固定 Home 根本身会被拒绝。
6. 所有操作的中间目录仍会完整解析，经由中间符号链接越过 Home 的请求会失败。
7. 文件读取固定受 50 MB 上限约束。
8. 递归列表和搜索有深度限制，文件操作期间会检查取消信号。
9. Home 根和 50 MB 上限在启动时于内存中生成，不持久化到
   `local-capabilities.json`。
10. Desktop 不再显示逐目录授权确认框，也不保存永久授权目录列表或目录请求历史。
11. 操作系统权限仍然生效。macOS 受保护目录可能需要用户直接前往系统“隐私与安全性”
   调整权限；Desktop 不提供打开系统文件权限设置的应用内快捷入口。

## 文件操作检查

| 操作 | 当前检查 |
|---|---|
| 读取、列表、搜索、信息 | 已存在的请求路径 canonicalize 后必须位于固定 Home 根内。 |
| 写入 | 父目录必须解析到固定 Home 根内，已有符号链接目标会被拒绝。 |
| 删除 | 父目录必须解析到固定 Home 根内；不跟随最后一级符号链接，且拒绝删除固定 Home 根本身。 |
| 移动 | 来源父目录和目标父目录都必须解析到固定 Home 根内；最后一级来源符号链接按链接条目移动。 |

## Bash 边界

- Bash 与文件工具是两套权限面。
- 在支持的平台上，Bash 开启后命令直接执行，不再逐条显示产品确认框。
- 用户可以在 **Settings > Local Tools** 关闭 Bash。
- 起始工作目录会 canonicalize 且必须位于 Home。
- runtime 会清空继承环境，并使用固定的命令 `PATH`。
- 命令仍以 Desktop 用户的系统权限运行，可以引用 Home 之外的绝对路径或调用其他程序；
  起始目录限制不是文件系统沙箱。

不要建议用户用 Bash 绕过操作系统拒绝的文件访问。不需要本地命令执行时，应关闭 Bash。

## 默认配置

| 设置 | 当前策略 | 持久化 |
|---|---|---|
| 文件根目录 | 当前 Desktop 用户的 Home | 启动时在内存中生成，不写入 `local-capabilities.json`。 |
| 文件读取上限 | 50 MB | 启动时在内存中生成，不写入 `local-capabilities.json`。 |
| Browser 模式 | 默认 `isolated` | 用户可在 **Settings > Local Tools** 切换并持久化。 |
| Bash | 支持的平台默认开启 | 用户可切换并持久化；开启后命令直接执行。 |

## 不要这样说

- 不要说安装或运行 Desktop 就获得了不受限制的本地文件访问权。
- 不要让用户等待、批准、撤销或重试产品级目录授权确认；该流程已经删除。
- 不要声称 Desktop 会镜像 macOS 或 Windows 的文件权限状态，或可以替用户打开系统文件
  权限设置。
- 不要把 Bash 的起始工作目录限制描述为文件系统沙箱，也不要让用户等待逐命令确认。
- 不要建议用 Bash 绕过操作系统拒绝。
- 不要说本地 Chrome 可以接管任意已有标签页。
- 不要引导用户寻找 Local Desktop 状态卡、刷新操作或浏览器 loopback 连接；浏览器只保留
  Desktop 安装包入口。
- 不要让用户把私有文件正文、token、Cookie、签名 URL 或完整原始日志粘贴到聊天中。

## 相关条目

- `moclaw.how_to.use_local_desktop`
- `moclaw.troubleshooting.local_folder_permission_denied`
- `moclaw.troubleshooting.local_desktop_disconnected`
- `moclaw.reference.cloud_and_local_tools`
