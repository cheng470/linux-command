grep 用于在文件中搜索文本

# 语法

grep [OPTION]... PATTERN [FILE]...

# 参数

```
-E, --extended-regexp 使用扩展正则表达式模式
-i, --ignore-case 忽略大小写
-o, --only-matching 只打印匹配的行
-c, --count 统计匹配的行数
-n, --line-number 显示行数
-v, --invert-match 匹配结果反转
-B, --before-context=NUM 打印前面 NUM 行
-A, --after-context=NUM 打印后面 NUM 行
-C, --context=NUM 打印相邻 NUM 行
-R, --dereference-recursive 递归搜索文件，可以搭配使用 --include 和 --exclude
```

# 例子

```sh
# 简单匹配用法
grep bash /etc/passwd
grep "bash" /etc/passwd
cat /etc/passwd | grep bash

# 扩展正则匹配
grep -E "[a-z]+[0-9]+" /etc/passwd
egrep "[a-z]+[0-9]+" /etc/passwd

# 只打印匹配的部分
grep -o bash /etc/passwd

# 统计匹配的行数
grep -E -c "[a-z]+" /etc/passwd

# 统计匹配的个数
grep -E -o "[a-z]+" /etc/passwd | wc -l

# 匹配结果反转
grep -E -v "[a-z]+" /etc/passwd

# 匹配某个结果和之后2行
seq 10 | grep 5 -A 2

# 匹配某个结果和之前2行
seq 10 | grep 5 -B 2

# 匹配某个结果和前后2行
seq 10 | grep 5 -C 2

# 显示行数
seq 10 | grep -n 5
```

## 在工程中搜索关键字，并打印具体的行数

```
$ grep "Hello" . -R -n
./src/main/java/com/mycompany/app/App.java:4: * Hello world!
./src/main/java/com/mycompany/app/App.java:11:        System.out.println( "Hello World!" );
```