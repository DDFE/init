###Icon-Face(font-face)技术学习记录
####@font-face简介
1. @font-face是Css3的一个模块，主要作用是让我们可以使用自定义的字体，以往使用的字体必须要客户端存在，font-face让我们可以使用服务器端的字体。
2. 兼容问题－－don't worry！IE很早就支持了！！！

####@font-face语法

	 @font-face{
	 	font-family: YourDefinedName;
	 	src: url('/static/your-path/xx.otf') format("opentype");
	 	src: url(''),
	 		url(),
	 		url(),
	 		url(); //为了兼容不同的浏览器
	 	font-weight: [normal|border];
	 	font-style: [normal|italic]
	 }
	 
####字体文件格式介绍
1. otf
2. eot
3. woff
4. ttf
5. svg


	 
####使用@font-face的demo如下：

	<!doctype html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>@font-face属性demo</title>
		<style type="text/css">
			@font-face{
				font-family: WebFont;
				src: url('/static/webapp/font/Fontin_Sans_R_45b.otf') format("opentype");
				font-weight: 700;			
			}
			h1{
				font-family: WebFont;
				font-size: 60px;
				text-align: center;
				border: solid 1px #4488aa;
				margin: 20px;
				padding: 5px;
			}
			address{
				font-family: WebFont;
				font-size: 14px;
				font-style: normal;
				text-align: center;
				margin: 20px;
				padding: 5px;			
			}
		</style>
	</head>
	<body>
		<h1>Cascading style sheets</h1>
		<address>This page use font-face ssss</address>
	</body>
	</html>
	
效果：

![字体效果](../images/imgs-note/QQ20140423-1.png)


####什么是Icon-Face技术


####Icon Font的优缺点
- Icon Font 的优点

	- 轻薄：Market项目中原icon图片背景27K（如果做成半透明发光，阴影效果会达到100K），目前全部用6K的字体代替。
	- 丰满：并且添加hover，click等状态效果更灵活。
	- 百搭：在不同的分辨率屏幕上适配缩放不失真！
	- 安静：由于体积小，可实现通过base64编码能置于样式表内。从而没有了http请求。　　

- Icon Font 的缺点

	- 样式不如图片丰富。但是，我们有很多场景是用纯色icon，特别是在Windows 8这种Metro UI开始越来越多的时候。
	- 文字渐变在Android平台上无法显示，在充满未知的将来一切或许都会后得到解决。
	- 重构成本相应提高。熟练之后其实也充满乐趣。
	- 页面重构越来越背离“切图”这个不准确的描述。用轻量级代码还原UI，优化设计稿是页面重构最核心的任务。
	
####如何制作Icon Font
####Icon-Font与Data-URI
####Icon-Font与Css-Sprites
####Css-Sprite与Data-URI
####SVG字体图标

####有用的连接：

- [前端观察](http://www.qianduan.net/css3-icon-font-guide.html)
- [阿里巴巴iconfont库](http://www.iconfont.cn/)
- [免费生成图标字体](http://fontello.com/)
- [免费字体下载](http://www.exljbris.com/fontinsans.html)
- [网页设计图标字体的简单方法](http://yife.im/web-design-icon-fonts-simple-way/)
- [ICON字体的优缺点](http://cube.qq.com/?p=476)
- [FontCreator下载地址](http://www.high-logic.com/font-editor/fontcreator.html)
- [WebFont-Generator](http://www.fontsquirrel.com/tools/webfont-generator)
- [Fontawesome for bootstroop](http://fontawesome.io/)
	
