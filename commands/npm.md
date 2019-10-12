npm 是 NodeJS 语言的包管理工具。

# 安装

```sh
sudo apt install npm
```

安装完成后查看版本：

```
$ npm -v
3.5.2
```

# 例子

```sh
# 安装依赖包
npm install <package>
npm install --global <package>
# 查看已安装
npm ls
# 初始化 package.json 文件
npm init
```

# 配置

## 查看配置

```
$ npm config list
; cli configs
user-agent = "npm/3.5.2 node/v8.10.0 linux x64"

; builtin config undefined
globalconfig = "/etc/npmrc"
globalignorefile = "/etc/npmignore"
prefix = "/usr/local"

; node bin location = /usr/bin/node
; cwd = /home/cheng470
; HOME = /home/cheng470
; "npm config ls -l" to show all defaults.
```

## 配置 registry 地址

```sh
# 查看默认镜像
cheng470@CN-00121983:~$ npm config get registry
https://registry.npmjs.org/
# 配置国内镜像
cheng470@CN-00121983:~$ npm config set registry https://mirrors.huaweicloud.com/repository/npm/
cheng470@CN-00121983:~$ npm config get registry
https://mirrors.huaweicloud.com/repository/npm/
```

## 配置本地全局模块安装位置

安装位置由 prefix 属性决定的。通过如下命令查看安装位置：

```
npm config ls -l | grep prefix
```

有多种方式修改。

1 通过 npm config

```
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.profile
source ~/.profile
npm install -g jshint
```

2 通过 NPM_CONFIG_PREFIX

```
NPM_CONFIG_PREFIX=~/.npm-global
```

3 通过 nvm 安装 node

通过 nvm 会自动配置好 prefix 属性，这也是官方推荐的方式。如下：

```
$ nvm install node
$ npm config ls -l | grep prefix
prefix = "/home/cheng470/.nvm/versions/node/v12.11.0"
save-prefix = "^"
tag-version-prefix = "v"
```

# 参考

[华为开源镜像站_软件开发服务_华为云](https://mirrors.huaweicloud.com/)
[Resolving EACCES permissions errors when installing packages globally | npm Documentation](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally)