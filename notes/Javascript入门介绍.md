##ECMAScript：
1. javascript主要分为三个部分：
 
    > ①javascript核心（ECMAScript）  
    > ②DOM文档对象模型  
    > ③BOM浏览器对象模型    

2. ECMAScript与web浏览器没有任何依赖，这门语言并不包含输入输出，ECMAScript-262定义的只是语言基础。web浏览器只是ECMAScript实现可能的宿主环境之一！
3. 宿主环境提供基本的ECMAScript实现，同时也会提供该语言的扩展，这些扩展如DOM利用ECMAScript的核心类型和语法提供更多的功能。
4. ECMAScript-262标准没有参照Web浏览器，它规定了这门语言的语法、类型、语句、关键字、保留字、操作符、对象。
5. Javascript实现了ECMAScript，同样ActionScript、OpenView ScriptEase也实现了ECMAScript。

##DOM：
1. DOM是针对XML但经过扩展用于HTML的应用程序编程接口（API Application Program Interface）。
2. DOM1级（1998年10月）正式成为W3C的推荐标准，DOM1级有两个模块：
 
    >①DOM核心（DOM Core）  
    >②DOM HTML。
3. DOM Core规定的是如何映射基于XML的文档结构，以便简化对文档中任一部分的访问和操作。
4. DOM HTML是在DOM Core的基础上加以扩展，添加了针对HTML的对象和方法。
5. DOM2级在原来DOM的基础上又扩充了（DHTML一直都支持的）鼠标和用户界面事件、范围、便利（迭代DOM文档的方法）等模块。，而且还通过对象接口增加了对CSS的支持。
6. DOM2级同时也对DOM1级的核心进行扩展并开始支持XML命名空间。
7. DOM2级别增加的新类型和新接口的定义：      
 
    >①DOM视图（跟踪不同文档视图的接口）  
    >②DOM事件（事件和事件处理接口）    
    >③DOM样式（基于Css为元素应用样式的接口）   
    >④DOM遍历和范围（遍历和操作文档树的接口）  
8. DOM3级进一步扩展DOM。引入了：
 
    >①以统一方式加载和保存文档的方法（在DOM加载和保存模块中定义）  
    >②新增验证文档的方法（在DOM验证模块中定义）
9. DOM3级也对DOM核心进行了扩展，开始支持XML1.0规范，涉及XML Infoset，XPath，XML Base。
10. DOM0（其实不存在）指的是IE4.0，Netscape Navigator4.0最初支持的DHTML而已。
11. Web浏览器对DOM的支持：IE在IE的时候才完全实现DOM1，而FF，Chrome，Safari，Opera已经远超IE了！

##BOM：
1. 根本上来讲BOM只处理浏览器窗口和框架，但是人们习惯把针对浏览器的js扩展算作BOM的一部分。
2. BOM主要包括以下内容：
 
    >①弹出新浏览器窗口的功能  
    >②移动、缩放管理浏览器窗口的功能   
    >③提供浏览器对象信息的navigator对象  
    >④提供浏览器所加载页面的详细信息的location对象  
    >⑤提供用户显示器分辨率的screen对象  
    >⑥对cookies的支持  
    >⑦像XMLHttpRequest和IE的ActiveXObject对象。  

  
##Script元素
1、在HTML页面中插入Javascript的主要方法，就是使用`<script>`元素，这个元素被加入到正式的HTML规范中。
2、`<script>`元素定义了5个属性：
①charset（指定代码的字符集，大部分浏览器会忽略此属性，不常用）
②defer（表示脚本可以延迟到文档完全被解析和现实之后在加载）
③language（已被废弃）
④src（可选，表示外部文件，也可来源于外部域）
⑤type（必选，可以看成是language的替代属性，虽然`text/javascript`和`text/ecmascript`已经不被推荐，但是一直以来还是使用`text/javascript`，实际上服务器在传送javascript文件时使用的MIME类型为`application/x-javascript`,另外非IE浏览器中可以使用`application/javascript`或者`application/ecmascript`，考虑到最大限度的浏览器兼容性还是建议使用`text/javascript`）
3、在使用`<script>`嵌入到代码中时，记住不要在代码中任何地方出现`</script>`，注意分割！
4、外部js，只需要包好`<script></script>`之间的代码，也就是说外部js不需要再包含`<script></script>`。
5、如果在XHTML中`<script>`元素也可以写成`<script type='text/javscript' src='example.js' />`注意此处没有`</script>`，而在HTML中则不行，特别是IE会报错。
6、外部js文件的扩展名.js不是必须的，浏览器不会检测其扩展名，这样就使得服务器返回动态生成js文件成为可能。
7、带有src属性的`<script>`元素不应该在其`<script></script>`中再出现代码。
8、建议把`<script>`元素放在body元素的后面。防止出现由于加载js文件文档出现空白。
9、在XHTML中使用`<script>`需要利用CData片段

    <script> 
    <![CData[ 
        //这个区域内写js代码
    //]]>
    </script>

当有浏览器不兼容XHTML时，因而不支持XHTML，再使用//注释掉CData即可。

    <script type='text/javascript'>
    //<![CData[
        //这里写js代码！
    //]]
    </script>

10、不支持javascript的浏览器会把`<script>`元素直接输出到页面，解决方法

    <script type='text/javascript'>
    <!--
        //这里写js代码！
    --></script>
    PS：其实这个已经没有必要了，因为大部分浏览器都开始支持js了。

11、`<noscript>`元素，在浏览器不支持脚本或者脚本被禁用时，`<noscript>`有用。

    <noscript>
    <p>本页面需要浏览器支持（启用）JavaScript</p>
    </noscript>

*liujb引用请注明出处*