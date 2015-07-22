[本文参考地址](https://github.com/nswbmw/N-chat/wiki/%E7%AC%AC%E4%B8%80%E7%AB%A0-socket.io-%E7%AE%80%E4%BB%8B%E5%8F%8A%E4%BD%BF%E7%94%A8#socketio-%E7%AE%80%E4%BB%8B)
 
####Socket.io 简介####
  
1.socket.io 是一个为实时应用提供跨平台实时通信的库。socket.io 旨在使实时应用在每个浏览器和移动设备上成为可能，模糊不同的传输机制之间的差异。  
2.socket.io 的名字源于它使用了浏览器支持并采用的 HTML5 WebSocket 标准，因为并不是所有的浏览器都支持 WebSocket ，所以该库支持一系列降级功能：  

- Adobe® Flash® Socket  
- AJAX long polling
- AJAX multipart streaming
- Forever Iframe
- JSONP Polling  

在大部分情境下，你都能通过这些功能选择与浏览器保持类似长连接的功能。 

####1.安装####

`npm install socket.io`
若使用Express，则需要再package.json中添加`"socket.io":"*"`并`npm install`即可  

####2.Client(index.html)####

    <script src="/socket.io/socket.io.js"></script>
    <script>
      var socket = io.connect('http://localhost');
      socket.on('news', function (data) {
        console.log(data);
        socket.emit('my other event', { my: 'data' });
      });
    </script>  
`var socket = io.connect('http://localhost')`表示与本地服务器建立连接。如果socket.io客户端跟服务端在同一台服务器上面也可以使用`var socket = io.connect()`直接建立本地和服务器连接。

####2.Server(app.js)####

    var app = require('express')()
      , server = require('http').createServer(app)
      , io = require('socket.io').listen(server);
 
    server.listen(80);
 
    app.get('/', function (req, res) {
      res.sendfile(__dirname + '/index.html');
    });
 
    io.sockets.on('connection', function (socket) {
      socket.emit('news', { hello: 'world' });
      socket.on('my other event', function (data) {
        console.log(data);
      });
    });

其中`io = require('socket.io').listen(server);`将socket.io绑定到服务器上，于是任何连接到该服务器的客户端都具备了实时通信功能。  

####3.Socket.io核心函数####

+ emit：
    用来发射一个事件或者触发一个事件，第一个参数为事件名，第二个参数为要发送的数据，第三个参数为回调函数（一般都省略，如需要对方接收到信息后立即确认，则需要用到回调函数）
+ on：
    用来监听一个emit发送的事件，第一个参数为要监听的事件名，第二个参数为一个匿名函数用来接收对方发送来的数据，该匿名函数的第一个参数为接收的数据，若有第二个参数则为要返回的函数。
+ 默认的事件

>connect：当与对方建立连接后自动触发connect事件。
>message：当收到对方发来的数据后触发message事件（通常为socket.send()）
>disconnect：当对方关闭连接后触发disconnect事件。

####4.注意点####

+ socket.emit()：向建立该连接的客户端广播。
+ socket.broadcast.emit()：向除去建立该连接的客户端的所有客户端广播。
+ io.sockets.emit()：向所有客户端广播，等同于上面两个之和。







