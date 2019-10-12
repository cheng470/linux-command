man (Manual) 查询命令的说明文档。

# 例子

```
# 查 date 命令的用法，最简单也是最常用
man date
```

## 查询特定的手册页面

```sh
man -f man
```

可以得到如下输出：

```
man (7)              - macros to format man pages
man (1)              - an interface to the on-line reference manuals
```

括号里面是代号的意思，具体含义如下：

| 代号 | 代表内容 |
| - | - |
| 1 | 使用者在shell环境中可以操作的指令或可可执行文件 |
| 2 | 系统核心可调用的函数与工具等 |
| 3 | 一些常用的函数（function）与函数库（library），大部分为C的函数库（libc） |
| 4 | 设备文件的说明，通常在/dev下的文件 |
| 5 | 配置文件或者是某些文件的格式 |
| 6 | 游戏（games） |
| 7 | 惯例与协定等，例如Linux文件系统、网络协定、ASCII code等等的说明 |
| 8 | 系统管理员可用的管理指令 |
| 9 | 跟kernel有关的文件 |

知道有代号 1 和 7 后，可以通过如下命令进入查看：

```sh
man 1 man
man 7 man
```

这个用法等价于 [whatis](whatis.md) 命令

## 关键词检索

```
man -k unmount
```

输出如下：

```
fusermount (1)       - unmount FUSE filesystems
umount (2)           - unmount filesystem
umount (8)           - unmount file systems
umount.nfs (8)       - unmount a Network File System
umount2 (2)          - unmount filesystem
```

这个用法等价于 [apropos](apropos.md) 命令