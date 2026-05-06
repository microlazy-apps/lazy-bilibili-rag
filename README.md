# lazy-bilibili-rag

[懒猫微服](https://lazycat.cloud) 上的 [bilibili-rag](https://github.com/via007/bilibili-rag) 一键部署 ——
把 B 站收藏夹变成可对话、可检索的知识库。

## 安装

下载最新 lpk：[Releases](https://github.com/microlazy-apps/lazy-bilibili-rag/releases/latest)

```sh
lpk-manager install ./cloud.lazycat.app.bilibili-rag-*.lpk
```

或在懒猫应用商店搜索「Bilibili-RAG」直接安装。

## 首次安装填写

- **DashScope API Key**（必填）—— 阿里云百炼（DashScope）。同时用于 LLM、Embedding、ASR。
  在 https://bailian.console.aliyun.com 申请。
- **LLM 模型**（默认 `qwen3-max`）
- **Embedding 模型**（默认 `text-embedding-v4`）
- **ASR 模型**（默认 `paraformer-v2`）

> 多数模型有免费额度。先用短视频（约 10 分钟）验证流程与费用。

## 使用

装好后访问 `https://bilibili-rag.{你的微服域名}`：

1. 扫码登录 B 站
2. 选择收藏夹 → 同步入库（拉音频 → ASR → 向量化）
3. 在对话窗口提问，命中相关视频片段并给出来源

## 数据持久化

- `/lzcapp/var/persist/` —— SQLite 数据库 + ChromaDB 向量库
- `/lzcapp/var/logs/`    —— 应用日志

## 开发

仓库结构：bilibili-rag 上游以 git subtree 形式存放在 `vendor/bilibili-rag/`，
所有改动以 patch 形式存在 `patches/`。

详细开发说明（patches 工作流、本地构建、发布流程、架构选择）见 [CLAUDE.md](CLAUDE.md)。

## License

MIT。Upstream bilibili-rag (`vendor/bilibili-rag/`) 也是 MIT ——
见 `vendor/bilibili-rag/LICENSE`。
