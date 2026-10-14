# Endless 版本发布

Endless 项目所有组件的统一发布渠道，包括 Terminal、CLI、原生服务和 Endless IPC Yocto SDK。

安装包、发行说明、SHA-256 和历史版本见 [GitHub Releases](https://github.com/endless-sky-tech/endlesst-releases/releases)。

## 下载

| 目标 | 下载 |
|---|---|
| Endless IPC Yocto SDK | [5.0.20（2026-10-11）](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/yocto-sdk-5.0.20-2026-10-11) |
| Windows x64 便携版 | [Endless Terminal 3.1.22](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.22/Endless.Terminal-Portable-3.1.22-x64.exe) |
| Linux AArch64 原生服务 | [3.1.19 压缩包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.19/endlesst-terminal-3.1.19-linux-aarch64.tar.gz) |
| CLI Linux x64（glibc） | [3.1.21 tar.gz](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.21/endlesst-cli-3.1.21-linux-x64.tar.gz) |
| CLI Windows x64 | [3.1.21 ZIP](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.21/endlesst-cli-3.1.21-windows-x64.zip) |

## CLI 安装

无需 Node.js/npm，也可下载压缩包后直接运行。

Linux x64（glibc）：

```sh
curl -fsSL https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.sh | sh
export PATH="$HOME/.local/bin:$PATH"
```

Windows x64（PowerShell）：

```powershell
irm https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.ps1 | iex
```

升级：`endlesst-cli update`。运行中的 `hub daemon` 需在升级前停止，升级后重启。

## 连接设备

在 [注册页](https://182.92.195.68/account/?register=1) 创建账号，在 Terminal 登录，再执行：

```sh
endlesst-cli hub login
endlesst-cli hub connect
```

设备与授权管理见 [账号中心](https://182.92.195.68/account/)。
