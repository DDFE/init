`var x = 30, y = 45;//定义两个变量`
####全局对象中跟数字有关的方法

    isNaN() //检查某个值是否是数字。
    Number() //把对象的值转换为数字。
    parseFloat() //解析一个字符串并返回一个浮点数。 
    parseInt() //解析一个字符串并返回一个整数。

####Number对象的方法

    console.log(11.24567.toString(8)); //把数字转换为字符串，使用指定的基数如8进制，16进制。
    console.log(11.24567.toFixed(2)); // 把数字转换为字符串，保留指定小数位.
    console.log(111111.24567.toExponential()); //把对象的值转换为指数计数法.
    console.log(11.25567.toPrecision(3)); //把数字格式化为指定的长度。


####返回随机数

    console.log(Math.random()) //返回 0 ~ 1 之间的随机数

####四舍五入

    console.log(Math.floor(x)) //对数进行下舍入
    console.log(Math.ceil(x)) //对数进行上舍入
    console.log(Math.round(x)) //把数四舍五入为最接近的整数

####绝对值平局数

    console.log(Math.abs(x)) //返回数的绝对值
    console.log(Math.sqrt(x)) //返回数的平方根
    
####最大值最小值

    console.log(Math.max(x, y)) //返回 x 和 y 中的最高值
    console.log(Math.min(x, y)) //返回 x 和 y 中的最低值

####三角函数

    console.log(Math.sin(x)) //返回数的正弦
    console.log(Math.cos(x)) //返回数的余弦
    console.log(Math.tan(x)) //返回角的正切
    console.log(Math.atan2(y, x)) //返回从 x 轴到点 (x,y) 的角度（介于 -PI/2 与 PI/2 弧度之间）
    console.log(Math.acos(x)) //返回数的反余弦值
    console.log(Math.asin(x)) //返回数的反正弦值
    console.log(Math.atan(x)) //以介于 -PI/2 与 PI/2 弧度之间的数值来返回 x 的反正切值
    
####指数和幂

    console.log(Math.exp(x)) //返回 e 的指数
    console.log(Math.log(x)) //返回数的自然对数（底为e）
    console.log(Math.pow(x, y)) //返回 x 的 y 次幂

####其他方法

    //console.log(Math.toSource()) //返回该对象的源代码
    //console.log(Math.valueOf()) //返回 Math 对象的原始值