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

CLI 最新正式版为 [3.1.2](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/v3.1.2)，支持会员 `hub login`。

## Terminal 下载

目前提供原有 3.1.1 安装包，保持原始字节：

- [Windows x64 便携版](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.1/Endless.Terminal-Portable-3.1.1-x64.exe)
- [Linux AArch64 原生包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.1/endlesst-terminal-3.1.1-linux-aarch64.tar.gz)
- [全部发行版与校验文件](https://github.com/endless-sky-tech/endlesst-releases/releases)

Windows 新下载渠道的源码已完成，本次没有重新构建 Windows EXE。

会员页：<https://182.92.195.68/account/>。购买暂未开放。
