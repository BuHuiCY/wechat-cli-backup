# WeChat CLI 1.6.21 — macOS arm64 binary backup

本仓库备份本机安装的 WeChat CLI **1.6.21**，适用于 macOS Apple Silicon（arm64）。这是已编译程序备份，不是源码仓库。

## 文件

- `wechat-cli-1.6.21-macos-arm64.tar.gz`：包含 `wechat-cli`、`wxkey` 和 `lib/libWCDB.dylib`。
- `SHA256SUMS`：原始程序与压缩包的 SHA-256 校验值。

不包含微信聊天记录、账号配置、数据库、密钥、媒体或其他个人资料。

## 解压与验证

```sh
tar -xzf wechat-cli-1.6.21-macos-arm64.tar.gz
./wechat-cli/wechat-cli --version
```

本机验证主程序返回版本 `1.6.21`；未在其他电脑验证运行。使用前需自行完成必要的本地配置。

## 来源与权利

备份日期：2026-11-13。文件来自已有本地安装，原始上游与许可证尚未核实。本仓库不声明原程序的著作权，也不额外授予其使用或再分发许可。
