
###webapp设计原则

		3S原则是指：Simple、Small、Speedy。这是国外一位大牛总结的，可以参见《Mobile Web Design: Best Practices》。对这三点，我深表认同。想说的是Speedy严格意义上应该算是结果，而不能归为原则。Web设计方面，我一直崇尚简约风格：便捷的操作、清爽的界面、友好的提示、少而小的图片、精简的代码等，当做到了这些，相信网站会变得Speedy。
		
###meta标签

1. `<meta content=”width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0;” name=”viewport” />`强制让文档的宽度与设备的宽度保持1:1，并且文档最大的宽度比例是1.0，且不允许用户点击屏幕放大浏览（注意：据说HTC G7自身系统浏览器不支持这一条规则，能对页面进行放大，一旦放大导致页面布局错乱，解决方法：定义页面的最小宽度 min-width，body{min-width: 300px;}）
2. `<meta content=”yes” name=”apple-mobile-web-app-capable” />` iOS设备(不只iphone)中的safari私有meta标签，它表示：允许全屏模式浏览，开启对Web Aapp程序的支持。
3. `<meta content=”black” name=”apple-mobile-web-app-status-bar-style” />`ios系统的私有标签，它指定在web app状态下，ios设备中顶端的状态条的颜色； 默认值为default（白色），可以定为black（黑色）和black-translucent（灰色半透明）。若值为“black-translucent”将会占据页面px位置，浮在页面上方（会覆盖页面20px高度–iphone4和itouch4的Retina屏幕为40px）
4. `<meta content=”telephone=no” name=”format-detection” />`使设备浏览网页时对数字不启用电话功能（不同设备解释不同，itouch点击数字为存入联系人，iphone为拨打电话），忽略将页面中的数字识别为电话号码。若需要启用电话功能将telephone=yes即可，具体调用格式可以这样书写代码`<a href="13800138000">Call Me</a>`，若在页面上面有google maps, iTunes和youtube的链接会在ios设备上打开相应的程序组件。
5. ` <meta content=”email=no” name=”format-detection” />`iOS中不会自动识别邮箱地址，android中会自动识别邮箱地址，所以这句话是禁止设备自动识别邮箱地址
6. `<meta name="apple-mobile-web-app-title" content="XXX网站欢迎你">`iOS6可以通过meta标签来给主屏webapp指定标题：
7. `-webkit-tap-highlight-color: rgba(0,0,0,0);`webapp中input文本框输入高亮


----

###其他

1. `-webkit-border-image`来定义复杂样式的按钮。
2. 块级化a标签，尽可能保证用户的可点击区域较大
3. 自适应布局模式
4. 学会使用`webkit－box`可以帮助前端工程师做到盒子模型的灵活控制。
5. iOS和android中去除输入url的控件条`setTimeout(scrollTo,0,0,0);`这句代码必须放在window.onload里才能够正常的工作，而且你的当前文档的内容高度必须是高于窗口的高度时，这句代码才能有效的执行。
6. 如何检测用户是通过主屏启动你的webapp
	 
		看过Apple webapp API的同学都知道iOS为safari提供了一个将当前页面添加主屏的功能，按下 iphoneipodipod touch底部工具中的小加号，或者ipad顶部左侧的小加号，就可以将当前的页面添加到设备的主屏，在设备的主屏会自动 增加一个当前页面的启动图标，点击该启动图标就可以快速、便捷的启动你的webapp。从主屏启动的webapp和浏览器访问你的webapp最大的区别 是它清除了浏览器上方和下方的工具条，这样你的webapp就更加像是nativeapp了，还有一个区别是window对像中的navigator子对 象的一个standalone属性。iOS中浏览器直接访问站点时，navigator.standalone为false,从主屏启动webapp 时，navigator.standalone为true， 我们可以通过navigator.standalone这个属性获知用户当前是否是从主屏访 问我们的webapp的。在Android中从来没有添加到主屏这回事！
	
7. 如何关闭iOS中键盘自动大写
 
		我们知道在iOS中，当虚拟键盘弹出时，默认情况下键盘是开启首字母大写的功能的，根据某些业务场景，可能我们需要关闭这个功能，移动版本webkit为 input元素提供了autocapitalize属性，通过指定autocapitalize=”off”来关闭键盘默认首字母大写。

8. iOS中如何彻底禁止用户在新窗口打开页面

		有时我们可能需要禁止用户在新窗口打开页面，我们可以使用a标签的target=”_self“来指定用户在新窗口打开，或者target属性保持空，但 是你会发现iOS的用户在这个链接的上方长按3秒钟后，iOS会弹出一个列表按钮，用户通过这些按钮仍然可以在新窗口打开页面，这样的话，开发者指定的 target属性就失效了，但是可以通过指定当前元素的-webkit-touch-callout样式属性为none来禁止iOS弹出这些按钮。这个技 巧仅适用iOS对于Android平台则无效。
		
9. iOS中如何禁止用户保存图片\复制图片

		我们在第13条技巧中提到元素的-webkit-touch-callout属性，同样为一个img标签指定-webkit-touch-callout为none也会禁止设备弹出列表按钮，这样用户就无法保存＼复制你的图片了。
 
10. iOS中如何禁止用户选中文字
 
		我们通过指定文字标签的-webkit-user-select属性为none便可以禁止iOS用户选中文字。

11. iOS中如何获取滚动条的值

		桌面浏览器中想要获取滚动条的值是通过document.scrollTop和document.scrollLeft得到的，但在iOS中你会发现这两 个属性是未定义的，为什么呢？因为在iOS中没有滚动条的概念，在Android中通过这两个属性可以正常获取到滚动条的值，那么在iOS中我们该如何获 取滚动条的值呢？通过window.scrollY和window.scrollX我们可以得到当前窗口的y轴和x轴滚动条的值。
		
12. 如何解决盒子边框溢出

		当你指定了一个块级元素时，并且为其定义了边框，设置了其宽度为100％。在移动设备开发过程中我们通常会对文本框定义为宽度100％，将其定义为块级元 素以实现全屏自适应的样式，但此时你会发现，该元素的边框(左右)各1个像素会溢了文档，导致出现横向滚动条，为解决这一问题，我们可以为其添加一个特殊 的样式-webkit-box-sizing:border-box;用来指定该盒子的大小包括边框的宽度
			
13. 如何解决Android 2.0以下平台中圆角的问题
		 
		如果大家够细心的话，在做wap站点开发时，大家应该会发现android 2.0以下的平台中问题特别的多，比如说边框圆角这个问题吧。
		在对一个元素定义圆角时，为完全兼容android 2.0以下的平台，我们必须要按照以下技巧来定义边框圆角：
		1. -webkit这个前缀必须要加上（在iOS中，你可以不加，但android中一定要加）；
		2. 如果对针对边框做样式定义，比如border:1px solid #000;那么-webkit-border-radius这属性必须要出现在border属性后。
		3. 假如我们有这样的视觉元素，左上角和右上角是圆角时，我们必须要先定义全局的(4个角的圆角值)-webkit-border- radius:5px;然后再依次的覆盖左下角和右下角，-webkit-border-bottom-left-radius:0;-webkit- border-bottom-right-border:0;否则在android 2.0以下的平台中将全部显示直角，还有记住！-webkit这个前 缀一定要加上！
		
14. 同步调试 
 
		iOS 6中Safari和webview，支持用桌面Safari同步调试了。像在pc端上一样调试webapp或者hybrid app对前端开发者无疑是极大的方便。方法很简单：
		
		第一步，手机上设置Safari开启 web inspector（设置–>safari–>高级）
		第二步，手机连上电脑
		第三部，打开电脑上的Safari，然后菜单–》开发，即可看到设备。点击即可调试。

15. click事件的样式变化

		虽然没有鼠标，但仍然会有鼠标事件，其中的onclick事件发生时，safari会自动改变一下元素的样式，以示被点击。这个样式可以用-webkit-tap-highlight-color属性来定义。
		
		
16. touch事件改变样式
 
		 :active这个高端洋气的CSS伪类状态在WEB页面开发中已经很常用了。但可惜的是，iOS和Android都没有在手机端实现这个状态。不过我们总是有曲线救国的办法的不是么，找到替代的解决方案并不难，只要在JavaScript中增加下述事件就可以监听到:active状态啦。document.addEventListener("touchstart",function(){}, true) 而后，您可能会想用CSS来添加个按钮被按下的效果，且把该死的触摸高亮给去掉。`-webkit-tap-highlight-color:rgba(0,0,0,0);
		 



###参考

[移动web前端开发](http://www.w3cfuns.com/thread-5596330-1-1.html)
