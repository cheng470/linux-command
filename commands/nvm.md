Node Version Manager - POSIX-compliant bash script to manage multiple active node.js versions

# 安装

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
```

安装完成后，在当前用户的 `~/.bashrc` 下面加了如下环境变量：

```sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

需要 `source .bashrc` 或者重启终端生效。

生效后，通过 `command -v nvm` 检查：

```
$ command -v nvm
nvm
```

# 使用

```sh
# 安装最新版本node
nvm install node
nvm install iojs
# 安装最新lts版本node
nvm install --lts
# 指定安装版本，这里没有写 node
nvm install 6.14.4 # or 10.10.0, 8.9.1, etc
nvm install 5.0
nvm install 4.2
# 查询本地已经安装的版本
mvn ls
mvn ls 12
# 查询远程服务器可以安装的版本
nvm ls-remote
# 使用最新版本
nvm use node
nvm use --lts
# 使用指定版本
nvm use 6.14.4
# 使用指定版本运行 app.js
nvm run 6.10.3 app.js
# 设置 PATH 后运行命令，相当于 mvn use <version> && command
nvm exec 4.8.3 node app.js
nvm exec 4.2 node --version
# 显示指定版本的安装路径
nvm which 5.0
# 使用华为镜像安装
NVM_NODEJS_ORG_MIRROR=https://mirrors.huaweicloud.com/nodejs/ nvm install 8
```

安装结果：

```
cheng470@CN-00121983:~$ node -v
v12.11.0
cheng470@CN-00121983:~$ which node
/home/cheng470/.nvm/versions/node/v12.11.0/bin/node
cheng470@CN-00121983:~$ ll /home/cheng470/.nvm/versions/node/v12.11.0/bin/
total 44360
drwxr-xr-x 0 cheng470 cheng470      512 Sep 26 05:21 ./
drwxrwxrwx 0 cheng470 cheng470      512 Oct  1 11:07 ../
-rwxr-xr-x 1 cheng470 cheng470 45423432 Sep 26 05:21 node*
lrwxrwxrwx 1 cheng470 cheng470       38 Sep 26 05:21 npm -> ../lib/node_modules/npm/bin/npm-cli.js*
lrwxrwxrwx 1 cheng470 cheng470       38 Sep 26 05:21 npx -> ../lib/node_modules/npm/bin/npx-cli.js*
cheng470@CN-00121983:~$ npm -v
6.11.3
$ echo $PATH
/home/cheng470/.nvm/versions/node/v12.11.0/bin:/home/cheng470/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:
```


# 资源

[nvm-sh/nvm: Node Version Manager - POSIX-compliant bash script to manage multiple active node.js versions](https://github.com/nvm-sh/nvm)
