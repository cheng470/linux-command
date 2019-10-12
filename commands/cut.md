cut 可以将文本按列切分

# 语法

```
cut OPTION... [FILE]...
```

# 参数

```
-c 选择第几列字符
-d 指定分隔符，默认是 TAB
-f 选择第几列字段
```

# 例子

```sh
# 指定冒号分隔符，选择第1列
cut -d: -f1 /etc/passwd
cut -d : -f 1 /etc/passwd

# 选择第1列和第3列
cut -d: -f1,3 /etc/passwd

# 选择第1列至第3列
cut -d: -f1-3 /etc/passwd

# 选择第1至第3个字符
cut -c1-3 /etc/passwd
cut -c-3 /etc/passwd

# 选择第3到最后字符
cut -c3- /etc/passwd
```