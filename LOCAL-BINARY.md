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

本机验证主程序返回版本 `1.6.21`。使用前需完成本机微信数据库配置。

## 本机语音转写

以下命令使用本仓库备份的 macOS arm64 二进制。已在微信 4.2.0 上验证一条本机已同步的语音，SILK 音频成功解码为 WAV，查询返回了非空的中文转写文本。

先从仓库根目录确认 CLI 能读取本机微信数据库。已有 1.6.21 配置时，`status` 中的 `live_read_ok` 应为 `true`。如需指定配置文件，可在命令前设置 `WECHAT_CLI_CONFIG=/path/to/config.json`。

```sh
./wechat-cli/wechat-cli status --strict-read-only --pretty
./wechat-cli/wechat-cli asr status --pretty
```

下面用 uv 定位 Python 3.12，并通过 [ASR-CONSTRAINTS.txt](ASR-CONSTRAINTS.txt) 固定已实测的依赖。PyAV 19.0.2 与这版 `faster-whisper` 的接口不兼容，即使 ASR 状态显示就绪，也会在读取音频时报错。首次下载 `large-v3` 模型约需 3 GB。

```sh
WECHAT_CLI_ASR_SETUP_PYTHON="$(uv python find 3.12)" \
  PIP_CONSTRAINT="$PWD/ASR-CONSTRAINTS.txt" \
  ./wechat-cli/wechat-cli asr setup --model large-v3
./wechat-cli/wechat-cli asr status --pretty
```

当 `wechat_voice_ready` 为 `true` 时，查询语音消息：

```sh
./wechat-cli/wechat-cli history "联系人或群名" --type voice --view agent --limit 3 --pretty
```

成功时 `data.messages[].voice.transcript.status` 为 `ok`，文字位于 `data.messages[].voice.transcript.text`。语音音频需已同步到本机。这里验证的是本地解码和转写，独立音频导出命令的支持情况仍待确认。

## 来源与权利

备份日期：2026-11-13。文件来自已有本地安装，原始上游与许可证尚未核实。本仓库不声明原程序的著作权，也不额外授予其使用或再分发许可。
