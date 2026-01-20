## 1.先识别冲突
```bash
git pull            # 或 git merge / git rebase
```
看到  
```
Auto-merging src/utils.js
CONFLICT (content): Merge conflict in src/utils.js
Automatic merge failed; fix conflicts and then commit the result.
```
说明冲突了。

---

## 2.解决流程

| 步骤 | 命令/操作 | 说明 |
|---|---|---|
| ① 找冲突文件 | `git status` | 列表里 **both modified** 的就是 |
| ② 打开文件手工合 | 用 VS Code / Cursor 打开 | 会看到：<br>`<<<<<<< HEAD`<br>我的代码<br>`=======`<br>远程代码<br>`>>>>>>> main` |
| ③ 留下想要的内容 | 删标记、改代码 | 保证语法正确、逻辑通顺 |
| ④ 告诉 Git 已解决 | `git add src/utils.js` | 标记冲突已处理 |
| ⑤ 完成合并 | `git commit`  （不用再写 -m） | Git 会自动生成 Merge 日志 |
| ⑥ 上传 | `git push` | 远程得到合并后的结果 |

---

## 3.反悔药
- 合到一半想放弃  
  `git merge --abort`  或  `git rebase --abort`
- 已 commit 发现合错  
  `git reset --hard HEAD~1`  （回退一次合并提交）

