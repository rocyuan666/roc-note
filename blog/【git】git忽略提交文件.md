git提交忽略文件通常会使用`.gitignore`来解决，但是这种方案只能对git未跟踪的文件有效，git已经跟踪的文件是无效的；使用以下方案设置关闭git跟踪的文件状态。

# 关闭跟踪

```bash
# 关闭跟踪文件，不提交
git update-index --assume-unchanged /src/xxx.js
# 关闭追踪某个目录下的某种类型文件
git update-index --assume-unchanged /src/*.js
```

# 恢复跟踪

```bash
# 恢复跟踪文件，提交
git update-index --no-assume-unchanged /src/xxx.js
# 恢复追踪某个目录下的某种类型文件
git update-index --no-assume-unchanged /src/*.js
```

# 查看当前关闭跟踪的文件

```bash
# 列出关闭追踪的文件
git ls-files -v | grep '^h\ '
# 提取文件路径
git ls-files -v | grep '^h\ ' | awk '{print $2}'
# 恢复所有文件追踪
git ls-files -v | grep '^h' | awk '{print $2}' |xargs git update-index --no-assume-unchanged
```
