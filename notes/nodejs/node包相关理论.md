
###node包相关理论

####包内严格来讲需要有以下文件和文件夹

- package.json（有比较严格的规范）
- bin
- lib
- doc
- test

**node中对包没有那么严格，只需要有package.json文件就行了**

1、nodejs中模块和包没有本质区别，两个概念可以理解成一个意思  
2、模块和文件一一对应，一个文件就是一个模块，这个文件可以是js代码，json或者C/C++的扩展   
3、两个对象 exports和require，用来公开接口和从外部获取模块的接口，即所获的exports对象   
4、有时候想把一个对象封装到模块中，使用module.export = myObj;来取代exports.myObj = myObj;   
5、把文件夹封装成一个模块，就是包！   
6、npm：nodejs中包统一管理器`npm install [-g] express`  
7、本地模式和全局模式安装包（带-g参数表示全局安装）   

- 如果要把包当作工程的一部分，通过本地获取
- 如果要在命令行下使用，则使用全局安装（不能通过require来获取）
- 可以通过npm link命令打破全局安装的包不能通过require来获取的限制。
- npm可以用来发布自己的包