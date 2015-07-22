#### 简介 ####

Angular.js是一个MV*（Model-View-Whatever，不管是MVC或MVVM，统归为MDV-Model Drive View）Javascript框架，其是Google推出的SPA（Single-Page-Application）应用框架，为我们的Web开发增加了不少魔法变换。

#### 快速开始 ####

- 查看如下代码，在浏览器中会出现Hello World!  

	 
	    <!doctype html>
	    <html ng-app>
	        <head>
	            <script src="http://code.angularjs.org/angular-1.0.1.min.js"></script>
	       </head>
	        <body>
	            Hello {{'World'}}!
	        </body>
	    </html>


- 如下代码将绑定输入框

	
	    <!doctype html>
	    <html ng-app>
	        <head>
	            <script src="http://code.angularjs.org/angular-1.0.1.min.js"></script>
	        </head>
	        <body>
	            Your name: <input type="text" ng-model="yourname" placeholder="World">
	            <hr>
	            Hello {{yourname || 'World'}}!
	        </body>
	    </html>


####AngularJS应用的解析

- 模板（Templates）
模板是您用HTML和CSS编写的文件，展现应用的视图。 您可给HTML添加新的元素、属性标记，作为AngularJS编译器的指令。 AngularJS编译器是完全可扩展的，这意味着通过AngularJS您可以在HTML中构建您自己的HTML标记！
- 应用程序逻辑和行为（Logic and Behavior）
应用程序逻辑和行为是您用JavaScript定义的控制器。AngularJS与标准AJAX应用程序不同，您不需要另外编写侦听器或DOM控制器，因为它们已经内置到AngularJS中了。这些功能使您的应用程序逻辑很容易编写、测试、维护和理解。
- 模型数据（Data）
模型是从AngularJS作用域对象的属性引申的。模型中的数据可能是Javascript对象、数组或基本类型，这都不重要，重要的是，他们都属于AngularJS作用域对象。
AngularJS通过作用域来保持数据模型与视图界面UI的双向同步。一旦模型状态发生改变，AngularJS会立即刷新反映在视图界面中，反之亦然。

####AngularJS非常有用的服务特性

- 底层服务包括依赖注入，XHR、缓存、URL路由和浏览器抽象服务。
- 您还可以扩展和添加自己特定的应用服务。
- 这些服务可以让您非常方便的编写WEB应用。

[参考地址](http://www.angularjs.cn/A002)
