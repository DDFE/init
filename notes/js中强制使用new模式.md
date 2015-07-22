####1、以new操作符调用构造函数的过程类似于：

    var Person = function(name) {
        //init a object
        //var this = {};
        //注意：var this = {};并不是真的空，它从Person的prototype中继承了很多成员
        //他更像var this = Object.create(Person.prototype)
    
        //add method and properties to objects
        this.name = name;
        this.sayName = function() {
            console.log(this.name);
        }
    
        //return this object
        //return this;
    };
验证一下：

    var p1 = new Person('ALLEN'),
        p2 = new Person('ALLEN');
    alert(p1.sayName === p2.sayName); //false

将`sayName()`方法添加到this中造成的后果就是每`new Person()`都会在内存中创建一个新的函数，这效率很明显比较低下，解决方法就是往`prototype`属性中添加方法。
如：

    Person.prototype.sayName(){
        console.log(this.name);
    };
验证一下：

    var p1 = new Person('ALLEN'),
        p2 = new Person('FUCK');
    alert(typeof p1.sayName); //function
    alert(p1.sayName.constructor === Function); //true
    alert(p1.sayName === p2.sayName); //true

####2、强制使用new的模式：

①问题：

    var Person = function(name) {
        this.name = name;
    };
    var p1 = new Person("ALLEN");
    var p2 = Person("JiangBei");
    alert(p1.name); //ALLEN
    alert(p2.name); //undefined
    alert(window.name); //Jiangbei
    //原因：如果忘记使用new操作符调用构造函数，那么构造函数的this将会指向全局变量，在浏览器中this会指向window对象。
    //我们尽量保持全局变量的整洁性。

②强制new的第一方案：

    var Person = function(name) {
        var that = {};
        that.name = name;
        return name;
    };
    //或者
    var Person = function(name) {
        return {
            name: name;
        };
    };
这样，任何一种方式访问Person()都会返回一个对象。

    var p1 = new Person('ALLEN'),
        p2 = Person('Liu');
    alert(p1.name); //ALLEN
    alert(p2.name); //Liu
但是这样做有一个问题：会丢失到原型的链接。

②强制使用new的完美方案

    var Person = function(name) {
        if (!(this instanceof Person)) {
            return new Person(name);
        } else {}
        //此处更好的代码是
        //if(!(this instanceof arguments.callee)){
        //    return new arguments.callee(name);
        //}else{}
        this.name = name;
    };
    Person.prototype.sayName = function() {
        alert(this.name);
    }:
    //arguments.callee就是函数本身

PS：原型测试

    var Person = function() {
        this.name = "ALLEN";
    };
    
    var p1 = new Person();
    alert(p1.constructor === Person); //true
    alert(p1.__proto__ === Person.prototype); //true
     
  