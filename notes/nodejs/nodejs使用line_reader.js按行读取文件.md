####Nodejs使用line_reader.js按行读取文件
    var input = '110226',
        fs = require('fs'),
        lineReader = require('./line_reader.js');
    
    //node异步读取文件内容到string
    fs.readFile('num_region_map.txt', 'utf-8', function(err, data) {
        if (!err) {
            console.log(data);
        } else {}
    });
    
    
    //读取文件内容并按行写入数组
    var arr = [];
    lineReader.eachLine('num_region_map.txt', function(line) {
        arr.push(line);
    }).then(function() {
        for (var i = 0; i < arr.length; i++) {
            var line = arr[i].slice(0, 6);
            if (line === input) {
                console.log(arr[i].slice(7));
            }
        };
        console.log(arr.length); //output the length of array
        console.log("I'm done!!");
    });
    
    
    //按行读取文件并构造对象
    var obj = {};
    lineReader.eachLine('num_region_map.txt', function(line, last) {
        var key = line.slice(0, 6),
            val = line.slice(7, line.length);
        obj[key] = val;
        if (last) {
            console.log(obj['110226']); //读取对象的属性
            return false; // stop reading
        } else {}
    });
    
    
    //按行读取文件并自定义回调函数
    lineReader.eachLine('num_region_map.txt', function(line, last, cb) {
        console.log(line);
        if (!last) {
            cb(false); // stop reading
        } else {
            cb();
        }
    });
    
    //read line by line
    lineReader.open('num_region_map.txt', function(reader) {
        if (reader.hasNextLine()) {
            reader.nextLine(function(line) {
                console.log(line);
            });
        } else {}
    });