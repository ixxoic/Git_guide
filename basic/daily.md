
1. **git add** → 把改动放进“暂存区”  
2. **git commit** → 给暂存区拍快照并写日志  
3. **git push** → 把本地快照上传到远程仓库  

---

```
工作目录  →  git add  →  暂存区  →  git commit  →  本地仓库  →  git push  →  远程仓库
```
---
```bash
git status          # 看改了哪些文件
git add .           # 全部放进暂存区
git commit -m "描述" # 写日志
git pull            # 先拉后推，减少冲突
git push            # 上传
```

