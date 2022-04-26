git上传步骤

1.删除其他分支

```bash
git push origin :master #删除远程master分支，不是默认分支
```

2.上传本地文件到github（已经初始化git init）

```bash
git add . #上传本目录中所有文件，添加进仓库
git commit -m "注释" 
git remote add origin git@...
git push -u origin main #把代码上传到GitHub仓库
```

3.错误信息及解决方法

```bash
error: failed to push some refs to 'https://github.com/kingdom-l/Data_Structures_and_Algorithms.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

解决方法：

```bash
git pull origin main
git push origin main
```

