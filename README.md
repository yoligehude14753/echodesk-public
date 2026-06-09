# EchoDesk

EchoDesk 是一个桌面办公助手。这个仓库是 **公开分发仓库**，用于发布安装包、使用说明和安全公告。

> 重要：EchoDesk 不是开源项目。本仓库不包含完整源码、服务端实现、模型网关凭证或内部部署配置。公开仓库只用于让用户下载安装包并查看使用文档。

## 下载与安装

从本仓库的 [Releases](https://github.com/yoligehude14753/echodesk-public/releases) 下载最新版本：

- macOS：下载 `EchoDesk-*-mac-*.dmg`
- Windows：下载 `EchoDesk-*-win-*.exe`

安装后打开 EchoDesk，进入「设置 → 远程服务」，填写：

```text
服务网关地址：https://echodesk.yoliyoli.uk
访问 Key：由维护者单独分发给你的 key
```

保存后即可使用联网能力，包括主 LLM、fast LLM、语音转文字、文字转语音和文档生成。

## 为什么需要 Access Key

EchoDesk 的公网能力通过 `echo-gateway` 提供。真实的 Yunwu / heyi-bj 服务密钥只保存在服务端，不会写进客户端，也不会出现在这个公开仓库。

客户端只保存你的 Access Key：

```text
EchoDesk App --(Access Key)--> echo-gateway --(真实服务凭证)--> Yunwu / heyi-bj
```

没有 Access Key，或 Key 错误 / 被吊销时，联网接口会返回 `401`。

## 关于 `https://echodesk.yoliyoli.uk`

`https://echodesk.yoliyoli.uk` 是 API 网关，不是网页。

- 直接打开根路径 `/` 返回 `{"detail":"Not Found"}` 是正常现象。
- 健康检查地址是 `https://echodesk.yoliyoli.uk/health`。
- EchoDesk 客户端实际调用 `/v1/chat/completions`、`/v1/audio/speech`、`/v1/audio/transcriptions` 等接口。

## 安全说明

只从本仓库 Releases 下载安装包。不要运行第三方转载的安装包，尤其是陌生仓库中的压缩包或“破解版”。

每个 Release 会尽量附带 `SHA256SUMS.txt`。下载后可校验：

```bash
shasum -a 256 EchoDesk-*
```

macOS / Windows 可能因为未签名安装包显示安全警告。确认来源是本仓库 Releases 后再继续安装。后续版本会接入代码签名和公证。

## 许可证

EchoDesk 是闭源专有软件。详见 [`LICENSE.md`](LICENSE.md)。

