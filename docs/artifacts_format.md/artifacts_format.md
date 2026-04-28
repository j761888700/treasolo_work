# Artifacts 输出格式（验收标准）

> 这些文件用于让审核/评估“一眼能验收”，也方便你复现 demo。

## 1) artifacts/plan.md
必须包含：
- 背景/目标（3 行内）
- TODO 列表（按文件/步骤拆）
- 验收标准（可观察/可执行）
- 风险点（可选）

## 2) artifacts/diff.patch
- 必须是标准 `git diff` 输出
- 必须可执行：`git apply --check artifacts/diff.patch`

## 3) artifacts/report.md
必须包含：
- 结论：成功/失败/部分完成
- 实际执行的命令（至少 1 条）+ 结果摘要
- 变更摘要（3~10 条 bullet）
- 下一步建议（可选）

## 4) artifacts/pr.md（可选）
- PR 标题
- 变更动机
- 变更点
- 验证方式
- 风险与影响面
