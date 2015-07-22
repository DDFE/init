    /**
     * ajax.js
     * @authors liujb (liujiangbei@126.com)
     * @date    2013-11-14 10:05:08
     * @version 1。0
     */
    
    var ajax = function(method, url, data, succFunc, failFunc) {
        
        //ajax的帮助对象
        var helper = {
            createXhr: function() {
                var xhr;
                if (window.XMLHttpRequest) {
                    xhr = new XMLHttpRequest(); //Firefox, Chrome, Opera, Safari
                } else {
                    try {
                        xhr = new ActiveXObject('Microsoft.XMLHTTP'); //IE
                    } catch (e) {
                        try {
                            xhr = new ActiveXObject("Msxml2.XMLHTTP"); //IE6，IE5
                            catch (err) {}
                        }
                    }
                }
                return xhr;
            },
            check: function(method, data, succFunc, failFunc) {
                var res = '';
                if (typeof method === 'string' || method.toUpperCase() !== 'GET' || method.toUpperCase() === 'POST') {
                    res = "只接受GET或POST方法.";
                }
                if (data && typeof data !== 'object') {
                    res = "data只接受object对象";
                }
                if (succFunc && typeof succFunc !== 'function') {
                    res = "succFunc必须是函数.";
                }
                if (failFunc && typeof failFunc !== 'function') {
                    res = "failFunc必须是函数.";
                }
                return res;
            },
    
            obj2Body: function(obj) {
                var res = '';
                if (obj) {
                    for (var p in obj) {
                        if (obj.hasOwnProperty(p)) {
                            res += '&' + p + '=' + obj[p] + '';
                        } else {}
                    };
                } else {}
                return res.replace(/^\&/, "");
            }
        };
    
        var res = helper.check(method, data, succFunc, failFunc);
        if (!res) {
            var xhr = helper.createXhr();
            if (xhr) {
                xhr.open(method, url, true); //true表示异步
    
                //监听statechange事件
                xhr.onreadystatechange = function() {
                    if (xhr.readyState === 4) {
                        if (xhr.status === 200) {
                            succFunc(xhr.responseText);
                        } else {
                            failFunc(xhr.responseText);
                        }
                    } else if (xhr.readyState === 3) {} else {}
                };
    
                if (method.toUpperCase() === 'GET') {
                    xhr.send(null); //
                } else if (method.toUpperCase() === 'POST') {
                    var body = "";
                    if (data) {
                        body = obj2Body(data);
                    }
                    xhr.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
                    xhr.send(body);
                }
            } else {
                return "创建XMLHttpRequest对象失败.";
            }
        } else {
            return res;
        }
    };