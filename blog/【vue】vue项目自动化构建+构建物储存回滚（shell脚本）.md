## 构建更新，储存每次构建物

```shell
#!/bin/sh

dir_name="project_dir_name" # 克隆项目到本地的文件夹名
git_path="git clone url" # 项目的 git clone 地址
git_branch="master" # 项目的 git 分支
vue_build_dir_name="dist" # vue项目配置打包后的目录名 一般是 dist
vue_build_script="build:prod" # vue项目配置打包的脚本 一般是 build

save_tar_dir="dist_files" # 存放所有构建物文件
remote_files="favicon.ico index.html index.html.gz assets" # 需要删除跟站点下的文件

if [ $# == 0 ]
then
  vue_build_script="build:prod"
else
  vue_build_script=$1
fi

rm -rf ${dir_name}
echo "正在克隆代码..."
git clone ${git_path} ${dir_name} -b ${git_branch} --depth=1
echo "克隆完成"
cd ${dir_name}
echo "正在安装项目依赖..."
npm install
echo "安装项目依赖完成"
echo "正在打包..."
npm run ${vue_build_script}
echo "打包完成"

echo "正在整理资源..."
current_date_time=$(date '+%Y-%m-%d_%H-%M-%S') # 当前日期时间
tar_name="${dir_name}_dist_${current_date_time}" # 构建物名称
tar cvf ${tar_name}.tar -C ./${vue_build_dir_name} .
cd ../

if [ ! -d ${save_tar_dir} ]
then
  mkdir -p ${save_tar_dir}
  echo "存放所有构建物文件目录已创建"
else
  echo "存放所有构建物文件目录已存在"
fi

mv ./${dir_name}/${tar_name}.tar ./
rm -rf ${remote_files}
tar xvf ${tar_name}.tar
mv ${tar_name}.tar ./${save_tar_dir}
rm -rf ${dir_name}
echo "构建更新完成"
```

## 构建物回滚

```shell
#!/bin/sh

remote_files="favicon.ico index.html index.html.gz assets" # 需要删除跟站点下的文件

if [ $# == 0 ]
then
    echo "请传入构建物参数";
else
    rm -rf ${remote_files}
    tar xvf ${1}
    echo "使用了：${1} 构建物"
fi
```
