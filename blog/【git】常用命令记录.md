```bash
# 提交到暂存区
git add .
# 提交到本地仓库
git commit -m "xxx"
# 拉取
git pull
# 推送到远端
git push


# 查看所有分支（本地与远端）
git branch -a
# 合并分支
git merge branchName
# 删除已经合并的分支
git branch -d 分支名
#删除远程仓库分支
git push origin -d 分支名
# 切换分支 -b新建分支  拉取远端某个分支与之关联
git checkout -b 分支名 origin/分支名


# 查看远程仓库 -v查看详细信息
git remote -v
# 添加本地仓库连接的远端仓库（可连接多个，pull与push需指定远端名，如下）
# git pull origin(远端仓库名) master(远端分支)
# git push origin(远端仓库名) master(远端分支)
git remote add 名字 远端仓库连接


# 添加标签 
git tag 标签名 # 直接给当前的提交版本创建一个标签
git tag 标签名 提交版本号 # 给指定的提交版本创建一个标签
# 删除标签
git tag -d # 删除所有的标签
git tag -d 标签名称 # 删除指定名称的标签
# 标签推送到远程
git push --tags


# 查看提交日志
git log

```
