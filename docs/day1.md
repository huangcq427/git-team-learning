## 从 main 新建分支并推送到 GitHub 全流程

### 1. 确保在最新的 main 上

```bash
# 切换到 main 分支
git checkout main

# 拉取最新代码
git pull origin main
```

### 2. 创建并切换到新分支

```bash
# 一步完成：创建 + 切换
git checkout -b feature/your-branch-name
```

分支命名建议：

| 类型 | 前缀 | 示例 |
|---|---|---|
| 新功能 | `feature/` | `feature/login-page` |
| 修复 bug | `fix/` | `fix/null-pointer` |
| 热修复 | `hotfix/` | `hotfix/security-patch` |
| 文档 | `docs/` | `docs/api-readme` |

### 3. 开发，修改代码

```bash
# 写代码...
# 改文件...
```

### 4. 提交更改

```bash
# 查看改动
git status

# 添加所有更改（或指定文件）
git add .
# 或
git add src/login.js

# 提交
git commit -m "feat: 添加登录页面"
```

### 5. 推送到 GitHub

```bash
# 首次推送，建立本地分支与远程分支的关联
git push -u origin feature/your-branch-name
```

> `-u`（即 `--set-upstream`）只需要第一次加，之后直接 `git push` 就行。

### 6.（可选）创建 Pull Request

推送后，GitHub 会自动提示创建 PR：

```bash
# 用 GitHub CLI 直接创建 PR
gh pr create --base main --head feature/your-branch-name --title "添加登录页面" --body "描述..."
```

或者直接在 GitHub 网页上点击 **"Compare & pull request"** 按钮。

---

### 完整命令一气呵成版

```bash
git checkout main
git pull origin main
git checkout -b feature/your-branch-name
# ... 开发 ...
git add .
git commit -m "feat: 描述你的改动"
git push -u origin feature/your-branch-name
```

### 后续合并回 main

PR 审核通过后：

```bash
# 合并完成后，切回 main 并清理
git checkout main
git pull origin main

# 删除本地分支
git branch -d feature/your-branch-name

# 删除远程分支（如果需要）
git push origin --delete feature/your-branch-name
```

整个流程就这些，核心就是 **pull → branch → commit → push → PR**。
