​###方法调用模式

    /**
     方法调用Function
     1、当一个function被保存为一个对象的属性时，我们称为method
     2、this绑定到该对象
     */
    var obj = {
        val: 0,
        getVal: function() {
            console.log(this); //{ value: 0, getVal: [Function] }，充分体现this指的就是obj这个对象
            console.log(this.toString()); //[object Object]
            return this.val;
        }
    };
    console.log(obj.getVal());
    //prototype只能用在类型上！！！不能用于对象上！！！

###函数调用模式
    
    /**
     函数调用模式
     1、当一个函数并非一个对象的属性时，那么就是当一个函数来调用的
     2、this指向全局对象（大胆猜想这种方案是错的）
     3、解决此方法的方案就是定义一个变量存储this对象
    */
    var add = function(a, b) {
        console.log(this.toString()); //[object global]全局变量啊
        return a + b;
    };
    console.log(add(2, 4));

###解决函数调用模式中this会指向全局变量的方法
    /**
     * 解决函数调用模式中this会指向全局变量的方法
     */
    var obj = {
        val: 4,
        getVal: function() {
            return this.val;
        }
    };
    obj.double = function() { //方法模式，double是obj对象的方法
        var that = this; //this指的就是obj对象
        var helper = function() { //函数模式
            that.val = that.val * 2;
        };
        helper();
    };
    obj.double(); //方法模式调用double
    console.log(obj.val); //

###构造器调用模式
    /**
     构造器调用模式
     1、如果一个函数前面带上一个new来调用，那么就是构造器调用模式
    */
    var Person = function(name) {
        console.log(this.constructor);
        this.name = name;
    };
    Person.prototype.getName = function() {
        return this.name;
    };
    var person = new Person('ALLEN');
    console.log(person.getName());

###apply/call调用模式
    /**
     Apply调用模式(apply/call)
     1、apply让我们构建一个参数数组传递给调用函数，也允许我们选择this的值
    */
    var func = function() {
        console.log(Object.prototype.toString.apply(this));
        console.log(this.value); //this本来指向全局变量，因为是函数调用模式
    };
    
    var obj1 = {
        value: 'This is the first object\'s value'
    };
    var obj2 = {
        value: 'This is the second object\'s value'
    };
    func.apply(obj1); //This is the first object's value
    func.apply(obj2); //This is the second object's value