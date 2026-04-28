# LLM Profiles（模型配置档）

> 目的：MVP 先跑通，不要求你有任何付费 Token。

## Profile A：本地 Ollama（OpenAI 兼容，推荐默认）
Ollama 的 OpenAI 兼容接口：
- Base URL：`http://localhost:11434/v1`
- API Key：随便填（例如 `ollama`，会被忽略）

在 DeerFlow 的 `config.yaml` 里增加一个模型（示例）：
```yaml
models:
  - name: ollama
    display_name: Ollama (OpenAI Compatible)
    use: langchain_openai:ChatOpenAI
    model: llama3.2   # 你本机 ollama 里有啥模型就写啥
    base_url: http://localhost:11434/v1
    api_key: $OPENAI_API_KEY
    temperature: 0.2
    max_tokens: 4096
```
然后在 `.env` 里放一个占位：
```bash
OPENAI_API_KEY=ollama
```

## Profile B：小米 MiMo（拿到 Token Plan 后再启用）
等你申请通过后，把 MiMo 的 `base_url` 和 `api_key` 填到 `config.yaml/.env` 即可切换。

> 注意：不要把真实 key 提交到 GitHub。
