---
layout: default
title: Markdown Plus 本地助手下载与安装
permalink: /markdown-plus/native-host/
---

# Markdown Plus 本地助手下载与安装

本地助手让 Chrome 商店版 Markdown Plus 将 `file://` Markdown 的修改写回原文件，并显示本地目录中的 Markdown 文件。仅需为当前用户安装一次；安装扩展本身不会自动安装助手。使用前还需在 Chrome 的扩展详情中开启“允许访问文件网址”。

macOS 使用 `markdown-plus-v0.1.4` 助手 ZIP，Windows 继续使用兼容的 `markdown-plus-v0.1.1` ZIP。请只从本页链接下载与设备架构匹配的安装包，并核对下方 SHA-256。

## 选择安装包

| 系统 | 架构 | 下载 ZIP |
| --- | --- | --- |
| macOS | Apple Silicon（arm64） | [下载 macOS arm64]({{ site.github.repository_url }}/releases/download/markdown-plus-v0.1.4/Markdown-Plus-Native-Host-0.1.4-arm64-unsigned-public.zip) |
| macOS | Intel（x64） | [下载 macOS x64]({{ site.github.repository_url }}/releases/download/markdown-plus-v0.1.4/Markdown-Plus-Native-Host-0.1.4-x64-unsigned-public.zip) |
| Windows | x64 | [下载 Windows x64]({{ site.github.repository_url }}/releases/download/markdown-plus-v0.1.1/Markdown-Plus-Native-Host-0.1.1-windows-x64.zip) |
| Windows | ARM64 | [下载 Windows ARM64]({{ site.github.repository_url }}/releases/download/markdown-plus-v0.1.1/Markdown-Plus-Native-Host-0.1.1-windows-arm64.zip) |

下载后可用 SHA-256 核对 ZIP。四个文件的预期校验值为：

```text
43746f644564dca3deff86484a65f587c9fd87d2821f47c11646637b5e58f415  Markdown-Plus-Native-Host-0.1.4-arm64-unsigned-public.zip
3bc13f1c3685d8e9fc1843ae6f6bbef2e00cf79b18837bf3d847f7ebe1482d35  Markdown-Plus-Native-Host-0.1.4-x64-unsigned-public.zip
73c38a2ad316bc90dfbac59810f9da259531b166e0f0461d52bf7a604e2c3f82  Markdown-Plus-Native-Host-0.1.1-windows-x64.zip
727197a4f6a57a2d5f7447aebfbed41e8b4b3793db9f2b4abd96237ae419ad99  Markdown-Plus-Native-Host-0.1.1-windows-arm64.zip
```

这些安装包包含独立运行的本地助手。无需另装 Node.js 或 Bun，也无需管理员权限。它没有独立的 `.app` 或 `.pkg`，不会常驻后台；Chrome 只在扩展请求时启动助手进程。

## macOS 安装、更新与卸载

**macOS 0.1.4 助手在编译后进行了 ad-hoc 签名，并通过严格的签名完整性校验；没有 Developer ID 发布者签名或 Apple 公证。下载后，Gatekeeper 仍可能拦截安装脚本或助手程序。** 确认安装包来自本页公布的下载位置后，只有系统提供“仍要打开”选项时，才由用户自行决定是否在“系统设置”→“隐私与安全性”中允许对应程序；若无法确认来源或无法完成系统许可，请停止安装。安装脚本不会关闭 Gatekeeper，也不会移除文件的 quarantine 属性。

1. 下载与 Mac 架构相符的 ZIP，并在 Finder 中解压。
2. 打开解压出的 `Markdown Plus Native Host` 文件夹，运行 `install.command`；如被系统拦截，按上面的提示手动处理。
3. 在 `chrome://extensions/` 中重新加载 Markdown Plus，并在扩展详情中开启“允许访问文件网址”。
4. 打开一个本地 Markdown 文件，尝试目录浏览或保存，确认助手可用。

更新现有用户级助手时，直接运行新版 ZIP 的 `install.command`。脚本先核对 Chrome 清单和所有权标记，匹配后才替换助手；遇到不属于此助手的注册或文件会拒绝覆盖。助手沿用协议版本 1，可与现有商店扩展配合使用。

arm64 最终包已完成临时用户目录下的安装、重装、连接、目录读取、Markdown 写入、冲突保护和卸载验证；x64 包已完成架构和严格签名校验，尚未完成 Intel Mac 实际运行验证。浏览器下载后的 Gatekeeper 行为与干净设备完整安装流程尚未验证。首次安全提示仍需用户自行处理，不能把 ad-hoc 校验通过视为系统许可。

安装程序只在当前用户目录放置助手和 Chrome Native Messaging 注册清单。卸载时，运行**同一 ZIP** 解压文件夹中的 `uninstall.command`；请保留该 ZIP 或解压文件夹，以便日后卸载。

## Windows 安装与卸载

**Windows ZIP 未进行代码签名。** 下载或首次运行时，Windows 可能显示 SmartScreen 警告。请先核对下载来源；如果无法确认来源，请停止安装。

1. 下载与 Windows 架构相符的 ZIP，完整解压后，在解压文件夹中运行 `install.cmd`。
2. 在 `chrome://extensions/` 中重新加载 Markdown Plus，并在扩展详情中开启“允许访问文件网址”。
3. 打开一个本地 Markdown 文件，尝试目录浏览或保存，确认助手可用。

安装程序将文件放在当前用户的 `%LOCALAPPDATA%`，并一次性写入当前用户的 HKCU Chrome Native Messaging 注册项。卸载时，运行**同一 ZIP** 解压文件夹中的 `uninstall.cmd`；请保留该 ZIP 或解压文件夹，以便日后卸载。

本地助手的数据处理和删除方式见 [隐私说明]({{ '/markdown-plus/privacy/' | relative_url }})。
