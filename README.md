# Endless Terminal 下载

CLI、Windows Terminal、Linux AArch64 原生服务及会员云平台均已更新至 **3.1.19**。安装包使用免费的公开 GitHub Releases 渠道，历史版本保留。

| 目标 | 下载 |
|---|---|
| Windows x64 便携版 | [Endless Terminal 3.1.19](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.19/Endless.Terminal-Portable-3.1.19-x64.exe) |
| Linux AArch64 原生服务 | [3.1.19 压缩包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.19/endlesst-terminal-3.1.19-linux-aarch64.tar.gz) |
| CLI 通用 npm 包（Node.js 22+） | [3.1.19 tarball](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.19/endlesst-cli-3.1.19.tgz) |

[全部正式附件与 SHA-256 校验](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/v3.1.19)。CLI 使用最新发行版的 `latest.json`，Windows 使用 `terminal.json`。

本版采用 Hub 协议 6，**CLI 和 Terminal 都需要升级到 3.1.19**。平台已同步更新，旧客户端不能连接新协议。

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

已有 CLI：

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

本版通过 Linux / Windows 全量端到端测试、Windows 实际打包程序、AArch64 QEMU，以及真实 ECS 的注册、登录、自动加入设备、CLI 免填秘钥连接、relay / P2P、令牌刷新和客户端撤销验证。硬件测试使用夹具；正式支付仍待商户和定价就绪后另行验收。
