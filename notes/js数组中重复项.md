##去除数组中重复项

    var arr = [1, 1, 2, 3, 33, 4, 4, 5];

####方法1

    var func1 = function(arr) {
        for (var i = 0, len = arr.length; i < len; i++) {
            for (var j = i + 1; j < len; j++) {
                if (arr[i] === arr[j]) {
                    arr.splice(j, 1); //删除j位置的元素并返回删除后的数组
                    break;
                } else {}
            }
        }
    };

####方法2

    var func2 = function(arr) {
        var newArr = [];
        for (var i = 0, len = arr.length; i < len; i++) {
            for (var j = i + 1; j < len; j++) {
                if (arr[i] === arr[j]) {
                    j = false;
                    break; //发现元素相同则跳出循环
                } else {}
            }
            if (j) {
                newArr.push(arr[i]);
            } else {}
        }
        return newArr;
    };

####方法3

    function func3(ar) {
        var m, n = [],
            o = {};
        for (var i = 0;
            (m = ar[i]) !== undefined; i++)
    
            if (!o[m]) {
                n.push(m);
                o[m] = true;
            }
        return n.sort(function(a, b) {
            return a - b；
        });
    }
    arr = func2(arr);
    console.log(arr.toString());