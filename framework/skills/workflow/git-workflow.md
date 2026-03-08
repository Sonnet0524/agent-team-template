# Git 工作流程

> 🔧 标准的 Git 协作流程

---

## 分支策略

### 分支类型

```
main                    # 主分支，稳定版本
├── develop             # 开发分支（可选）
├── feature/xxx         # 功能分支
├── bugfix/xxx          # 修复分支
└── hotfix/xxx          # 紧急修复
```

### 命名规范

- **功能分支**: `feature/{description}-{number}`
  - 例: `feature/csv-parser-001`
  
- **修复分支**: `bugfix/{description}-{number}`
  - 例: `bugfix/encoding-issue-001`
  
- **紧急修复**: `hotfix/{description}`
  - 例: `hotfix/critical-bug`

---

## 标准工作流程

### 1. 开始新功能

```bash
# 1. 切换到 main 分支
git checkout main
git pull origin main

# 2. 创建功能分支
git checkout -b feature/{description}

# 3. 开发并提交
git add .
git commit -m "feat: 添加 xxx 功能"

# 4. 推送到远程
git push origin feature/{description}

# 5. 创建 Pull Request
# 通过 GitHub CLI 或网页
```

### 2. 提交规范

#### Commit Message 格式

```
<type>: <subject>

<body>

<footer>
```

#### Type 类型

| Type | 含义 | 示例 |
|------|------|------|
| `feat` | 新功能 | `feat: 添加 CSV 解析器` |
| `fix` | 修复 | `fix: 修复编码问题` |
| `docs` | 文档 | `docs: 更新 API 文档` |
| `style` | 格式 | `style: 调整代码格式` |
| `refactor` | 重构 | `refactor: 优化解析逻辑` |
| `test` | 测试 | `test: 添加单元测试` |
| `chore` | 构建/工具 | `chore: 更新依赖` |

#### 示例

```bash
git commit -m "feat: 实现 CSV 解析器

- 支持 UTF-8 和 GBK 编码
- 添加错误处理
- 单元测试覆盖率 85%

Closes #123"
```

### 3. Pull Request 流程

#### 创建 PR

```bash
# 使用 GitHub CLI
gh pr create --title "feat: 添加 xxx 功能" \
             --body "## 变更内容
- 功能1
- 功能2

## 测试
- [ ] 单元测试通过
- [ ] 集成测试通过

## 关联 Issue
Closes #123"
```

#### PR 模板

```markdown
## 变更内容
[描述变更]

## 测试
- [ ] 单元测试通过
- [ ] 集成测试通过
- [ ] 手动测试通过

## 检查清单
- [ ] 代码符合规范
- [ ] 文档已更新
- [ ] 没有破坏现有功能

## 关联 Issue
Closes #[issue-number]
```

### 4. 代码审查

#### Review 检查项

- [ ] 代码逻辑正确
- [ ] 符合编码规范
- [ ] 有适当的注释
- [ ] 测试覆盖充分
- [ ] 没有安全漏洞
- [ ] 性能影响评估

#### Review 意见格式

```markdown
## 总体评价
[总体评价]

## 建议修改
- [ ] [具体问题1] - [建议]
- [ ] [具体问题2] - [建议]

## 小问题（可选）
- [小问题1]
- [小问题2]

## 结论
- [ ] 批准合并
- [ ] 需要修改
```

### 5. 合并代码

```bash
# 方法 1: GitHub 网页合并（推荐）
# 点击 "Merge pull request"

# 方法 2: GitHub CLI
gh pr merge --squash --delete-branch

# 方法 3: 命令行
git checkout main
git pull origin main
git merge feature/xxx
git push origin main
```

---

## 常见场景

### 场景 1: 合并冲突

```bash
# 1. 获取最新代码
git checkout main
git pull origin main

# 2. 切换到功能分支
git checkout feature/xxx

# 3. 合并 main
git merge main
# 解决冲突...

# 4. 提交解决
git add .
git commit -m "merge: 解决合并冲突"

# 5. 推送
git push origin feature/xxx
```

### 场景 2: 撤销提交

```bash
# 撤销最后一次提交（保留修改）
git reset --soft HEAD~1

# 撤销最后一次提交（丢弃修改）
git reset --hard HEAD~1

# 撤销已推送的提交（创建反向提交）
git revert HEAD
git push origin main
```

### 场景 3: 临时保存

```bash
# 保存当前状态
git stash

# 查看 stash 列表
git stash list

# 恢复最近 stash
git stash pop

# 恢复指定 stash
git stash apply stash@{1}
```

---

## 最佳实践

### DO ✅

- ✅ 频繁提交（小步快跑）
- ✅ 写清晰的 commit message
- ✅ 创建 PR 前 self-review
- ✅ 保持 PR 小而专注
- ✅ 及时同步 main 分支
- ✅ 删除已合并的分支

### DON'T ❌

- ❌ 提交未测试的代码
- ❌ 在 main 分支直接开发
- ❌ 提交大文件到仓库
- ❌ 提交敏感信息（密码、密钥）
- ❌ PR 包含多个无关功能
- ❌ 强制推送（force push）

---

## 命令速查

```bash
# 基础操作
git clone <url>
git add <file>
git commit -m "message"
git push origin <branch>
git pull origin <branch>

# 分支操作
git branch                    # 列出分支
git checkout <branch>         # 切换分支
git checkout -b <branch>      # 创建并切换
git branch -d <branch>        # 删除分支
git merge <branch>            # 合并分支

# 查看状态
git status                    # 当前状态
git log --oneline            # 简洁日志
git diff                      # 查看差异
git show <commit>            # 查看提交

# 远程操作
git remote -v                # 查看远程
git fetch origin             # 获取更新
git pull --rebase            # 变基拉取

# GitHub CLI
gh repo view                 # 查看仓库
gh issue list                # 列出 issues
gh pr create                 # 创建 PR
gh pr merge                  # 合并 PR
```

---

**维护者**: PM Agent Framework  
**最后更新**: 2026-03-08
