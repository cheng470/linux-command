# 语法

```
sed [OPTION]... {script-only-if-no-other-script} [input-file]...
```

# 参数

```
-e script, --expression=script 执行后面跟着的脚本
-f script-file, --file=script-file 执行后面跟着的脚本文件
-i[SUFFIX], --in-place[=SUFFIX] 直接修改原文件，如果带有 SUFFIX，则以该字符做后缀备份原文件
-n, --quiet, --silent 禁止自动打印原内容
-r --regexp-extended 使用增强的正则表达式
```

# 脚本动作

| 动作 | 说明 |
| - | - |
| a \ text | Appeend 往后一行添加字符串 |
| c \ text | Replace 替换 |
| d | Delete 删除 |
| i \ text | Insert 往前一行插入字符串 |
| n | Next 读取下一行到模式空间 | 
| p | Print 打印 |
| q | Quit 退出 |
| r | Read 读取文件 |
| s/regexp/replacement/ | Replace 替换 |
| w | Write 写入文件 |

# 例子

```sh
# 第4行后面添加 new line
nl /etc/passwd | sed '4anew line'
nl /etc/passwd | sed '4a new line'
nl /etc/passwd | sed '4a\new line'

# 第4行后面添加两行 new line
nl /etc/passwd | sed '4anew line\
> new line'
nl /etc/passwd | sed '4anew line\nnew line'

# 第4行前面添加 new line
nl /etc/passwd | sed '4inew line'

# 删除第2行
nl /etc/passwd | sed '2d'

# 删除第3行到最后一行
nl /etc/passwd | sed '3,$d'

# 删除匹配行
nl /etc/passwd | sed '/root/d'

# 删除空白行
nl /etc/passwd | sed '/^$/d'

# 将2-5行的内容替换成 replace line
nl /etc/passwd | sed '2,5creplace line'

# 打印5-7行
nl /etc/passwd | sed -n '5,7p'

# 搜索包含 root 字串的行，然后打印
nl /etc/passwd | sed -n '/root/p'

# 搜索从包含 daemon 的行到包含 mail 的行，然后打印
nl /etc/passwd | sed -n '/daemon/,/mail/p'

# 搜索包含 root 字串的行，然后执行动作,最后的 q 动作是退出
nl /etc/passwd | sed -n '/root/{s/bash/zsh/;p;q}'

# 搜索替换
nl /etc/passwd | sed 's/bash/zsh/g'

# 搜索替换第1-5行
nl /etc/passwd | sed '1,5 s/bash/zsh/g'

# 多条命令，先搜索替换，然后打印1-5行，多种写法
nl /etc/passwd | sed 's/bash/zsh/g' | sed -n -e '1,5p'
nl /etc/passwd | sed -n 's/bash/zsh/g; 1,5p'
nl /etc/passwd | sed -n -e 's/bash/zsh/g' -e '1,5p'

# 在第一行后面添加文件内容
nl /etc/passwd | sed -n -e '1r /root/line.txt' -e '1,3p'

# 将匹配的内容写入 /root/a.txt
nl /etc/passwd | sed -n '/root/ w /root/a.txt'

# 将匹配 root 的下一行进行替换
nl /etc/passwd | sed '/root/{n; s/sbin/test/}'

# 打印奇数行
nl /etc/passwd | sed -n 'p;n'

# 打印偶数行
nl /etc/passwd | sed -n 'n;p'
```

修改文件内容的例子：

```
[root@node1 ~]# cat testfile
HELLO LINUX!
Linux is a free unix-type opterating system.
This is a linux testfile!
Linux test
[root@node1 ~]# sed -i '2anew line' testfile
[root@node1 ~]# cat testfile
HELLO LINUX!
Linux is a free unix-type opterating system.
new line
This is a linux testfile!
Linux test
```

## 查网卡 eth-0 的 ip

```
[root@node1 ~]# ip a | grep inet | grep eth0
    inet 192.168.31.254/24 brd 192.168.31.255 scope global d
[root@node1 ~]# ip a | grep inet | grep eth0 | sed 's/^.*inet //g' | sed 's/\/24.*$//g'
192.168.31.254
```