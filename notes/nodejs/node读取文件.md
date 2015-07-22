####node读取文件

**1、异步读取文件**

    var fs = require('fs');
    fs.readFile('file.txt', 'utf-8', function(err, data) {
        if (err) {
            console.error(err);
        } else {
            console.log(data);
        }
    });
    console.log('异步读取文件内容，不会阻塞进程，reading...');

**2、同步读取文件**

     var data = fs.readFileSync('file.txt', 'utf-8'); //
     console.log(data);
     console.log('同步读取文件内容，会阻塞进程，reading...');

**3、异步读取时回调函数写外边**

    //读取文件的回调函数
    function readFileCallback(error, data) {
        if (error) {
            console.error(error);
        } else {
            console.log(data);
        }
    };
    fs.readFile('file.txt', 'utf-8', readFileCallback); //跟第一种很相似
    console.log('回调函数方式阻塞文件内容，reading....');