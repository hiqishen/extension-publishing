---
layout: default
title: Markdown Plus 本地助手下载与安装
permalink: /markdown-plus/native-host/
---

# Markdown Plus 本地助手下载与安装

本地助手让 Chrome 商店版 Markdown Plus 将 `file://` Markdown 的修改写回原文件，并显示本地目录中的 Markdown 文件。仅需为当前用户安装一次；安装扩展本身不会自动安装助手。使用前还需在 Chrome 的扩展详情中开启“允许访问文件网址”。

**下载状态：本页所述用户级 ZIP 尚未开放下载。** 各平台 ZIP 的公开下载链接和 SHA-256 校验值会在发布并完成对应平台安装、Chrome 调用和卸载验证后列出。请勿从第三方站点寻找或下载声称属于 Markdown Plus 的助手。

## 选择安装包

| 系统 | 架构 | 下载 |
| --- | --- | --- |
| macOS | Apple Silicon（arm64） | 待发布 |
| macOS | Intel（x64） | 待发布 |
| Windows | x64 | 待发布 |
| Windows | ARM64 | 待发布 |

这些安装包包含独立运行的本地助手。无需另装 Node.js 或 Bun，也无需管理员权限。它没有独立的 `.app` 或 `.pkg`，不会常驻后台；Chrome 只在扩展请求时启动助手进程。

## macOS 安装与卸载

**计划提供的 macOS ZIP 未签名、未经 Apple 公证。下载后，Gatekeeper 可能拦截安装脚本或助手程序。** 确认安装包来自本页公布的下载位置后，如 macOS 阻止打开，需由用户按系统提示在“系统设置”→“隐私与安全性”中手动允许对应程序；若无法确认来源或无法完成系统许可，请停止安装。安装脚本不会关闭 Gatekeeper，也不会移除文件的 quarantine 属性。

1. 下载与 Mac 架构相符的 ZIP，并在 Finder 中解压。
2. 打开解压出的 `Markdown Plus Native Host` 文件夹，运行 `install.command`；如被系统拦截，按上面的提示手动处理。
3. 在 `chrome://extensions/` 中重新加载 Markdown Plus，并在扩展详情中开启“允许访问文件网址”。
4. 打开一个本地 Markdown 文件，尝试目录浏览或保存，确认助手可用。

安装程序只在当前用户目录放置助手和 Chrome Native Messaging 注册清单。卸载时，运行**同一 ZIP** 解压文件夹中的 `uninstall.command`；请保留该 ZIP 或解压文件夹，以便日后卸载。

## Windows 安装与卸载

**计划提供的 Windows ZIP 未进行代码签名。** 下载或首次运行时，Windows 可能显示 SmartScreen 警告。请先核对下载来源；如果无法确认来源，请停止安装。

1. 下载与 Windows 架构相符的 ZIP，完整解压后，在解压文件夹中运行 `install.cmd`。
2. 在 `chrome://extensions/` 中重新加载 Markdown Plus，并在扩展详情中开启“允许访问文件网址”。
3. 打开一个本地 Markdown 文件，尝试目录浏览或保存，确认助手可用。

安装程序将文件放在当前用户的 `%LOCALAPPDATA%`，并一次性写入当前用户的 HKCU Chrome Native Messaging 注册项。卸载时，运行**同一 ZIP** 解压文件夹中的 `uninstall.cmd`；请保留该 ZIP 或解压文件夹，以便日后卸载。

本地助手的数据处理和删除方式见 [隐私说明]({{ '/markdown-plus/privacy/' | relative_url }})。
