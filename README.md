# Endless 版本发布

Windows Terminal 当前为 **0.2.4 开发版**，默认下载安装版；CLI 与 Linux AArch64 原生端继续使用已发布的 **0.2.3**。项目处于 0.x 开发阶段，尚未正式发布；原 3.x 为历史构建编号。请使用下方对应产品的版本链接，不使用共享仓库的全局 latest 入口。

Windows Terminal 已有便携版用户请先退出旧程序，安装一次 0.2.4 Setup；配置、设备身份与登录信息保留。之后在“帮助 → 版本更新”下载并校验新版，点击“重启并安装”完成升级。安装会停止当前连接和任务，普通退出不会自动安装。

Endless 项目所有组件的统一发布渠道，包括 Terminal、CLI、原生服务和 Endless IPC Yocto SDK。

安装包、发行说明、SHA-256 和历史版本见 [AtomGit 国内下载](https://atomgit.com/endless-sky-tech/endlesst-releases/releases)与 [GitHub 下载](https://github.com/endless-sky-tech/endlesst-releases/releases)。

## 下载

| 目标 | 下载 |
|---|---|
| Endless IPC Yocto SDK AArch64 | [5.0.20（2026-10-23）](https://atomgit.com/endless-sky-tech/endlesst-releases/releases/yocto-sdk-5.0.20-2026-10-23) |
| Endless IPC Yocto SDK 全平台历史版 | [5.0.20（2026-10-11）](https://atomgit.com/endless-sky-tech/endlesst-releases/releases/yocto-sdk-5.0.20-2026-10-11) |
| Windows x64 安装版（默认） | [Endless Terminal 0.2.4 Setup](https://atomgit.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.4/Endless.Terminal-Setup-0.2.4-x64.exe) |
| Windows x64 便携版（可选） | [Endless Terminal 0.2.4 Portable](https://atomgit.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.4/Endless.Terminal-Portable-0.2.4-x64.exe) |
| Linux AArch64 原生服务 | [0.2.3 压缩包](https://atomgit.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.3/endlesst-terminal-0.2.3-linux-aarch64.tar.gz) |
| CLI Linux x64（glibc） | [0.2.3 tar.gz](https://atomgit.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.3/endlesst-cli-0.2.3-linux-x64.tar.gz) |
| CLI Windows x64 | [0.2.3 ZIP](https://atomgit.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.3/endlesst-cli-0.2.3-windows-x64.zip) |

Windows 安装包已通过本机源码完整回归与隔离 Wine 安装验收；尚未复验原生 Windows 与现场硬件，当前安装包未签名。

## CLI 安装

无需 Node.js/npm，也可下载压缩包后直接运行。

Linux x64（glibc）：

```sh
curl -fsSL https://atomgit.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.3/install.sh | ENDLESST_RELEASE_BASE=https://atomgit.com/endless-sky-tech/endlesst-releases/releases sh
export PATH="$HOME/.local/bin:$PATH"
```

Windows x64（PowerShell）：

```powershell
$env:ENDLESST_RELEASE_BASE = 'https://atomgit.com/endless-sky-tech/endlesst-releases/releases'
irm https://atomgit.com/endless-sky-tech/endlesst-releases/releases/download/v0.2.3/install.ps1 | iex
```

0.2.3 起，CLI 的 `endlesst-cli update` 与 Windows Terminal 内置更新默认优先 AtomGit，网络故障时回退 GitHub。历史版本可重新运行本页对应平台的安装命令。运行中的 `cloud daemon` 需在升级前停止，升级后重启。

安装命令显式指定 AtomGit 下载源，可执行文件及 SHA-256 校验文件均从国内渠道取得。两个仓库分发相同的程序包。CLI 使用 SHA-256 校验；Windows 安装版使用官方 electron-updater 与 latest.yml 的 SHA-512 校验，下载换源锁定同版文件与摘要。历史附件保留原始字节；升级到 0.2.3 后使用新的双渠道自动更新。

## 连接设备

在 [注册页](https://182.92.195.68/account/?register=1) 创建账号，在 Terminal 登录，再执行：

```sh
endlesst-cli cloud login
endlesst-cli cloud connect
```

设备与授权管理见 [账号中心](https://182.92.195.68/account/)。

## Cloud 协议 8 与版本重新起算

0.1.0 的 Cloud、CLI、Windows Terminal 和 Linux AArch64 Terminal 必须同步升级。CLI 命令使用 `cloud` 与 `--cloud`，云端 WebSocket 为 `/cloud`。退出旧程序并备份配置后，将 `svr-config.json` 的 `agent.hubUrl` 改为 `agent.cloudUrl`，`account.json` 的 `hub` 改为 `cloud`，`cli-servers.json` 的 `hubs` 改为 `clouds`、设备条目的 `hub` 改为 `cloud`。保留设备身份、注册凭据、访问秘钥、账号令牌与调试档案；旧常驻连接先用旧 CLI 停止，升级后以 `cloud daemon start` 重启。
