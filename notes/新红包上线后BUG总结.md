####新红包问题总结

新红包上线后报出了一系列的BUG，主要问题主要是以下几点

1，昵称中的特殊字符

case:在领取列表中昵称出现了类html标签的字符，在渲染页面时被浏览器渲染成了标签，而这类标签恰好有user-agent-stylesheet(浏览器默认样式).当时采取的临时解决方案是修改CSS，把user-agent-stylesheet给覆盖，但是正确的做法应该是昵称中无论有什么特殊字符都应该原样的显示在页面上。

 问题解析：虽然PHP把昵称相关的字符echo到页面上时是编码过的，但是浏览器接收到编码时会自动解码一次，比如PHP编码后的字符  &lt;span&gt;,在浏览器显示则为<span>，如果拿着<span>直接innerText到container中，那么在页面上原样显示。但是如领取列表必须使用innerHTML属性，这时浏览器会把<span>当成一个HTML标签。
 
 解决方案1. 这不是最佳方案，不过可以快速解决问题，就是在innerHTML之前用js再编码一次。方法如下:
 	
		function html2Escape(sHtml) {
        return sHtml.replace(/[<>&"]/g,function(c){return {'<':'&lt;','>':'&gt;','&':'&amp;','"':'&quot;'}[c];});
    	}
    	
 解决方法2. 使用模板引擎，这是最佳方案

 <br/>	
2，红包标题中的特殊字符

 case: 之前红包中出现了%，然后BUG表现为整个页面无法渲染。
 
 问题分析: 这个问题其实也是编码与解码的问题，出现这个问题其实是沟通上的问题，在开发初期PHP对echo到页面上的字符编码可能做出过调整，而在联调时报出的BUG，前端这边采用的是容错处理，而没有去深究然后造成的两次解码出现的问题，在测试时也没有验到类似的case，所以BUG没有命中。
 
 解决方案: 前后端在配合时前期就应该约定好一些规范，来避免类似的问题出现。这些问题都不大，但是调试时会浪费较多的时间。这也是@桂勇哲在新红包初期总结时强调的文档的重要性
 


 <br/>
  3,  红包主题中的引号题
 
 case : 新红包上线后偶尔报出的可以正常的领取红包，但是金额没有显示
 
 问题分析：这个问题主要原因也是出现在昵称上，因为昵称中出现了引号，而把PHP echo到页面的JSON字符串给截断了，导致JS无法正确的解析该JSON字符串。
 
 解决方案：PHP输出JSON串到页面时在HTML中对字符进行编码一次，示例如下
 
		<input type="hidden" id='hid-all-hb-info' value='<?php echo htmlspecialchars($all_hb_info, ENT_QUOTES);  ?>'>
		
 <br/>

4, 领取列表中昵称过长而引起的样式错乱

 case:之前专车红包中报出红包领取列表中因为用户昵称过长而导致的页面样式出现问题，目前打车这边还未报出但是肯定会有同样的问题，因为用户圈是一样的都是在微信朋友圈中，后期支付后红包已经移植到手Q平台了，这类问题肯定少不了。
 
 问题分析：出现这类问题的原因是对于临界值的预估不足而未对该类问题做容错处理。
 
 解决方案：用户的昵称这种情况是无法受我们控制的，我们无法预估用户会输入字符长度与字符的内容，针对这类字符我们都需要考虑到临界值的处理，比如用户输入空字符我们默认显示为“好友”，而超过一定长度时页面需要考虑对字符串做截断处理或者必须完全显示时需要做换行处理等。
 
 对于临界值的处理与对异常的容错也是代码健壮性表现之一。
 
 对于字符串截取处理的JS代码如下，对于字符长度的截取中文肯定需要考虑到英文字符占1个字符而中文占两个字符的问题。
 	
4.1, 获取字符串的长度，一个英文占1个字节，一个中文占两个字节
 		
	    function getStringLength(str) {	    
     	   var realLength = 0, len = str.length, charCode = -1;
    	    for (var i = 0; i < len; i++) {
            charCode = str.charCodeAt(i);
         	   if (charCode >= 0 && charCode <= 128) realLength += 1;
         	   else realLength += 2;
      	     }
        return realLength;
    	};
    	
 4.2, 获取字符串的长度，超过长度默认为截取的长度+...（也可以用别的字符替代）
    	
		//substring 
		function subString(str,len,replaceString) { 
			replaceString=replaceString||"...";
        	var newLength = 0; 
        	var newStr = ""; 
        	var chineseRegex = /[^\x00-\xff]/g; 
        	var singleChar = ""; 
        	var strLength = str.replace(chineseRegex,"**").length; 
        	for(var i = 0;i < strLength;i++) { 
                singleChar = str.charAt(i).toString(); 
                if(singleChar.match(chineseRegex) != null) { 
                        newLength += 2; 
                }else { 
                        newLength++; 
                } 
                if(newLength > len) { 
                        break; 
                } 
                newStr += singleChar; 
        	} 
   	    	if(strLength > len) { 
                	newLength+=replaceString; 
       		} 
       		return newStr; 
    	} 
    	

 <br/>
 5, 未知的重复请求来源，造成服务器压力X2！！！！
   
 case:在看请求日志时会有未知的重复的请求，而且比较长时间未长到重复请求的来源，最后发现是因为背景图片为空导致的。
 
 问题分析：在做屏幕适配时是用JS来获取红包皮肤中的背景图片的路径，然后动态加上图片路径，之前的写法如下：
 
		document.getElementById("main").style.backgroundImage="url("+theme.backgroundurl+")";
		
 这种写法如果图片的url为""时，浏览器会拿到当前想要赋值背景图片HTML元素的baseURI,发一次请求，而这个baseURI一般就是当前的域名。
 
 解决方案：在给HTML元素动态加背景时需要对图片的URL做验证，示例如下：
 
		var bgUrl=theme.backgroundUrl;
		if(bgUrl){
			document.getElementById("main").style.backgroundImage="url("+bgUrl+")";
		}
		
只有保证背景图片路径不为空时才赋值给页面HTML元素。这种重复的请求会造成服务器压力成倍数增长，若页面中出现了多处类似情况，说不定服务器就被干趴下了，所以这种情况需要特别注意！！！

