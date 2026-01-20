# Git 配置与克隆速查手册

---

## 1.首次安装后必做：全局配置
| 配置项 | 命令示例 | 说明 |
|---|---|---|
| 用户名 | `git config --global user.name "ixxoic"` | 提交记录里显示的作者 |
| 邮箱 | `git config --global user.email ixxoic@example.com` | 与 GitHub 账号一致 |
| 默认分支名 | `git config --global init.defaultBranch main` | 新建仓库默认用 main |
| 编辑器 | `git config --global core.editor "code --wait"` | 把 VS Code 当默认编辑器 |
| 查看所有配置 | `git config --global --list` | 检查写对了没 |

> 如果想对某个仓库单独设置，进入该目录后去掉 `--global` 就可以了

---

## 2.凭证管理（免得每次输账号密码）
### 2.1 HTTPS
```bash
# 只用输一次，后续Git会记住
git config --global credential.helper store
```
> 密码会以明文存盘，如果介意可以用 `manager-core`（Win）或 `osxkeychain`（mac）。

### 2.2 SSH
1. 生成密钥  
   ```bash
   ssh-keygen -t ed25519 -C "ixxoic@example.com" 
   ```
2. 把公钥复制到 GitHub  
   - 打印公钥：`cat ~/.ssh/id_ed25519.pub`  
   - 登录 GitHub → Settings → SSH and GPG keys → New SSH key → 粘贴保存。
3. 测试连通  
   ```bash
   ssh -T git@github.com   # 如果看到 “Hi ixxoic! …” 就成功了
   ```
4. 克隆时改用 SSH 地址  
   ```
   git@github.com:用户名/仓库名.git
   ```

---

## 3.克隆的三种常见场景
| 场景 | 命令模板 | ps |
|---|---|---|
| 首次下载自己的仓库 | `git clone git@github.com:ixxoic/Git_guide.git` | SSH 免密 |
| 下载别人的开源仓库 | `git clone https://github.com/user/repo.git` | 无需权限 |
| 只下最近 1 次提交（浅克隆） | `git clone --depth 1 https://github.com/user/repo.git` | 省流量、速度快 |

克隆完成后本地会：
- 自动生成同名文件夹 `Git_guide`
- 自动把远程地址记为 `origin`
- 自动 checkout 默认分支（main/master）

---

## 4.克隆后常用的二次配置
```bash
cd Git_guide
# 让 pull 默认用 rebase，历史更线性
git config pull.rebase true
# push 时只推当前分支
git config push.default current
```

---

## 5.一键检查
- [ ] `git config user.name` 与 GitHub 显示一致  
- [ ] `ssh -T git@github.com` 返回成功信息  
- [ ] 克隆后 `git remote -v` 能看到 origin 指向正确地址  

完成以上步骤，即可在本地与 GitHub 之间双向同步代码。
```