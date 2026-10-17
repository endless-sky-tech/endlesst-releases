# Endless 版本发布

当前为 **0.2.1 开发版**，项目尚未正式发布。开发阶段使用 0.x，正式发布从 1.0.0 开始；原 3.x 为历史构建编号。请使用 [v0.2.1 开发版](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/v0.2.1)，不使用 GitHub 的正式版 latest 入口。

已安装 3.1.27 的 CLI 请先停止 cloud daemon，再显式运行 `endlesst-cli update --to 0.2.1`，或下载本版安装器；Terminal 退出后手动换用 0.2.1，配置保持。

Endless 项目所有组件的统一发布渠道，包括 Terminal、CLI、原生服务和 Endless IPC Yocto SDK。

安装包、发行说明、SHA-256 和历史版本见 [GitHub Releases](https://github.com/endless-sky-tech/endlesst-releases/releases)。

## 下载

| 目标 | 下载 |
|---|---|
| Endless IPC Yocto SDK | [5.0.20（2026-10-11）](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/yocto-sdk-5.0.20-2026-10-11) |
| Windows x64 便携版 | [Endless Terminal 0.2.1](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.1/Endless.Terminal-Portable-0.2.1-x64.exe) |
| Linux AArch64 原生服务 | [0.2.1 压缩包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.1/endlesst-terminal-0.2.1-linux-aarch64.tar.gz) |
| CLI Linux x64（glibc） | [0.2.1 tar.gz](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.1/endlesst-cli-0.2.1-linux-x64.tar.gz) |
| CLI Windows x64 | [0.2.1 ZIP](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.1/endlesst-cli-0.2.1-windows-x64.zip) |

## CLI 安装

无需 Node.js/npm，也可下载压缩包后直接运行。

Linux x64（glibc）：

```sh
curl -fsSL https://github.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.1/install.sh | sh
export PATH="$HOME/.local/bin:$PATH"
```

Windows x64（PowerShell）：

```powershell
irm https://github.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.1/install.ps1 | iex
```

升级：`endlesst-cli update`。运行中的 `cloud daemon` 需在升级前停止，升级后重启。

## 连接设备

在 [注册页](https://182.92.195.68/account/?register=1) 创建账号，在 Terminal 登录，再执行：

```sh
endlesst-cli cloud login
endlesst-cli cloud connect
```

设备与授权管理见 [账号中心](https://182.92.195.68/account/)。

## Cloud 协议 8 与版本重新起算

0.1.0 的 Cloud、CLI、Windows Terminal 和 Linux AArch64 Terminal 必须同步升级。CLI 命令使用 `cloud` 与 `--cloud`，云端 WebSocket 为 `/cloud`。退出旧程序并备份配置后，将 `svr-config.json` 的 `agent.hubUrl` 改为 `agent.cloudUrl`，`account.json` 的 `hub` 改为 `cloud`，`cli-servers.json` 的 `hubs` 改为 `clouds`、设备条目的 `hub` 改为 `cloud`。保留设备身份、注册凭据、访问秘钥、账号令牌与调试档案；旧常驻连接先用旧 CLI 停止，升级后以 `cloud daemon start` 重启。
