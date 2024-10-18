# node
## 常用开源
- 文件服务器
- https://github.com/cvabm/node-file-server 
- https://github.com/sigoden/dufs ，支持上传下载，执行exe即可
- http://iscute.cn/chfs 跟上边那个差不多
- https://github.com/drakkan/sftpgo exe可执行程序,功能复杂,常驻后台
## 设置镜像源
```
npm config get registry
npm set registry https://registry.npmjs.org/
```
## 设置代理
```
// 查看代理
npm config get proxy
npm config get https-proxy

// 设置代理
npm config set proxy http://127.0.0.1:8080
npm config set https-proxy http://127.0.0.1:8080

// 删除代理
npm config delete proxy
npm config delete https-proxy

```


## 快速创建一个最简单的 node 服务

### 方式一
1、生成 package.json 文件

```bash
npm init -ynpm install express
```

2、创建并编写 js 文件，例如：server.js

```
var express = require("express"); //导入express框架
var bodyParser = require("body-parser"); //http请求参数解析
var app = express(); //生成实例

//定义接口
app.get("/api/getList", function (request, response) {
  response.send("listData");
});

app.listen(80, function () {
  console.log("Node服务已启动");
});
```

3、在控制台执行命令，启动服务

```scss
node server.js
```

4、浏览器或 PostMan 访问地址， [http://localhost:3000/api/getList](http://localhost:3000/api/getList)


### 方式二
- `npx http-server .`