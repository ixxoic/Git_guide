# Git 日常速查表（1 页打印版）

| 场景 | 命令 | 备注 |
|---|---|---|
| 首次配置 | `git config --global user.name "你的名字"` &lt;br&gt; `git config --global user.email 你的邮箱` | 一次就够 |
| 新建仓库 | `git init` | 当前目录生成 `.git` |
| 克隆 | `git clone &lt;url&gt;` | 支持 HTTPS / SSH |
| 日常三件套 | `git add .` &lt;br&gt; `git commit -m "描述"` &lt;br&gt; `git push` | 顺序固定 |
| 查看状态 | `git status` / `git status -s` | 简短模式 |
| 拉最新 | `git pull` | 先拉后推，减少冲突 |
| 查看日志 | `git log --oneline -10` | 最近 10 条简洁历史 |
| 差异 | `git diff`（工作区） &lt;br&gt; `git diff --staged`（暂存区） | 退出按 `q` |
| 撤销工作区改动 | `git restore &lt;文件&gt;` | Git 2.23+ |
| 撤销已 add | `git restore --staged &lt;文件&gt;` | 回到未暂存状态 |
| 回退版本 | `git reset --hard &lt;提交ID&gt;` | 当前分支指针后退 |
| 新建分支 | `git switch -c 新分支` | 创建并切换 |
| 切换分支 | `git switch 分支名` | 2.23+ 新命令 |
| 合并分支 | `git merge 分支名` | 把指定分支并到当前分支 |
| 删除分支 | `git branch -d 分支名` | 未合并时用 `-D` 强删 |
| 查看分支 | `git branch -a` | 本地+远程 |
| 标签 | `git tag v1.0` &lt;br&gt; `git push origin v1.0` | 发版常用 |
|  stash 暂存 | `git stash push -m " wip "` &lt;br&gt; `git stash pop` | 临时切换任务 |
| 远程地址 | `git remote -v` | 查看/确认 |
| 改远程地址 | `git remote set-url origin &lt;新url&gt;` | HTTPS ↔ SSH 互切 |
| 冲突解决 | 1. `git status` 找文件 &lt;br&gt; 2. 手工编辑删标记 &lt;br&gt; 3. `git add` &lt;br&gt; 4. `git commit` | 无额外参数 |
| 放弃合并 | `git merge --abort` / `git rebase --abort` | 回到合并前 |
| 清理已合并分支 | `git branch --merged | grep -v 'main\|master' | xargs -n1 git branch -d` | 脚本级 |

