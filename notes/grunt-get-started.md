##Grunt快速入门

[原文地址](http://www.gruntjs.org/docs/getting-started.html)

__________

####1. 安装grunt-cli
		
	npm install -g grunt-cli
	
1. 这条命令将会把grunt命令植入到你的系统路径中，这样就允许你从任意目录来运行它(定位到任意目录运行grunt命令)。
2. 安装`grunt-cli`并不等于安装了grunt任务运行器！Grunt CLI的工作很简单：在Gruntfile所在目录调用运行已经安装好的相应版本的Grunt。这就意味着可以在同一台机器上同时安装多个版本的Grunt。
	
####2. CLI如何工作

1. 每次运行grunt时，它都会使用node的require()系统查找本地已安装好的grunt。正因为如此，你可以从你项目的任意子目录运行grunt。

2. 如果找到本地已经安装好的Grunt，CLI就会加载这个本地安装好的Grunt库，然后应用你项目中的Gruntfile中的配置(这个文件用于配置项目中使用的任务，Grunt也正是根据这个文件中的配置来处理相应的任务)，并执行你所指定的所有任务。

###3. 用一个现有的Grunt项目进行工作

1. 假设已经安装好Grunt CLI并且项目也已经使用一个package.json和一个Gruntfile文件配置好了，那么接下来用Grunt进行工作就非常容易了：

2. 进入到项目的根目录(在命令行面板定位到项目根目录。在windows系统下，也可以进入项目根目录的文件夹后，按Shift+鼠标右键，打开右键菜单，选择“在此处打开命令窗口(W)”)。

3. 运行npm install安装项目相关依赖(插件，Grunt内置任务等依赖)。

4. 使用grunt(命令)运行Grunt。

注意：就是这么简单。已经安装的Grunt任务可以通过运行grunt --help列出来，但是通常最好还是先查看一下项目的文档。

###4. 准备一个新的Grunt项目

一个典型的配置过程通常只涉及到两个文件：package.json和Gruntfile。

1. package.json：这个文件被用来存储已经作为npm模块发布的项目元数据(也就是依赖模块)。你将在这个文件中列出你的项目所依赖的Grunt(通常我们在这里配置Grunt版本)和Grunt插件(相应版本的插件)。

2. Gruntfile：通常这个文件被命名为Gruntfile.js或者Gruntfile.coffee，它用于配置或者定义Grunt任务和加载Grunt插件。

####4.1 创建package.json的方式

- 大多数的grunt-init模板都会自动创建一个项目特定的package.json文件。

- npm init命令会自动创建一个基本的package.json文件。

- 从下面的例子开始并根据规范来按需扩展。
	
		{
		    "name": "my-project-name", // 项目名称
		    "version": "0.1.0", // 项目版本
		    "devDependencies": { // 项目依赖
		        "grunt": "~0.4.1", // Grunt库
		        "grunt-contrib-jshint": "~0.6.0", //以下三个是Grunt内置任务
		        "grunt-contrib-nodeunit": "~0.2.0",
		        "grunt-contrib-uglify": "~0.2.2"
		    }
		}
		
####4.2 安装Grunt和grunt插件

1. 添加Grunt和Grunt插件到一个现有的package.json中最简单的方式就是使用`npm install <module> --save-dev`命令。这不仅会在本地安装<module>，它还会使用一个波浪形字符的版本范围自动将所安装的<module>添加到项目依赖中。

例如使用下面的命令将会安装最新版的Grunt到你的项目中，并自动将它添加到你的项目依赖中：

`npm install grunt --save-dev`

上述命令也可以用于Grunt插件和其他的node模块的安装。当完成操作后请确保更新后的package.json文件也要与你的项目一起提交。

####4.3 Gruntfile

	Gruntfile.js或者Gruntfile.coffee文件都是归属于你项目根目录中的一个有效的JavaScript或者CoffeeScript文件(和package.json文件一样都在根目录中)，并且它(Gruntfile)也应该与你的项目源文件一起提交。

一个Gruntfile由下面几部分组成：

- "wrapper"函数(包装函数)
- 项目和任务配置
- 加载的Grunt插件和任务
- 自定义任务
		
一个典型的Gruntfile示例

	/**
	* wrapper
	*/
	module.exports = function(grunt){
	
	    // 项目配置
	    grunt.initConfig({
	        pkg: grunt.file.readJSON('package.json'),
	        uglify: {
	            options: {
	                banner: '/*! <%= pkg.name %> <%= grunt.template.today("yyyy-mm-dd") %> */\n'
	            },
	            build: {
	                src: 'src/<%=pkg.name %>.js',
	                dest: 'build/<%= pkg.name %>.min.js'
	            }               
	        }
	    });
	
	    // 加载提供"uglify"任务的插件
	    grunt.loadNpmTasks('grunt-contrib-uglify');
	
	    // 默认任务
	    grunt.registerTask('default', ['uglify']);
	}


如果已有的package.json文件不包括Grunt模块，可以在直接安装Grunt模块的时候，加上--save-dev参数，该模块就会自动被加入package.json文件。

npm install grunt --save-dev
npm install grunt-contrib-jshint --save-dev
npm install grunt-contrib-concat --save-dev
npm install grunt-contrib-uglify --save-dev
npm install grunt-contrib-watch --save-dev



