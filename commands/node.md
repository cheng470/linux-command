node 命令是 NodeJS 语言的执行命令。

Node.js is a JavaScript runtime built on Chrome's V8 JavaScript engine.

# 安装

```sh
sudo apt install node
```

安装完成后查看版本：

```
$ node -v
v8.10.0
```

# 运行

```
mkdir -p example/node
cd example/node
vim app.js
```

app.js 内容：

```js
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

执行：

```sh
$ node app.js
Server running at http://127.0.0.1:3000/
```

访问：

```sh
$ curl http://127.0.0.1:3000
Hello World
```

# 资源

[Docs | Node.js](https://nodejs.org/en/docs/)
[Installing Node.js via package manager | Node.js](https://nodejs.org/en/download/package-manager/)
[Getting Started Guide | Node.js](https://nodejs.org/en/docs/guides/getting-started-guide/)