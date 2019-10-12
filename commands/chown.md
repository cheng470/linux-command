chown 既可以修改文件拥有者，也可以修改用户所属群组。

# 例子

```sh
# 修改文件拥有者
chown bin var.sh
# 同时修改文件拥有者和所属群组
chown root:root var.sh
# 修改文件所属群组
chown :adm var.sh

# 也可以用点号代替冒号，但有点不好理解
chown root.root var.sh
chown .adm var.sh
```