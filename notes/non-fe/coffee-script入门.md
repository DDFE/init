[官方网站](http://coffeescript.org/)
####Overview

    CoffeeScript is a little language that compiles into JavaScript.
    CoffeeScript is an attempt to expose the good parts of JavaScript in a simple way.
 
####安装方法

`npm install -g coffee-script`

> 必须先安装npm包管理器，windows平台下nodejs自带npm，安装完成后可以使用`coffee`Start the CoffeeScript REPL
 
####编译.coffee文件为.js文件

- `coffee --compile --output lib/ src/`将src目录下所有的coffee文件编译成lib目录树下所有js文件

####在Sublimtext中设置coffee环境

1. `Install Package`输入CoffeeScript，这就是安装了高亮语法显示。
2. 打开`C:\Users\Jiangbei\AppData\Roaming\Sublime Text 2\Packages\CoffeeScript`下的`CoffeeScript.sublime-build`
3. 将以下代码拷贝到'CoffeeScript.sublime-build'文件内，注意coffee.cmd的路径

        {
            "cmd": ["C:\\Users\\Jiangbei\\AppData\\Roaming\\npm\\coffee.cmd","-c","$file"],
            "file_regex": "^(*?):([0-9]*):?([0-9]*)",
            "selector": "source.coffee"
        }

4. Ctrl+B就可以将.coffee文件编译成.js文件了。

####Function

`square = (x) -> x * x `