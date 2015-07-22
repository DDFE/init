问题
  
    if ([] == ![]) {
        console.log('A');
    } else {
        console.log('B');
    } //提问：以上到底是输出 A 还是 B 呢？
    
注意：

    console.log([] == false); //true????真的很奇怪，[]是一个数组。
    console.log([] == true); //false
    if ([]) {
        alert('true') //弹出true
    }
    console.log(![]); //false
    console.log( !! []); //true

**也就是说：在做==时，js的执行到底做了什么？**

>  解答：终于尼玛找到答案了    
> `[]==![]`相当于`[]==false`(没有异议了吧因为![]就是false)    
> `[]==false`又是怎么转化的呢，对于Object类型先转化成基础类型Number，为0    
> `0==false`又将false转化为Number也是为0    
> 所以两者相等。    

####附上比较规则，ECMA这帮人写的算法过程比较啰嗦！一句话来概括就是：

- 对于基本类型Boolean，Number，String，三者之间做比较时，总是向 Number进行类型转换，然后再比较；
- 如果有Object，那么将Object转化成这三种基本类型（PS：到底转换成哪一种呢？我猜测会转化成Number），再进行基本类型比较；
- 对于null和undefined，只有 x，y分别是它们时才相同，其他都为false。

> PS：对于类型相同那么==操作符就会直接比较值，不会再进行转换了！

#####！最后！在JS中尽量少和使用同等运算符===和!==避免使用==和!=


