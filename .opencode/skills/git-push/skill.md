---
name: git-push
description: 提交并推送项目到Gitee远程仓库。当用户说"提交项目"、"push到gitee"、"git push"、"上传代码"时使用此skill。
---

# Git Push to Gitee

将当前项目提交并推送到 Gitee 远程仓库 `https://gitee.com/whalefox/yuanlei2026`。

## 步骤

### 1. 检查当前状态

```bash
git status
```

### 2. 添加所有文件到暂存区

```bash
git add -A
```

### 3. 创建提交

```bash
git commit -m "提交项目：高级网页设计课堂实践"
```

如果用户指定了提交信息，使用用户提供的信息。

### 4. 检查远程仓库配置

```bash
git remote -v
```

### 5. 配置远程仓库（如果尚未配置）

如果上一步没有输出或没有 `origin` 远程仓库：

```bash
git remote add origin https://gitee.com/whalefox/yuanlei2026.git
```

如果已有 `origin` 但URL不匹配：

```bash
git remote set-url origin https://gitee.com/whalefox/yuanlei2026.git
```

### 6. 推送到远程仓库

```bash
git push -u origin master
```

如果用户使用的是 `main` 分支而非 `master`：

```bash
git push -u origin main
```

### 7. 验证推送结果

```bash
git status
git log --oneline -5
```

## 注意事项

- 首次推送可能需要输入Gitee的用户名和密码（或配置SSH密钥）
- 如果远程仓库已有内容且历史不一致，可能需要使用 `git push -u origin master --force`（谨慎使用）
- 确保 `.gitignore` 已配置，避免提交不必要的文件（如 `.workbuddy/`）
