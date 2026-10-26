---
name: github-push
description: 提交并推送项目到GitHub远程仓库。当用户说"提交到github"、"push到github"、"上传到github"时使用此skill。
---

# Git Push to GitHub

将当前项目提交并推送到 GitHub 远程仓库 `https://github.com/tsingdao/yuanlei`（已设置 SSH 公钥，实际推送使用 SSH 地址 `git@github.com:tsingdao/yuanlei.git`）。

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

注意：本项目的 `origin` 远程指向 Gitee（`https://gitee.com/whalefox/yuanlei2026`），**不要修改或覆盖它**，GitHub 使用独立的远程名 `github`。

如果上一步没有 `github` 远程仓库：

```bash
git remote add github git@github.com:tsingdao/yuanlei.git
```

如果已有 `github` 但URL不匹配：

```bash
git remote set-url github git@github.com:tsingdao/yuanlei.git
```

### 6. 推送到远程仓库

```bash
git push -u github master
```

如果用户使用的是 `main` 分支而非 `master`：

```bash
git push -u github main
```

### 7. 验证推送结果

```bash
git status
git log --oneline -5
```

## 注意事项

- 已设置 SSH 公钥，优先使用 SSH 地址 `git@github.com:tsingdao/yuanlei.git`；如果 SSH 连接失败（如 22 端口被防火墙拦截），可改用 HTTPS 地址 `https://github.com/tsingdao/yuanlei.git`（需凭据管理器或个人访问令牌）。
- 首次连接 GitHub 时可能出现 host key 验证提示（`The authenticity of host 'github.com' can't be established`），输入 `yes` 继续即可。
- 不要使用 `--force` 强推，除非用户明确要求。
- 确保 `.gitignore` 已配置，避免提交不必要的文件。
