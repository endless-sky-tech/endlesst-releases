# Endless Terminal 下载

CLI 已更新至 **3.1.21**，提供 Linux x64 和 Windows x64 独立可执行文件，用户无需 Node.js/npm。Windows Terminal 维持 3.1.20；Linux AArch64 原生服务和会员云平台维持 3.1.19。安装包使用免费的公开 GitHub Releases 渠道，历史版本保留。

| 目标 | 下载 |
|---|---|
| Windows x64 便携版 | [Endless Terminal 3.1.20](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.20/Endless.Terminal-Portable-3.1.20-x64.exe) |
| Linux AArch64 原生服务 | [3.1.19 压缩包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.19/endlesst-terminal-3.1.19-linux-aarch64.tar.gz) |
| CLI Linux x64（glibc） | [3.1.21 tar.gz](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.21/endlesst-cli-3.1.21-linux-x64.tar.gz) |
| CLI Windows x64 | [3.1.21 ZIP](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.21/endlesst-cli-3.1.21-windows-x64.zip) |

[本次 CLI 附件与 SHA-256 校验](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/v3.1.21)。CLI 使用最新发行版的 `latest.json`，Windows 使用 `terminal.json`。

Hub 协议保持 6，本次不部署云平台。共享会话需桌面 Terminal 3.1.20 或以上；原生服务不提供桌面专属的 `session list/attach`。Ubuntu 桌面仍为预览，本次不发布 Linux 桌面安装包。

## 开始使用

1. 在 [注册页](https://182.92.195.68/account/?register=1) 填写账号、密码和确认密码，在当前页面完成注册。
2. 打开 Terminal 菜单栏的“账号”，输入账号和密码登录；当前设备自动加入账号。
3. 在操作电脑上安装 CLI，执行以下命令：

```sh
endlesst-cli hub login
endlesst-cli hub connect
endlesst-cli doctor
```

按 CLI 提示完成浏览器授权。账号只有一台设备时会自动选中；多台设备时按提示选择，或使用 `--device-name "办公室电脑"`。会员连接无需填写设备 ID、配对码或设备访问秘钥。在 [账号中心](https://182.92.195.68/account/) 可查看设备、用量和已授权客户端；“撤销访问”会立即断开该客户端。

注册在网页完成，Terminal 只负责登录。本机功能无需注册；游客也可启用免费连接，在高级连接设置复制配对信息给 CLI。

游客每台设备每月有 100 MiB 中继，注册免费账号每月 1 GiB，均为 1 台设备、1 路并发，P2P 不计中继流量。设备额度满时仍可登录；退出本机登录保留云端设备归属，解绑在账号中心操作。

正式支付和购买入口保持关闭，商户和价格待确定。

## 安装与升级

Linux x64（glibc），默认安装到 `~/.local/bin`：

```sh
curl -fsSL https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.sh | sh
export PATH="$HOME/.local/bin:$PATH"
endlesst-cli --version
```

Windows x64 PowerShell，默认安装到 `%LOCALAPPDATA%\endlesst-cli`：

```powershell
irm https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.ps1 | iex
& "$env:LOCALAPPDATA\endlesst-cli\endlesst-cli.exe" --version
```

也可下载上方压缩包，解压后在终端直接运行 `endlesst-cli` / `endlesst-cli.exe`。包内包含程序、摘要和许可证，运行时、P2P 原生模块及配套 Skill 均内置，不需要安装 Node.js/npm。安装器支持指定版本、目录、离线文件和保留配置的卸载：Linux 用 `--version`、`--prefix`、`--package`、`--uninstall`；Windows 对应 `-Version`、`-Prefix`、`-Package`、`-Uninstall`。

旧 npm 安装需重新运行上面的新安装器；新清单不使用旧 npm 升级协议。安装器保留用户配置，发现 PATH 优先指向旧命令时会提示。请把新目录放到 PATH 前面，或使用新程序的绝对路径。已安装独立发行版后：

```sh
endlesst-cli update --check
endlesst-cli update
endlesst-cli update --to <已发布的独立版本>
endlesst-cli skill install
```

升级前停止运行中的 `hub daemon`，升级后重新启动，常驻连接会使用新程序。macOS、ARM64、musl 暂未提供独立 CLI 包。

Windows Terminal 可从程序的更新入口下载，或直接下载上方 EXE；退出旧程序后运行新版。原生 Terminal 替换程序后重启。设备身份、注册凭据、用户配置和设备访问秘钥继续沿用。

3.1.21 CLI 通过同一源码提交的 Linux / Windows CI，并在两种原生系统中验收实际独立可执行包：PATH 不含 Node/npm，覆盖离线与在线安装、升级与回退、失败保留原程序、P2P/relay、串口 fixture、daemon 自启动及附着、内置 Skill、卸载与配置保留。硬件使用夹具；本次不发布 Terminal 新版，不重新验收 ECS 或 AArch64 真机。Windows 签名和其他系统的独立 CLI 包仍为后续项。
