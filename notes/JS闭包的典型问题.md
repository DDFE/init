**[参考地址](http://blog.csdn.net/nx8823520/article/details/6858126) 感谢那些给我们引导的先驱者们！**
####引入：为何每次点击都弹出5？？
    <html >
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />    
    <title>闭包演示</title>
    <script type="text/javascript"> 
        function init() {     
            var pAry = document.getElementsByTagName("p");     
            for( var i=0; i<pAry.length; i++ ) {     
                 pAry[i].onclick = function() {     
                 alert(i);     
            }
          }
        }
    </script></head>
    <body onload="init();">
        <p>产品一</p>
        <p>产品二</p>
        <p>产品三</p>
        <p>产品四</p>
        <p>产品五</p>
    </body>
    </html>
    //为什么会是5呢？
    //当 i == 4 的时候，刚好满足了条件，然后再进行了一次 i++，所以  i==5 了。
    //所以当点击的时候，弹出 5。

####方法1：将变量 i 保存给在每个段落对象（p）上

    function init() {
        var pAry = document.getElementsByTagName("p");
        for (var i = 0; i < pAry.length; i++) {
            pAry[i].i = i;
            pAry[i].onclick = function() {
                alert(this.i);
            }
        }
    }
    // 将 i 绑定到 pAry[i] 这个对象上

####方法2：将变量 i 保存到匿名函数本身

    function init2() {
        var pAry = document.getElementsByTagName("p");
        for (var i = 0; i < pAry.length; i++) {
            (pAry[i].onclick = function() {
                alert(arguments.callee.i);
            }).i = i;
        }
    }
    // 将 i 绑定到 (pAry[i].onclick = function() {} )这个对象上

####方法3：加一层闭包将 i 以函数参数的形式传递给内层函数

    function init3() {
        var pAry = document.getElementsByTagName("p");
        for (var i = 0; i < pAry.length; i++) {
            (function(arg) {
                pAry[i].onclick = function() {
                    alert(arg);
                }
            })(i)
        }
    }

####方法4：加一层闭包将 i 以局部变量

    function init() {
        var pAry = document.getElementsByTagName("p");
        for (var i = 0; i < pAry.length; i++) {
            (function() {
                var tmp = i; //局部变量
                pAry[i].onclick = function() {
                    alert(tmp);
                }
            })()
        }
    }

####方法5：返回一个函数作为响应事件（注意与3的细微区别）

    function init5() {
        var pAry = document.getElementsByTagName("p");
        for (var i = 0; i < pAry.length; i++) {
            pAry[i].onclick = function(arg) {
                return function() { //返回一个函数     
                    alert(arg);
                }
            }(i);
        }
    }    

####方法6：用Function实现，实际上每产生一个函数实例就会产生一个闭包

    function init6() {
        var pAry = document.getElementsByTagName("p");
        for (var i = 0; i < pAry.length; i++) {
            pAry[i].onclick = new Function("alert(" + i + ");"); //new一次就产生一个函数实例    
        }
    }

####方法7：用Function实现，注意与6的区别

    function init7() {
        var pAry = document.getElementsByTagName("p");
        for (var i = 0; i < pAry.length; i++) {
            pAry[i].onclick = Function('alert(' + i + ')')
        }
    }
    
*liujb整理*
