---
layout: default
title: Local Markdown Search 本机助手下载与安装
permalink: /local-markdown-search/native-host/
---

# Local Markdown Search 本机助手下载与安装

Chrome 商店版 Local Markdown Search 需要单独安装本机搜索助手。安装扩展不会自动安装助手；助手只在 Chrome 发起请求时运行。要从搜索结果打开本地文件，还需在 Chrome 扩展详情中开启“允许访问文件网址”。

## 下载一键安装包（1.0.8）

适用于 macOS 和 Windows 的完整安装包已包含一键安装脚本。点击下载、解压后双击对应脚本，安装程序会按需安装运行时、注册助手，并在首次安装时让你选择搜索目录。Chrome 只能下载文件，不能自动执行安装脚本。

安装器同时授权 Chrome 商店版与源码版扩展；重新安装会保留已有搜索目录和索引。安装扩展后，可从弹窗的“安装 / 修复本地助手”入口下载本包，安装完成后回到弹窗点击“重新检测连接”。

- [下载 `local-markdown-search-native-host.zip`](https://github.com/hiqishen/extension-publishing/releases/download/local-markdown-search-v1.0.8/local-markdown-search-native-host.zip)
- SHA-256：`d865cc1620ce86e7b47704709b65dd8a1d5ce251cc254e6c4e58987f9848dbbd`

下载后先按上述 SHA-256 校验文件：

- macOS / Linux（GNU 工具）：`sha256sum local-markdown-search-native-host.zip`
- Windows PowerShell：`Get-FileHash .\local-markdown-search-native-host.zip -Algorithm SHA256`

校验值不一致时，请停止安装。

## macOS 安装

1. 从本页提供的链接下载 ZIP，并先核对 SHA-256。
2. 在 Finder 中解压，双击 `setup-macos.command`。若设备尚未安装 `uv`，安装程序会先询问是否从 `astral.sh` 获取 `uv`；随后 `uv` 可能下载并管理 Python 3.12。首次运行还会让你选择要搜索的目录。
3. 安装程序为当前用户注册本机助手，并打开 Chrome 扩展程序页。确认商店版扩展已安装；若要直接打开 `file://` 文件，在扩展详情中开启“允许访问文件网址”。

macOS 安装脚本和助手未签名，也未经 Apple 公证，Gatekeeper 可能显示拦截或安全提示。先核对本页的官方链接和 SHA-256；若系统提示无法确认文件来源，或你无法核实校验值，请停止安装。确认来源后，只有系统提供允许选项时，才可自行决定是否在“系统设置 > 隐私与安全性”选择“仍要打开”。不要为安装而关闭 Gatekeeper；本包未完成干净设备上的首次下载运行验收。

## Windows 安装

1. 从本页提供的链接下载 ZIP，并先核对 SHA-256。
2. 完整解压后运行 `setup-windows.cmd`。若设备尚未安装 `uv`，脚本会询问是否从 `astral.sh` 获取 `uv`；随后 `uv` 可能下载并管理 Python 3.12。首次运行还会让你选择要搜索的目录。
3. 助手安装在当前用户目录，并在当前用户的 Chrome 注册表项中注册。安装程序会打开 Chrome 扩展程序页；确认商店版扩展已安装，并按需开启“允许访问文件网址”。

Windows 安装脚本和助手未进行代码签名，下载或首次运行时 SmartScreen 可能显示警告。先核对本页的官方链接和 SHA-256；若系统提示无法确认文件来源，或你无法核实校验值，请停止安装。仅在系统提供允许选项且你已确认来源时自行决定是否继续；本包未完成实体 Windows Chrome 的首次下载运行验收。

## 卸载与本机数据

卸载 Chrome 扩展不会自动卸载本机助手。卸载助手前先退出 Chrome，再移除 Native Messaging 注册和助手程序。以下是默认安装位置；如果你曾为 Chrome 配置自定义用户数据目录，macOS 的注册清单会位于该目录下的 `NativeMessagingHosts` 文件夹。

**macOS**

- 移除 `~/Library/Application Support/Google/Chrome/NativeMessagingHosts/com.local.md_search.json`。
- 移除 `~/Library/Application Support/LocalMarkdownSearch/native_host.py` 和 `~/Library/Application Support/LocalMarkdownSearch/run_native_host.sh`。

**Windows**

- 在注册表编辑器中移除 `HKEY_CURRENT_USER\Software\Google\Chrome\NativeMessagingHosts\com.local.md_search` 项。
- 在 `%LOCALAPPDATA%\LocalMarkdownSearch\` 中移除 `native_host.py`、`run_native_host.cmd` 和 `NativeMessagingHosts` 文件夹。

上述步骤会移除助手注册和程序，但会保留 `%LOCALAPPDATA%\LocalMarkdownSearch\` 或 `~/Library/Application Support/LocalMarkdownSearch/` 中的 `config.json` 与 `index.sqlite3`。若要同时清除已保存的搜索目录、索引和选择记录，可在卸载助手后自行删除整个 `LocalMarkdownSearch` 数据文件夹。删除该文件夹不会删除原有 Markdown 文件。扩展偏好设置由 Chrome 单独管理。

更多数据处理说明见[隐私说明]({{ '/local-markdown-search/privacy/' | relative_url }})。
