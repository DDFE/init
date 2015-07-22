###js关闭当前页面的几种方式

####不带任何提示直接关闭窗口

	<a href="javascript:window.opener=null;window.open('','_self');window.close();">关闭</a>

####自定义提示关闭

    <script language="javascript">
    function custom_close() {
        if (confirm("您确定要关闭本页吗？")) {
            window.opener = null;
            window.open('', '_self');
            window.close();
        } else {}
    }
    </script>
    // 这个脚本是 ie6和ie7 通用的脚本
    <input id="btnClose" type="button" value="关闭本页" onClick="custom_close()" />

####关闭当前页面:

	<a href="javascript:window.opener=null;window.close();">关闭</a>
	如果是按钮则:
	Response.Write("<script language=\"javascript\">window.opener=null;window.close();</script>");
这样点关闭的时候就不会弹出如当前窗口正试图关闭的对话框了。

#####怎么样当用户点浏览器关闭按钮时弹出对话框呢?

	<body onbeforeunload="return '真的要关闭此窗口吗?'">
	
*这样的话在点关闭时弹出确认对话框，点取消不关闭,点确定关闭窗口。*

####那么怎么当用户点击按钮的时候弹出对话框呢?

	Response.Write("<script language=\javascript\">" + "if(confirm(\"确定吗?\"))"+"{window.location.href='default.aspx';}"+"else{history.back();}"+"</script>");

*意思是：首先用confirm函数弹出个有确定取消的对话框,如果你点了确定就返回真,就执行window.location.href='default.aspx'代码,如果点了取消就返回假,就执行history.back();返回到原来的页面*