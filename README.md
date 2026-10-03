# Endless Terminal 下载

CLI 与 Windows Terminal 已配套更新至 **3.1.20**；Linux AArch64 原生服务和会员云平台维持 3.1.19。安装包使用免费的公开 GitHub Releases 渠道，历史版本保留。

| 目标 | 下载 |
|---|---|
| Windows x64 便携版 | [Endless Terminal 3.1.20](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.20/Endless.Terminal-Portable-3.1.20-x64.exe) |
| Linux AArch64 原生服务 | [3.1.19 压缩包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.19/endlesst-terminal-3.1.19-linux-aarch64.tar.gz) |
| CLI 通用 npm 包（Node.js 22+） | [3.1.20 tarball](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.20/endlesst-cli-3.1.20.tgz) |

[本次 CLI / Windows 附件与 SHA-256 校验](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/v3.1.20)。CLI 使用最新发行版的 `latest.json`，Windows 使用 `terminal.json`。

Hub 协议保持 6，本次不部署云平台。共享会话需 CLI 与桌面 Terminal 配套升级至 3.1.20；原生服务不提供桌面专属的 `session list/attach`。Ubuntu 桌面仍为预览，本次不发布 Linux 桌面安装包。

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

Linux / macOS：

```sh
curl -fsSL https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.sh | sh
```

已有 CLI（使用自定义 prefix 的 3.1.19 或更早版本，请先用新版安装器传入原 prefix 升级；3.1.20 的 update 保留原安装目录）：

```sh
endlesst-cli update
```

如果 CLI 提示后台进程正在运行，先执行 `endlesst-cli hub daemon stop`，再升级。升级后重新执行 `hub login` 获取本机客户端授权。旧 OSS 渠道首次升级可指定：

```sh
ENDLESST_RELEASE_BASE=https://github.com/endless-sky-tech/endlesst-releases/releases endlesst-cli update
```

Windows PowerShell：

```powershell
irm https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.ps1 | iex
```

Windows Terminal 可从程序的更新入口下载，或直接下载上方 EXE；退出旧程序后运行新版。原生 Terminal 替换程序后重启。设备身份、注册凭据、用户配置和设备访问秘钥继续沿用。

3.1.20 通过对应源码提交的 Linux / Windows CI、实际 Windows 便携 EXE 启动与重启验收，以及隔离安装目录中的 CLI 安装、升级、回退、失败处理、Skill 安装和卸载验收。硬件功能使用夹具；此次未重新验收 ECS 或 AArch64 真机。签名、独立 CLI 可执行文件与 Linux 正式桌面发行仍为后续项。
