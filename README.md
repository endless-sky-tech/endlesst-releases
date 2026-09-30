# Endless Terminal 下载

此仓库提供 Endless Terminal CLI、Windows 便携版和 Linux AArch64 安装包。

## CLI 安装

需要 Node.js 22 或以上版本和 npm。

Linux / macOS：

```sh
curl -fsSL https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.sh | sh
```

Windows PowerShell：

```powershell
irm https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.ps1 | iex
```

新版升级：`endlesst-cli update`。从旧 OSS 渠道安装的 CLI，首次升级请指定新渠道：

```sh
ENDLESST_RELEASE_BASE=https://github.com/endless-sky-tech/endlesst-releases/releases endlesst-cli update
```

CLI 最新正式版为 [3.1.4](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/v3.1.4)，支持会员 `hub login`，所有设备连接统一经 Hub 使用 deviceId，包括同机 CLI。

## Terminal 下载

目前提供原有 3.1.1 安装包，保持原始字节：

- [Windows x64 便携版](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.1/Endless.Terminal-Portable-3.1.1-x64.exe)
- [Linux AArch64 原生包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.1/endlesst-terminal-3.1.1-linux-aarch64.tar.gz)
- [全部发行版与校验文件](https://github.com/endless-sky-tech/endlesst-releases/releases)

Terminal 侧边栏“账号 / 会员”和新下载渠道的源码已完成并验证；Windows EXE 尚未重新构建，3.1.1 包不含新侧边栏。

会员页：<https://182.92.195.68/account/>。购买暂未开放。

## 按设备 ID 连接

先在 Terminal 绑定设备，再登录同一账号并配对设备访问秘钥：

```sh
endlesst-cli hub login --name cloud --official
endlesst-cli hub list --hub cloud --json
endlesst-cli hub connect --device <deviceId> --hub cloud --token-prompt
endlesst-cli doctor --device <deviceId> --hub cloud
```

账号登录与设备访问秘钥独立。CLI 3.1.3 起不接受 Terminal 地址直连、`--server` 或本机自动发现；旧直连配置需要清理后重新按 Hub 配对。免费额度与定价尚未定案，购买继续关闭。
