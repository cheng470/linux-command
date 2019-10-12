# 安装操作

```sh
# 普通安装
rpm -i example.rpm
# 安装时，显示正在安装的文件信息
rpm -iv example.rpm
# 安装时，显示正在安装的文件信息以及进度
rpm -ivh example.rpm
```

# 查询操作

```sh
# 查询某个是否安装
rpm -qa | grep example
# 查询rpm包详细信息
rpm -qip example.rpm
```