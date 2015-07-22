##获取查询字符串

    /**
     * 查詢字符串
     */
    function getQuerySting() {
        var queryString = (location.search.length) ? location.search.substring(1) : '';
        var args = {};
        var items = queryString.split('&');
        var item = null,
            name = null,
            value = null;
        if (items) {
            for (var i = 0, len = items.length; i < len; i++) {
                item = items[i].split('=');
                name = decodeURIComponent(item[0]);
                value = decodeURIComponent(item[1]);
                args[name] = value;
            };
        } else {}
        return args;
    };

##检测浏览器插件

    /**
     * 检测浏览器插件两个版本
     * ①IE浏览器：以COM对象的方式实现插件
     * ②非IE浏览器：navigator.plugins数组中的每一个项都有name,description,filename,length
     */
    //非IE版本
    function hasNonIEPlugins(pluginsName) {
        pluginsName = pluginsName.toLowerCase();
        for (var i = 0, length = navigator.plugins.length; i < length; i++) {
            var item = navigator.plugins[i];
            if (item.name.toLowerCase().indexOf(pluginsName) > -1) {
                return true;
            } else {}
        };
        return false;
    };
    console.log('是否有Java:' + hasNonIEPlugins('Java'));
    //IE版本
    function hasIEPlugins(pluginName) {
        try {
            new ActiveXObject(pluginName);
            return true
        } catch (e) {
            return false;
        }
    };
    console.log('IE浏览器下是否有Flash插件:' + hasIEPlugins('ShockwaveFlash.ShockwaveFlash'));
    //检测是否有Flash插件
    function hasFlash() {
        var result = hasNonIEPlugins('Flash');
        if (!result) {
            result = hasIEPlugins('ShockwaveFlash.ShockwaveFlash');
        }
        return result;
    };
    console.log('检测浏览器下是否有Flash插件（各种浏览器）：' + hasFlash());
    
##获取文件扩展名
    
    /**
     * 获取文件扩展名
     */
    function getExtension(path) {
        var result = /\.[^\.]+/.exec(path);
        //或者 var result =/\.[A-z0-9]+/.exec(aa);  
        //这句更容易理解是不是 后面的加号还可以改成*结果是一样的
        return result;
    };
    
    /*一个更简单的方法 author:songchao*/
    function getExtension(path){
        return path.split('.').pop();
    }

##获取字符串的长度
    
    /*
     * 获取字符串的长度，中文算两个字符
     */
    function getStrLength(str) {
        var count = 0;
        if (str) {
            for (var i = 0, len = str.length; i < len; i++) {
                var c = str.charCodeAt(i);
                if ((c >= 0x0001 && c <= 0x007e) || (0xff60 <= c && c <= 0xff9f)) {
                    count++;
                } else {
                    count += 2;
                }
            }
        } else {}
        return count;
    };

####屏蔽特殊字符

    /*
     * 屏蔽特殊字符
     */
    function filterSpecialChar(str) {
        //var reg = /[\,\<\.\>\/\?\;\:\\\|\[\{\]\}\`\~\!\#\$\%\^\&\*\(\)\-\=\+\，\。\：\；\【\】\~\《\》\？\￥\！\……\（\）\ \"\'\@\“\”\‘\’\☆]/g;
        var reg = /[\,\<\.\>\/\?\;\:\\\|\[\{\]\}\`\~\!\#\$\%\^\&\*\(\)\-\=\+\，\。\：\；\【\\】\~\《\》\？\￥\！\……\（\）\ \""\''\@@\“”\‘’\☆]/g;
        str = str.replace(reg, "");​
        return str;
    }

##Cookies操作
    
    /**
     * [setCookie 写cookies]
     * @param {[type]} name
     * @param {[type]} value
     */
    function setCookie(name, value) {
        var exp = new Date();
        exp.setTime(exp.getTime() + 1 * 60 * 60 * 1000);
        document.cookie = name + "=" + escape(value) + ";expires=" + exp.toGMTString();
    };
    /**
     * [getCookie 读取cookies]
     * @param  {[type]} name
     * @return {[type]}
     */
    function getCookie(name) {
        var arr, reg = new RegExp("(^| )" + name + "=([^;]*)(;|$)");
        if (arr = document.cookie.match(reg)) {
            return unescape(arr[2]);
        } else {
            return null
        };
    };
    /**
     * [delCookie 删除cookies]
     * @param  {[type]} name
     * @return {[type]}
     */
    function delCookie(name) {
        var exp = new Date();
        exp.setTime(exp.getTime() - 1);
        var cval = getCookie(name);
        if (cval != null) {
            document.cookie = name + "=" + cval + ";expires=" + exp.toGMTString();
        } else {}
    };
    //使用示例  
    setCookie("name", "hayden");
    alert(getCookie("name"));

##获取浏览器版本

    /**
     * [GetBrowserVersion 获取浏览器版本]
     */
    function GetBrowserVersion() {
        var ua = navigator.userAgent.toLowerCase();
        var is = (ua.match(/ \b(chrome | opera | safari | msie | firefox)\b /) || ['', 'mozilla'])[1];
        var r = '(?:' + is + '|version)[\\/: ]([\\d.]+)';
        var v = (ua.match(new RegExp(r)) || [])[1];
        return v;
    };

##去除空格

    str.replace(/(^\s*)|(\s*$)/g,"");

##getElementsByClassName

    var getElesByClassName = function(node, className) {
        if (node.getElementsByClassName) {
            console.log('支持');
            return node.getElementsByClassName(className);
        } else {
            console.log('不支持');
            var res = [];
            var eles = node.getElementsByTagName("*");
            for (var i = 0, len = eles.length; i < len; i++) {
                if (eles[i].getAttribute) {
                    if (eles[i].getAttribute("class").indexOf(className) !== -1) {
                        res.push(eles[i]);
                    } else {}
                } else {}
            }
            return res;
        }
    };

    var getByClassName = function(className, parent) {
        var elem = [],
            p = new RegExp("(^|\\s)" + className + "(\\s|$)"),
            node = parent && parent.nodeType == 1 ? parent.getElementsByTagName('*') : document.getElementsByTagName('*');
    
        for (var n = 0, i = node.length; n < i; n++) {
            if (p.test(node[n].className)) {
                elem.push(node[n]);
            }
        }
        return elem;
    };

##字符串数组中最长项

    /**
     * 返回一个字符串数组中最长的字段
     */
    var maxString = function(_array) {
        // _array will be an array
        // return the longest string in the array
        return _array.sort(function(x, y) {
            if (typeof x === 'string' && typeof y === 'string') {
                return x.length < y.length;
            } else {
                return true;
            }
        })[0];
    };
