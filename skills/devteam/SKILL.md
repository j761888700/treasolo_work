---
name: devteam
version: 0.1.0
description: "DeerFlow 多 Agent 协作：把需求变成 plan/diff/report（可选 PR 文案）"
---

# DevTeam Skill

## 目标
输入一句需求（task），像一个小研发团队一样分工协作，最终交付：
- `artifacts/plan.md`
- `artifacts/diff.patch`
- `artifacts/report.md`
- `artifacts/pr.md`（可选）

## 输入（建议格式）
你可以直接输入自然语言，例如：
> 给 README 增加一段 FAQ；保证输出 artifacts。

可选开关（写在需求里即可）：
- `commit=false/true`：是否本地创建分支并 commit（默认 false，不 push）
- `pr_doc=false/true`：是否生成 `artifacts/pr.md`（默认 true）

## 工作流（角色分工）
按顺序执行：
1. Planner：把需求改写成 TODO + 验收标准（输出到 plan 草稿）
2. RepoScout：定位要改的文件/入口（只找，不写）
3. Coder：生成改动（优先输出 patch）
4. Tester：跑最小验证命令并记录结果
5. Reviewer：审 diff，必要时让 Coder 补一轮
6. Reporter：统一落盘 artifacts（plan/diff/report/pr）

每个角色提示词见：`skills/devteam/prompts/`。

## 安全要求（MVP）
- 默认禁止危险命令（见 `policies/safe_commands.md`）
- 不读取/输出任何密钥
- 默认不 push 到远端
