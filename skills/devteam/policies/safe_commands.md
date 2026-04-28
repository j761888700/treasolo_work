# 安全命令策略（MVP）

## 允许（示例）
- git: `git status`, `git diff`, `git apply --check`, `git checkout -b`, `git commit`（仅在显式开启 commit=true 时）
- 文件查看：`ls`, `find`, `cat`, `sed -n`, `python -m compileall`
- 测试/验证：`pytest`, `npm test`, `python -m unittest`

## 禁止（硬禁）
- 破坏性删除：`rm -rf`, `del /f`, `mkfs`, `dd` 等
- 修改系统/敏感目录：`/etc`, `/usr`, `/bin`, `~/.ssh`
- 网络外发密钥/文件：上传私钥、打印环境变量里的密钥
- 任何需要 sudo 的操作
