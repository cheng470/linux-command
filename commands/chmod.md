chmod 修改文件或目录的访问权限。这里分为文件权限和目录权限。

文件权限：
- r: 读取文件内容
- w: 修改文件内容
- x: 执行文件内容

目录权限：
- r: 具有读取目录清单的权限，也就是可以通过 ls 显示目录里面的文件
- w: 在该目录里面：创建、删除目录下的文件或目录。
- x: 表示用户能否进入该目录成为工作目录。


# 例子

```sh
# 查看文件权限
$ ls -l var.sh
-rwxr-xr-x 1 cheng470 cheng470 234 Aug 22 11:06 var.sh

# 修改权限值为 777
$ chmod 777 var.sh
$ ls -l var.sh
-rwxrwxrwx 1 cheng470 cheng470 234 Aug 22 11:06 var.sh

# 修改用户为rwx，群主和其他为rx
$ chmod u=rwx,go=rx var.sh
$ ls -l var.sh
-rwxr-xr-x 1 cheng470 cheng470 234 Aug 22 11:06 var.sh

# 修改为所有人都可写
$ chmod a+w var.sh
$ ls -l var.sh
-rwxrwxrwx 1 cheng470 cheng470 234 Aug 22 11:06 var.sh

# 修改为所有人不可执行
$ chmod a-x var.sh
$ ls -l var.sh
-rw-rw-rw- 1 cheng470 cheng470 234 Aug 22 11:06 var.sh
```