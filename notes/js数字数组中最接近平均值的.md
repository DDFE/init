	/*
	 * 代码片段，js数组中最接近平均值的数字
	 */
    if (dataArray.length) {
        var data = []; //最后要得到的数组
        var sum = 0,
            average = 0;
    
        //求数组的平均值
        for (var i = 0, length = dataArray.length; i < length; i++) {
            var value = parseInt(dataArray[i]);
            sum += value;
            data.push(value);
        };
        average = sum * 1.0 / dataArray.length; //平均值
    
        var abs_array = [], //各个项与平均值相减后的绝对值数组
            tmp_array = [], //abs_array的一个副本，用来找位置
            index_array = []; //索引数组容器
        for (var i = 0; i < dataArray.length; i++) {
            abs_array.push(Math.abs(average - parseInt(dataArray[i]))); //填充绝对值数组
        };
        tmp_array = abs_array.concat(); //副本
        abs_array.sort(); //对相减后的绝对值数组进行排序
    
        /*循环绝对值副本数组，找出最小项的位置*/
        for (var i = 0; i < tmp_array.length; i++) {
            if (abs_array[0] == tmp_array[i]) { //第一个肯定就是绝对值最小的，绝对值最小对应的就是最接近平均值
                index_array.push(i); //将绝对值最小的那个项在原绝对值数组中的索引添加到索引数组中
            } else {}
        };
        /*循环索引数组，将原data数组中对应位置的项改成想要的object*/
        for (var i = 0; i < index_array.length; i++) {
            var index = index_array[i], //最接近平均值的项的索引
                value = dataArray[index]; //最接近平均值的项
            if (0 != parseInt(value)) {
                var obj = generateObject(value);
                data[index] = obj; //替换数组中的指定位置的项
            } else {}
        };
        //generateChart(title, regionArray, data);
    } else {}