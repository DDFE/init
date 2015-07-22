#减少图片http请求次数的方法优缺点

##1.WebFont

###优点
* 图标字体，字体图标高性能，易维护，本身就是字符，因为可以很好地享受CSS诸多属性控制，**CSS对字体的属性操作都可以应用啦**	

* 当然，我们有很多场景是用纯色icon，特别是在Windows 8这种Metro UI开始越来越多的时候。
另外，这种方法可以**有效减少页面的请求**，但是对于习惯使用CSSGaGa的auto sprite功能的同学来说，这种方法对页面性能的提升不大。

* 但是**对于移动终端，特别是webapp中，这种方法还是有很大的用武之地的，可以很方便的兼容多分辨率，配合离线存储效果更佳。**

###缺点
* 其实，这种方法有一个不足，**就是只支持纯色icon**，最多能高端浏览器上实现渐变色或图形蒙板。
##2.CSS Sprites

###优点：
CSS Sprites为什么突然跑火，跟能够提升网站性能有关。显而易见，这是它的巨大优点之一。

* 利用CSS Sprites能很好地**减少了网页的http请求**，从而大大的提高了页面的性能，这是CSS Sprites最大的优点，也是其被广泛传播和应用的主要原因；

* 个人认为CSS Sprites**能减少图片的字节**，我曾经比较过多次3张图片合并成1张图片的字节总是小于这3张图片的字节总和。

###缺点：
诚然CSS Sprites是如此的强大，但是也存在一些不可忽视的缺点。

* 在图片合 并的时候，你要把多张图片有序的合理的合并成一张图片，还要**留好足够的空间**，防止板块内不会出现不必要的背景，否则可能会出          现出现干扰图片的情况；

* 这些还好，**做痛苦的是在宽屏，高分辨率的屏幕下的自适应页面，你的图片如果不够宽，很容易出现背景断裂；**

* CSS Sprites在**开发的时候比较麻烦**，你要通过photoshop或其他工具测量计算每一个背景单元的精确位置，这是针线活，没什么难度，但是很繁琐；不过网上已经有高手开发出“CSS Sprites 样式生成工具”，大家可以尝试一下。

* CSS Sprites在**维护的时候比较麻烦**，sprites是一把双刃剑，如果页面背景有少许改动，一般就要改这张合并的图片，无需改的地方最好不要动，这样避免改动更多的css，如果在原来的地方放不下，有只能（最好）往下加图片，这样图片的字节就增加了，因为每次的图片改动都得往这个图片删除或添加内容，显得稍微繁琐，而且**重新算图片的位置**（尤其是这种上千px的图）也是一件颇为不爽的事情。当然，在性能的口号下，这些都是可以克服的。

* 由于图片的位置需要固定为某个绝对数值，这就**失去了诸如center之类的灵活性。**

##3.Data URL

大家可能注意到了，网页上有些图片的src或css背景图片的url后面跟了一大串字符，比如：data:image/png;base64,　iVBORw0KGgoAAAANSUhEUgAAAAEAAAAkCAYAAABIdFAMAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAHhJREFUeNo8zjsOxCAMBFB/　KEAUFFR0Cbng3nQPw68ArZdAlOZppPFIBhH5EAB8b+Tlt9MYQ6i1BuqFaq1CKSVcxZ2Acs6406KUgpt5/　LCKuVgz5BDCSb13ZO99ZOdcZGvt4mJjzMVKqcha68iIePB86GAiOv8CDADlIUQBs7MD3wAAAABJRU5ErkJggg%3D%3D。那么这是什么呢？

这是Data URI scheme。Data URI scheme是在RFC2397中定义的，**目的是将一些小的数据，直接嵌入到网页中，从而不用再从外部文件载入**。

在上面的Data URI中，

**data表示**取得数据的协定名称，

**image/png**是数据类型名称，

**base64** 是数据的编码方法，

**逗号后面**就是这个image/png文件base64编码后的数据。

下面的地址可以转换哦~~
[http://websemantics.co.uk/online_tools/image_to_data_uri_convertor/](http://websemantics.co.uk/online_tools/image_to_data_uri_convertor/)

###优点
* 我们把图像文件的内容直接写在了HTML 文件中，这样做的好处是，**节省了一个HTTP 请求**。

###缺点
* 坏处呢，就是**浏览器不会缓存这种图像**。

对于他们的优缺点，我们在不同的应用环境下会有不同的取舍，来发挥他们最大的优点