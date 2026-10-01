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

CLI 最新正式版为 [3.1.9](https://github.com/endless-sky-tech/endlesst-releases/releases/tag/v3.1.9)，支持会员 `hub login`，所有设备连接统一经 Hub 使用 deviceId，包括同机 CLI。

## Terminal 下载

Windows 最新便携版为 3.1.10，Linux AArch64 原生包为 3.1.11；两者均支持游客免费连接、账号接管和新版 Hub 协议：

- [Windows x64 便携版](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.10/Endless.Terminal-Portable-3.1.10-x64.exe)
- [Linux AArch64 原生包](https://github.com/endless-sky-tech/endlesst-releases/releases/download/v3.1.11/endlesst-terminal-3.1.11-linux-aarch64.tar.gz)
- [全部发行版与校验文件](https://github.com/endless-sky-tech/endlesst-releases/releases)

Terminal 侧边栏“账号 / 会员”统一提供注册、登录和当前设备绑定入口。Windows 回归测试、账号绑定页面与实际打包程序启动验收已通过，匿名下载已校验大小和 SHA-256。

旧 OSS 渠道的 Windows 3.1.1 首次升级时，请直接下载上述新版 EXE，退出旧程序后运行新版；用户目录中的配置继续沿用。新版可在 Devices → 版本更新下载后续版本。旧版附件保留，不覆盖。

会员页：<https://182.92.195.68/account/>。购买暂未开放。

## 按设备 ID 连接

无需注册：先在 Terminal 账号侧边栏点击“启用免费连接”，从本机配对页面获取设备 ID 与访问秘钥，再连接：

```sh
endlesst-cli hub add --name cloud --official
endlesst-cli hub connect --device <deviceId> --hub cloud --token-prompt
endlesst-cli doctor --device <deviceId> --hub cloud
```

账号登录与设备访问秘钥独立。CLI 3.1.3 起不接受 Terminal 地址直连、`--server` 或本机自动发现；旧直连配置需要清理后重新按 Hub 配对。CLI 3.1.9、Windows 3.1.10、Linux AArch64 3.1.11 使用 Hub 协议 4，旧版 CLI 和 Terminal 需要一起升级，已有设备 ID、配置和注册凭据保留。

注册后，在 Terminal 侧边栏点击“绑定当前设备”，到账号页登录并确认接管。现有设备 ID、秘钥、配置和正在运行的连接保留；以后用同一账号登录，原 CLI 设备配置继续沿用：

```sh
endlesst-cli hub login --name cloud
endlesst-cli hub account --hub cloud --json
```

免费额度：游客每台设备每月 100 MiB 中继，注册免费账号每月 1 GiB；均为 1 台设备、1 路并发。按 UTC 自然月统计双向中继载荷，P2P 直连不计中继流量。额度用完后限制新中继连接，现有连接继续运行并计量，可等待下月恢复或使用 P2P。需要更多设备、并发或流量时会提示更高额度；正式价格尚未确定，购买和支付继续关闭。
