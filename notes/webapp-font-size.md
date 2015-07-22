###font-size

-------

px，percent，em，rem之间的简单对比

1. px比较精确，方便调试
2. 百分比不容易计算
3. em只是相对于父元素指定的font-size
4. rem相对于root
	
		html{
	        font-size: 62.5%;
	    }
	    p{
	    	font-size: 1.2rem; //12px
	    }
	    span{
	    	font-size: 12px; //是一样的
	    }



1. IE6-8，以及所有的Modern Browers默认的字体都是**16px**－－幸运啊
2. 之前我们都是指定body为14px，而后都是使用em单位，这里面可能有些不大对
3. 以后都设定html为62.5%（也就是10px）然后使用rem单位，比如ue图上面的20点就是10px，也就是1rem。

###font-family

____

1. `font-family: Heiti SC','Microsoft YaHei', arial, sans-serif, 'Droid Sans Fallback';` -- 
2. `Heiti SC` -- OSX & iOS上默认字体
3. `STHeiTi-Light`

###font-adjust

----

1. `-webkit-text-size-adjust: none;` -- 可以调整字体大小小于12px
2. `font-size-adjust`