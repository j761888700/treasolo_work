# DeerFlow DevTeam 架构说明

## 一句话
把一个“需求”交给 DeerFlow，系统会像一个小研发团队一样分工协作，最后交付：
- artifacts/plan.md（计划）
- artifacts/diff.patch（补丁）
- artifacts/report.md（报告）
- artifacts/pr.md（可选：PR 文案）

## 多 Agent 分工
- Planner：把需求改写成 TODO + 验收标准（Acceptance Criteria）
- RepoScout：在仓库里定位要改的文件/入口，并给出依据
- Coder：根据定位生成改动（产出 patch / 或直接改文件）
- Tester：跑最小验证命令（有测试就跑测试；没有就跑最小检查）
- Reviewer：审一下 diff，指出风险点/遗漏，必要时让 Coder 补一轮
- Reporter：整理执行过程与最终产物，落盘到 artifacts/

## 数据流（简图）
```
用户输入 task
   |
   v
Planner -> RepoScout -> Coder -> Tester -> Reviewer
   |                                  |
   +--------------> Reporter <---------+
                     |
                     v
          artifacts/plan.md
          artifacts/diff.patch
          artifacts/report.md
          artifacts/pr.md (可选)
```

## 安全策略（MVP）
- 默认不自动 commit/push
- 禁止危险命令（见 skills/devteam/policies/safe_commands.md）
