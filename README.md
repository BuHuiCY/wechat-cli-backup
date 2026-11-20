# WeChat CLI：项目源码与本机版本备份

这里集中保存 [huohuoer/wechat-cli](https://github.com/huohuoer/wechat-cli) 的项目快照，以及本机已安装的 WeChat CLI 1.6.21 程序备份。

## 目录导航

| 内容 | 入口 | 说明 |
| --- | --- | --- |
| 下载的项目源码 | [wechat-cli-upstream-a378923.zip](wechat-cli-upstream-a378923.zip) | 完整保留上游当前提交的 51 个文件，未修改内容 |
| 项目中文说明 | 压缩包内 `upstream/README_CN.md` | 上游安装、命令及使用说明 |
| 项目英文说明 | 压缩包内 `upstream/README.md` | 上游原始英文文档 |
| 项目许可证 | 压缩包内 `upstream/LICENSE`（Apache-2.0） | 适用于下载的上游项目 |
| 本机程序备份 | [1.6.21 macOS arm64](wechat-cli-1.6.21-macos-arm64.tar.gz) | 主程序、wxkey、libWCDB.dylib |
| 本机备份说明 | [LOCAL-BINARY.md](LOCAL-BINARY.md) | 内容、解压、版本验证与语音转写说明 |
| 本机备份校验值 | [SHA256SUMS](SHA256SUMS) | 原程序与压缩包 SHA-256 |

## 来源与版本

- 下载来源：https://github.com/huohuoer/wechat-cli
- 快照提交：`a3789232d4f79bf0b30634d9dadbce71e4acd601`
- 整理日期：2026-11-13。
- 上游 `pyproject.toml` 标注版本 **0.2.4**；本机程序返回版本 **1.6.21**。两者对应关系尚未核实，不能把本机程序视为该源码编译的产物。
- 上游文件按原样复制，保留原作者说明、致谢和 Apache-2.0 许可证。该许可证不自动覆盖来源尚未核实的本机二进制。

## 使用与验证范围

下载并解压源码 ZIP 后，请进入 `upstream/` 阅读源码与上游使用说明。源码安装命令需在该目录执行。本次仅整理、备份文件，没有安装或运行上游程序，也没有更改现有微信及 CLI 配置。

1.6.21 备份已在 macOS Apple Silicon 和微信 4.2.0 上验证版本输出、文件完整性，以及一条本地语音的转写。配置与示例见[本机语音转写](LOCAL-BINARY.md#本机语音转写)。`libWCDB.dylib` 依赖本机 Homebrew 的 SQLCipher 和 OpenSSL 4 动态库。

仓库不包含本机微信聊天记录、账号配置、数据库、密钥或私人媒体。

## 源码快照完整性

源码 ZIP 的 SHA-256：`fd5bd64d5ee21a3828f9e68db5f1944433e18becdad86212dfcf3e94dcfa03e7`。压缩包内 51 个文件已与上述上游提交逐个核对一致，包含原始文档、图片、源码和随仓库分发的辅助程序；不包含 `.git` 历史。
