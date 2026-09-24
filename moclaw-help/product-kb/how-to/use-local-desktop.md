---
id: moclaw.how_to.use_local_desktop
title: 使用 Local Desktop
type: how_to
product_area: local_desktop
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-29
source_paths:
  - maxgent/client/desktop/docs/moclaw-desktop.md
  - maxgent/client/desktop/electron/renderer/main/electron-local-desktop-client.ts
  - maxgent/client/desktop/electron/main/desktop-api.ts
  - maxgent/client/desktop/electron/main/capabilities/config-store.ts
  - maxgent/client/desktop/electron/main/capabilities/local-capability-service.ts
  - maxgent/client/webapp/src/lib/desktop-downloads.ts
  - maxgent/client/webapp/src/modules/app-shell/components/desktop-download-overlay.tsx
  - maxgent/client/webapp/src/modules/app-shell/components/desktop-download-overlay-view.tsx
  - maxgent/client/webapp/src/modules/settings/components/desktop-section-view.tsx
  - maxgent/client/webapp/src/platform/browser/browser-host.ts
  - maxgent/client/desktop/runtime/src/capabilities/bash.rs
  - maxgent/client/desktop/runtime/src/capabilities/browser_runtime.rs
applies_to:
  plans: [trial, pro]
  environments: [local, test, prod]
  platforms: [desktop]
---

# 使用 Local Desktop

## 直接答案

Local Desktop 只在 MoClaw Electron Desktop 内可用。请启动 Desktop，并在 Desktop
内的聊天中使用本地浏览器、文件、剪贴板或 Bash 能力。

浏览器 Web App 和移动端不会连接已安装的 Desktop，也不能通过本机端口调用这些能力。
桌面尺寸的浏览器 Web App 只在左侧栏底部账号入口旁提供 Desktop 下载入口；安装并登录后，
必须回到 Desktop 内继续本地任务。该入口在移动端和 Desktop 应用内隐藏。

在 Desktop 内使用 **Settings > Local Tools** 选择 Browser 模式或开关 Bash。
AI Cloud Computer 从 Chat 顶部 Header 右侧的 **Cloud Computer** 入口打开，它与本机
能力是两套独立环境。

## 使用步骤

1. 在桌面尺寸的浏览器中打开 `/chat`。
2. 点击左侧栏底部账号入口旁的 Desktop 下载图标，并选择当前实际显示的安装包。
3. 安装并启动 MoClaw Desktop，在 Desktop 中登录账号并打开聊天。
4. 本地文件任务只能使用当前 Desktop 用户 Home 目录内的路径；系统权限仍然生效，产品不再
   显示逐目录授权确认框。
5. 在支持的平台上，Bash 默认开启，开启后命令直接执行，不再逐条显示产品确认框；相关开关
   位于 **Settings > Local Tools**，不需要本地命令时应将其关闭。
6. Browser 默认使用隔离模式。本地 Chrome 模式需要开启 Chrome 远程调试，只控制专用自动化
   标签页；连接失败时可切回隔离模式。

## 边界

- Local Desktop 与 AI Cloud Computer 是两种独立能力。
- Chat 顶部 Header 右侧的 Cloud Computer 入口只打开云端工作区 Viewer；Desktop
  本地能力设置位于 **Settings > Local Tools**。
- Desktop 会在应用运行期间自动启动并监控本地 runtime；浏览器 Web App 不安装或连接该
  transport。
- 安装 Desktop 不等于获得整机文件访问权。文件工具的固定根目录是当前 Desktop 用户的
  Home，路径还会经过规范化、符号链接和 50 MB 读取上限检查，操作系统权限继续生效。
- 产品不再显示逐目录授权确认框，也不保存永久授权目录列表或提供打开系统文件权限设置的
  应用内入口。
- Bash 与文件工具是两套权限面。Bash 的起始工作目录必须位于 Home，但命令仍以 Desktop
  用户的系统权限运行；这不是文件系统沙箱，也不能作为绕过文件权限的建议。
- 本地 Chrome 只控制专用自动化标签页，不接管用户已有标签页。
- 浏览器 Web App 中看不到 Local Desktop 属于预期行为，不需要启动 Desktop 后刷新网页。
- 下载入口只反映当前可用安装包，不承诺固定的系统或处理器版本数量。

## 本地浏览器说明

- 隔离模式是默认本地浏览器模式。
- 本地 Chrome 模式可能需要通过 `chrome://inspect/#remote-debugging` 开启远程调试，
  但只会创建并控制专用的 MoClaw 自动化标签页，不能接管任意已有标签页。
- 云端浏览器登录态、本地隔离浏览器和用户常规 Chrome 登录态互不自动迁移。

## 本地能力不可用时

- 确认任务打开在 MoClaw Desktop，而不是浏览器 Web App 或移动端。
- 如果本地 runtime 意外停止，完全退出并重开 Desktop，再重试一次。
- 如果 **Settings > Local Tools** 加载失败，使用页面内重试操作并保留可见错误。
- 本地 Chrome 模式失败时，检查远程调试配置或切回隔离模式。

## 不要这样说

- 不要把 Local Desktop 与 AI Cloud Computer 混为一谈。
- 不要引导用户寻找 Local Desktop 状态卡、刷新操作或浏览器到 Desktop 的 loopback 连接；
  这些连接流程已经不存在，但浏览器中的 Desktop 下载入口仍然存在。
- 不要说安装 Desktop 就获得了本地文件访问权。
- 不要让用户等待、批准或管理产品级目录授权；该流程已经删除。
- 不要说使用 Desktop 会自动复用用户普通 Chrome 的已有标签页或登录态。
- 不要建议用 Bash 绕过操作系统拒绝的本地文件访问。

## 相关条目

- `moclaw.reference.local_desktop_permissions`
- `moclaw.troubleshooting.local_folder_permission_denied`
- `moclaw.troubleshooting.local_desktop_disconnected`
