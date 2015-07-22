##CSS框架开发的大致结构组成
1. reset.css
格式化css的真正好处是能够快速启动工作，你可以在新的HTML文件里引入框架，不用再处理重置padding 和 margins，实现统一的排版、浏览器下的相同表现。

2. layout.css
网站的设计可能有很多种布局，但是大多数都是由几个具有复用性的布局组成，选择性的引入所需要的布局，可以很快地应用所期望的页面布局。

3. base.css
定义body、h1-h6、a:link-a:active、p等的字体大小和颜色。
基本样式的css引用，譬如将ul定义class为“ul-text”，用来展现相同的icon、行间距、链接色彩。

4. table.css
定义table、tr、td、th、thead、tfoot、tbody、caption等标签的表现。

5. form.css
定义fieldset、label、button、input 、select、textarea这几个标签的表现。

6. print.css
修饰打印输出的页面。

7. specific page css
frontpage.css、list.css、detail.css、register.css等等

##CSS框架的弊端
1. 页面外部引用样式过多。
譬如关于ul的margin定义,在格式化的css中会声明为0，而在基本样式的css中又可能会声明margin:5px 10px;所以在Yslow中会出现多次定义。

2. 组件复用性的考量。
譬如表单定义的css中定义了所有表单的修饰,而假定在注册这个页面中只是需要这个css的百分之三十。那是否应切割出去那不要的百分之七十?

3. 到底该不该支持em?
可见如要支持em，最大的目的是为了在浏览器中可以根据用户的分辨率大小自由缩放，对于拥有超大显示器的用户与小显示器的用户是非常有用的。

##流行的CSS框架
[Github上流行的CSS框架](http://www.oschina.net/news/39496/the-most-popular-css-libraries-that-are-on-github)

*liujb引用注明出处*