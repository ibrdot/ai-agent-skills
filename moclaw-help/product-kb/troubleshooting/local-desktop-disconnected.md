---
id: moclaw.troubleshooting.local_desktop_disconnected
title: Local Desktop 不可用
type: troubleshooting
product_area: local_desktop
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-29
source_paths:
  - maxgent/client/desktop/docs/moclaw-desktop.md
  - maxgent/client/webapp/src/lib/desktop-downloads.ts
  - maxgent/client/webapp/src/modules/app-shell/components/desktop-download-overlay.tsx
  - maxgent/client/webapp/src/modules/settings/components/desktop-section-view.tsx
  - maxgent/client/webapp/src/platform/browser/browser-host.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/client/desktop/electron/main/capabilities/local-capability-service.ts
  - maxgent/client/desktop/electron/main/runtime/runtime-supervisor.ts
  - maxgent/client/desktop/electron/main/desktop-api.ts
  - maxgent/client/desktop/electron/renderer/main/electron-local-desktop-client.ts
applies_to:
  plans: [trial, pro]
  environments: [local, test, prod]
  platforms: [desktop]
---

# Local Desktop 不可用

## 直接答案

先确认用户正在 MoClaw Desktop 内操作。浏览器 Web App 和移动端不提供 Local Desktop，
也不会连接本机已安装的 Desktop；在这些宿主中显示不可用属于预期行为。

桌面尺寸的浏览器可从左侧栏底部账号入口旁下载安装包，然后必须在 Desktop 内继续任务。
如果用户已在 Desktop 内，重开应用、重试任务，并检查 **Settings > Local Tools** 中的
Browser 模式或 Bash 开关。文件工具固定使用当前 Desktop 用户的 Home，产品不再显示逐目录
授权确认框或管理永久授权目录。

## 常见原因

- Rust sidecar 未启动、崩溃或重启次数达到上限。
- 任务仍在浏览器 Web App 或移动端运行。
- 文件路径解析到当前 Desktop 用户的 Home 之外，或操作系统拒绝访问。
- Bash 被用户关闭。
- 本地 Chrome 模式未完成远程调试配置。
- 请求超过内容、时间或并发限制。

## 恢复步骤

1. 确认当前窗口属于 MoClaw Desktop，而不是系统浏览器或移动端。
2. 如果尚未安装，在桌面尺寸的浏览器 Web App 中使用账号入口旁的下载图标；该入口在移动端
   和 Desktop 应用内隐藏。
3. 完全退出并重新启动 Desktop，登录后在 Desktop 内重试任务。
4. 打开 **Settings > Local Tools**。Browser 默认使用隔离模式；本地 Chrome 失败时检查
   远程调试配置或切回隔离模式。
5. Bash 在支持的平台上默认开启；如果用户曾关闭且任务确实需要本地命令，可重新开启。开启
   后命令直接执行，不再逐条显示产品确认框。
6. 文件任务需确认路径位于当前 Desktop 用户的 Home 内，并检查操作系统自身的文件权限。
   不要等待产品目录确认框，也不要引导用户去 Settings 查找永久授权目录列表。

## 安全诊断

可以收集应用版本、操作系统、发生时间与时区、runtime 状态、能力名称和脱敏错误文本。
不要索要文件正文、密码、OAuth token、Cookie、API key、签名 URL 或完整原始日志。

## 升级处理

- Desktop 重启后 sidecar 仍不可用。
- 路径位于 Home 内，用户检查相关操作系统权限后同一操作仍然失败。
- 错误表明路径边界异常，或包含用户无法处理的 runtime 细节。

## 不要这样说

- 不要说 MoClaw 默认可以访问用户整台机器。
- 不要让用户等待或管理产品级目录授权；该流程已经删除。
- 不要引导用户寻找 Local Desktop 状态卡、刷新操作或浏览器 loopback 连接；浏览器只保留
  Desktop 安装包入口。
- 不要建议重启 AI Cloud Computer 来修复本机 Desktop runtime。
- 不要建议用 Bash 绕过操作系统拒绝的本地文件访问。

## 相关条目

- `moclaw.how_to.use_local_desktop`
- `moclaw.reference.local_desktop_permissions`
- `moclaw.troubleshooting.local_folder_permission_denied`
