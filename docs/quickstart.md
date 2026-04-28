# Quick Start（10分钟跑通）

> 目标：用 DeerFlow 跑一次 DevTeam，多 Agent 自动产出 artifacts。

## 0. 准备一个“零 Token”的模型接口（推荐 Ollama）
Ollama 提供 OpenAI 兼容接口：`http://localhost:11434/v1/chat/completions`（`api_key` 只是占位，会被忽略）。

## 1. 安装并启动 DeerFlow（推荐 Docker）
在本机：
```bash
git clone https://github.com/bytedance/deer-flow.git
cd deer-flow
make config
# 按 README/Install.md 的推荐流程初始化并启动
make docker-init
make docker-start
```
启动后默认访问：`http://localhost:2026`

## 2. 配置 DeerFlow 的模型（指向 Ollama）
编辑 deer-flow 根目录 `config.yaml`，用 `langchain_openai:ChatOpenAI` + `base_url` 配 OpenAI 兼容网关。
示例见：docs/llm_profiles.md

## 3. 安装本仓库的 Skill
按 `scripts/install_skill.md` 把 `skills/devteam` 安装到 DeerFlow。

## 4. 跑一个 demo 任务
在本仓库根目录执行：
```bash
bash scripts/devteam_run.sh "给 README 加一段 FAQ，并生成 artifacts"
```

## 5. 看产物
成功后会看到：
- artifacts/plan.md
- artifacts/diff.patch
- artifacts/report.md
- artifacts/pr.md（可选）
