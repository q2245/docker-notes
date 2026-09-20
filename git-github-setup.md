# Git 与 GitHub 连通教程

## 安装 GitHub CLI

Fedora 上安装：

```bash
sudo dnf -y install gh
```

查看是否已经安装：

```bash
gh --version
```

## 登录 GitHub

使用浏览器授权：

```bash
gh auth login --hostname github.com --git-protocol https --web
```

流程：

1. 终端会显示一个一次性代码，例如 `745D-550F`。
2. 浏览器打开 `https://github.com/login/device`。
3. 输入这个代码。
4. 点击授权后，终端会显示 `Authentication complete`。

检查登录状态：

```bash
gh auth status
```

## 配置 Git 用户信息

建议使用 GitHub 的 `noreply` 邮箱：

```bash
git config --global user.name "springchang"
git config --global user.email "q2245@users.noreply.github.com"
```

查看配置：

```bash
git config --global --list
```

## 创建本地仓库并提交

创建项目目录：

```bash
mkdir -p ~/文档/docker-notes
cd ~/文档/docker-notes
git init -b main
```

新建或编辑 `README.md` 后提交：

```bash
git add README.md
git commit -m "docs: add Fedora 44 Docker installation notes"
```

## 创建 GitHub 仓库并推送

使用 GitHub CLI 创建远端仓库，并把当前本地仓库推上去：

```bash
gh repo create docker-notes --public --source=. --remote=origin --push
```

这条命令完成的事情：

1. 在 GitHub 账号 `q2245` 下创建 `docker-notes` 仓库。
2. 添加远端地址 `https://github.com/q2245/docker-notes.git`。
3. 把本地 `main` 分支推送到 GitHub。
4. 设置 `main` 跟踪 `origin/main`。

查看远端：

```bash
git remote -v
```

## 之后的日常更新流程

每次修改文档后：

```bash
git status
git add .
git commit -m "docs: update notes"
git push
```

## 拉取远端更新

```bash
git pull
```

## 本次实际创建的仓库

仓库地址：

```text
https://github.com/q2245/docker-notes
```

本地位置：

```text
~/文档/docker-notes
```

当前包含两篇文档：

```text
README.md
git-github-setup.md
```
