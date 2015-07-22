####1、使用node内置的方法`node debug index.js`
其中主要的命令有：

1. run
2. restart
2. cont,c
2. next,n
2. step
2. out,o
2. setBreakpoint()
2. setBreakpoint('f()'),sb(...)
2. setBreakpoint("script.js",20)
2. clearBreakpoint()
2. backtrace,bt
2. list(5)
2. watch(expr)
2. unwatch(expr)
2. watchers
2. repl
2. kill
2. scripts
2. version


####2、远程调试（由于V8提供的调试功能是基于TCP协议的，因此nodejs可以轻松地实现远程调试）
    node --debug[=port] script.js（脚本会正常执行不会停止）
    node --debug-brk[=port] script.js
    
在一个终端中：

    allen@allen-pc:~/nodejs/2012$ node --debug-brk=2324 debug.js
    debugger listening on port 2324
    
在另一个终端中：

    allen@allen-pc:~$ node debug localhost:2324
    connecting... ok
    debug> 

####3、使用Eclipse调试nodejs


####4、使用node-inspector调试nodejs（只支持web-kit内核的浏览器，ff跟ie不支持）

[参考地址](http://www.js8000.com/%E5%BC%80%E5%8F%91node-js%E5%A5%BD%E7%94%A8%E7%9A%84debug%E5%B7%A5%E5%85%B7node-inspector/)

2. npm install -g node-inspector
2. 在终端输入node --debug-brk app.js或者node --debug app.js
2. 启动node-inspector：node-inspector [--web-port=]
2. 在浏览器中打开网页，即会显示出web调试工具http://localhost:8080/debug?port=5858
2. 在开一个页面打开app所监听的web服务器比如http://localhost:3000


####5、sublime text 2的nodejs调试插件

[参考地址](http://blog.csdn.net/kaosini/article/details/8603633)


####6、WebStorm调试nodejs

非常方便

[参考地址](http://www.cnblogs.com/enix/archive/2012/04/29/2475983.html)