# 在 CentOS 中部署一个迷你 node 服务器
1. 首先要确认服务器是否具有 Node.js 环境。
```
node --version
```
2. 没有的话选择任意一种方法部署 Node.js 环境；
这里我选择了二进制文件安装的方法。

先找到要安装的 [Node.js](https://nodejs.org/dist/latest/) 文件, 然后在服务器上下载上述找到的文件；
```
wget https://nodejs.org/dist/latest/node-v17.3.0-linux-x64.tar.xz
```
3.  解压文件；
```
tar -xvf node-v17.3.0-linux-x64.tar.xz
mv node-v17.3.0-linux-x64 node.js // 为了方便、简洁改一下文件名
```
4. 创建给node、npm、npx命令创建软链接；
```
ln -s /rot/node.js/bin/node /user/local/bin/node
ln -s /rot/node.js/bin/npm /user/local/bin/npm
ln -s /rot/node.js/bin/npx /user/local/bin/npx
```
5. 确任链接成功；
```
node --version
npm --version
npx --version
```
6. 创建迷你服务器；
```
cd ~
mkdir example
touch mini-server.js
vim mini-server.js
```
输入 i 进入编辑模式；
键入如下代码：
```
const http = require('http')
const hostname = '0.0.0.0'
const port = 80
const server = http.createServer((req, res) => {
    res.statusCode = 200
    res.setHeader('Content-Type', 'text/plain')
    res.end('Hello SAD!')
})

server.listen(port, hostname. () => {
    console.log(`Server running at http://${hostname}:{port}/`)
})
```
至此一个爆简易的迷你服务器就建成了，可以根据自己需要再增加功能。

7. 使用 nohup 挂起自建的 node 服务器；
```
nohup mini-server.js > mini-server.log 2>&1 &
```
8. 检查是否80端口被监听；
```
netstat -tpln
```

