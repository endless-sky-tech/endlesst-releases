# Endless Terminal 下载

CLI、Windows Terminal 和 Linux AArch64 原生服务的正式版本均为 **3.1.18**。安装包公开下载，源码仓库保持私有。使用免费 GitHub Releases 渠道，历史版本附件保留。

| 目标 | 下载 |
|---|---|
| Windows x64 便携版 | [Endless Terminal 3.1.18](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.18/Endless.Terminal-Portable-3.1.18-x64.exe) |
| Linux AArch64 原生服务 | [3.1.18 压缩包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.18/endlesst-terminal-3.1.18-linux-aarch64.tar.gz) |
| CLI 通用 npm 包（Node.js 22+） | [3.1.18 tarball](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.18/endlesst-cli-3.1.18.tgz) |

[全部正式附件与 SHA-256 校验](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/v3.1.18)。CLI 安装与更新使用 `latest.json`，Windows 更新使用 `terminal.json`，均位于最新发行版。

## 注册与登录

在 [云端注册页](https://182.92.195.68/account/?register=1) 填写账号、密码与确认密码，注册在同页完成。随后在 Terminal 侧边栏输入账号和密码登录，当前设备自动加入“我的设备”，默认界面展示设备名称和在线状态。注册在网站完成，Terminal 只登录；不需要填写 deviceId 或配对码。

本机功能无需注册。启用免费连接后，游客每台设备每月有 100 MiB 中继；注册免费账号每月 1 GiB，均为 1 台设备、1 路并发，P2P 不计中继流量。额度满时仍可登录，不自动替换原设备；退出本机登录保留云端设备归属，解绑在账号中心操作。

正式支付和购买入口保持关闭，尚未确定正式价格或开通商户。

## CLI 安装和升级

Linux / macOS：

```sh
curl -fsSL https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.sh | sh
endlesst-cli update
```

Windows PowerShell：

```powershell
irm https://github.com/endless-sky-tech/endlesst-releases/releases/latest/download/install.ps1 | iex
```

仍使用旧 OSS 渠道的 CLI，首次升级指定新的下载渠道：

```sh
ENDLESST_RELEASE_BASE=https://github.com/endless-sky-tech/endlesst-releases/releases endlesst-cli update
```

旧 OSS Windows Terminal 首次迁移请直接下载上方 EXE，退出旧程序再运行新版；后续通过 Terminal 的版本更新入口升级。设备身份、访问秘钥与注册凭据继续沿用。

CLI 连接仍统一经 Hub，已登录账号可以按设备名称配对并保存短名称。设备访问秘钥位于 Terminal 的高级连接设置：

```sh
endlesst-cli hub login --name cloud --official
endlesst-cli hub connect --device-name "办公室电脑" --hub cloud --as office --token-prompt
endlesst-cli doctor --device office
```

本版通过 Linux/Windows 自动回归、八组浏览器验收、真实 Windows 打包程序两次启动退出、AArch64 二进制 QEMU 验收及真实 ECS 注册登录与自动绑定验证。硬件验收使用串口、HID、视频夹具；正式支付待商户和定价就绪后另行验收。
