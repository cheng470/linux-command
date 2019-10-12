df 查看磁盘信息

# 例子

```sh
# 打印文件系统信息
$ df
Filesystem                      1K-blocks    Used Available Use% Mounted on
/dev/mapper/rhel-root            39719988 5818956  33901032  15% /
devtmpfs                          5913476       0   5913476   0% /dev

# 打印文件系统信息，大小格式按动态单位显示
$ df -h
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/rhel-root             38G  5.6G   33G  15% /
devtmpfs                         5.7G     0  5.7G   0% /dev
```