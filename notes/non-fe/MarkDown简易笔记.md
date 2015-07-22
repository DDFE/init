[参考地址](http://wowubuntu.com/markdown/#philosophy)

##1、宗旨
    易读易写

##2、目标
    Markdown 语法的目标是：成为一种适用于网络的书写语言。

##3、与HTML关联

    1.Markdown 不是想要取代 HTML，甚至也没有要和它相近，它的语法种类很少，只对应 HTML 标记的一小部分。
    2.Markdown 的构想不是要使得 HTML 文档更容易书写。在我看来， HTML 已经很容易写了。
    3.Markdown 的理念是，能让文档更容易读、写和随意改。
    4.HTML 是一种发布的格式，Markdown 是一种书写的格式。
    5.Markdown 的格式语法只涵盖纯文本可以涵盖的范围。

####特殊字符 & <
没大看懂

####段落和换行：
    按两个以上的空格然后按一下Enter就行了，建议使用区块引用

####标题（类 Setext 和类 atx 形式）
> 1）=====，最高阶标题
> 2）---------，第二阶标题
> 3）#，1-6个#号对应标题1-标题6（为了美感，建议闭合，如##标题2##）
> 建议使用3）来书写标题

####区块引用Blockquotes
Markdown 标记区块引用是使用类似 email 中用 > 的引用方式

> 1）可以在每行前边加上>
> 2）可以偷懒只在第一行加上>
> 3）可以嵌套>
> 4）嵌套列表

####无序列表

> 1）*
> 2）+
> 3）-

####有序列表
数字加英文句点如：1. 

####代码区域
> 使用4个空格或者tab

####分割线：
> 1）三个以上的星号
> 2）减号
> 3）或者底线______

####链接

    1）行内式：This is [ an example](http://www.baidu.com "Baidu") inline link
    2）相对地址：See my [About](/about/) page for details.
    3）参考式：
    This is [an example] [id] reference-style link
    [id]:http://baidu.com "Baidu"    这一行可以写在文档的任何位置

####强调：

    1）四个星号：**强调**，而*强调*会成为斜体
    2）四个底线：__强调__，而_强调_会成为斜体    

####小段代码
> 两个反引号括起来：`var name = 'allen'`

####图片

    1）行内式：![Alt text](http://www.baidu.com/imgs/a.jpg)
    如：![图片](http://apollo.s.dpool.sina.com.cn/nd/phototravel/vision/image/e2/74/1370414209_578744310_1728743920_0_60.jpg)
    2）参考式：
    ![Alt text][id]
    [id]: http://www.baidu.com/imgs/a.jpg
    如：
    ![图片][id]
    [id]: http://apollo.s.dpool.sina.com.cn/nd/phototravel/vision/image/e2/74/1370414209_578744310_1728743920_0_60.jpg

####自动连接

    <http://www.baidu.com>

####反斜杠
    \   反斜线
    `   反引号
    *   星号
    _   底线
    {}  花括号
    []  方括号
    ()  括弧
    #   井字号
    +   加号
    -   减号
    .   英文句点
    !   惊叹号
    
    
*著名出处liujb*
 
 
 
 
 
 
 
 
 
 
 
 