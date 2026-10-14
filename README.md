# Endless 版本发布

Endless 项目所有组件的统一发布渠道，包括 Terminal、CLI、原生服务和 Endless IPC Yocto SDK。

安装包、发行说明、SHA-256 和历史版本见 [GitHub Releases](https://github.com/endless-sky-tech/endlesst-releases/releases)。

## 下载

| 目标 | 下载 |
|---|---|
| Endless IPC Yocto SDK | [5.0.20（2026-10-11）](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/yocto-sdk-5.0.20-2026-10-11) |
| Windows x64 便携版 | [Endless Terminal 3.1.27](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.27/Endless.Terminal-Portable-3.1.27-x64.exe) |
| Linux AArch64 原生服务 | [3.1.27 压缩包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.27/endlesst-terminal-3.1.27-linux-aarch64.tar.gz) |
| CLI Linux x64（glibc） | [3.1.27 tar.gz](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.27/endlesst-cli-3.1.27-linux-x64.tar.gz) |
| CLI Windows x64 | [3.1.27 ZIP](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.27/endlesst-cli-3.1.27-windows-x64.zip) |

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

升级：`endlesst-cli update`。运行中的 `cloud daemon` 需在升级前停止，升级后重启。

## 连接设备

在 [注册页](https://182.92.195.68/account/?register=1) 创建账号，在 Terminal 登录，再执行：

```sh
endlesst-cli cloud login
endlesst-cli cloud connect
```

设备与授权管理见 [账号中心](https://182.92.195.68/account/)。

## Cloud 协议 8 升级

3.1.27 的 Cloud、CLI、Windows Terminal 和 Linux AArch64 Terminal 必须同步升级。CLI 命令使用 `cloud` 与 `--cloud`，云端 WebSocket 为 `/cloud`。退出旧程序并备份配置后，将 `svr-config.json` 的 `agent.hubUrl` 改为 `agent.cloudUrl`，`account.json` 的 `hub` 改为 `cloud`，`cli-servers.json` 的 `hubs` 改为 `clouds`、设备条目的 `hub` 改为 `cloud`。保留设备身份、注册凭据、访问秘钥、账号令牌与调试档案；旧常驻连接先用旧 CLI 停止，升级后以 `cloud daemon start` 重启。
