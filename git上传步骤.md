git上传步骤

1.删除其他分支

```bash
git push origin :master #删除远程master分支，不是默认分支
```

2.上传本地文件到github（已经初始化git init）

```
git add . #上传本目录中所有文件，添加进仓库
git commit -m "注释" 
git remote add origin git@...
git push -u origin master #把代码上传到GitHub仓库
```

