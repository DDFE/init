###checkType.js

####检测一个对象是否为特定的类型

    /**
     * 检测一个对象是否为特定的类型
     * 接收两个参数
     * 第一个参数为对象
     * 第二个参数为特定的类型比如'Number'
     * @return bool
     */
    var check = function() {
        if (arguments.length === 2) {
            return Object.prototype.toString.call(arguments[0]) === '[object ' + arguments[1] + ']';
        } else {}
    };

####检测对象是否为数字

    var isNum = function(val) {
        return check(val, 'Number');
    };

####检测对象是否为字符串

    var isString = function(str) {
        return check(str, 'String');
    };

####检测对象是否为布尔值

    var isBoolean = function(obj) {
        return check(obj, 'Boolean');
    };

####检测对象是否为Null

    var isNull = function(obj) {
        return check(obj, 'Null');
    };

####检测对象是否为Undefined

    var isUndefined = function(obj) {
        return check(obj, 'Undefined');
    };

####检测对象是否为数组

    var isArray = function(obj) {
        return check(obj, 'Array');
    };

####检测对象是否为Object

    var isObj = function(obj) {
        return check(obj, 'Object');
    };

####检测对象是否为函数

    var isFunc = function(obj) {
        return check(obj, 'Function');
    };

####检测对象是否为日期

    var isDate = function(obj) {
        return check(obj, 'Date');
    };

####检测对象是否为正则表达式

    var isReg = function(obj) {
        return check(obj, 'RegExp');
    };