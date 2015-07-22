##Async gulp task
*gulp是基于nodejs中，在node中所有操作都是异步进行的，如果下一个任务依赖于上一个任务完成，异步可能导致上一个任务还没有完成，下一个任务就已经执行了，这样就会出错！！！*

解决这个问题有以下几种方法；

###gulp.task('taskname',['deps tasks'],function(){});

利用gulp自身的依赖任务，可以完成简单依赖关系的任务，若“依赖”任务间还有依赖，完蛋了。

	gulp.task('default', ['compressor'], function() {
	    return gulp.src(['./dist', './compressor'])
	    .pipe(clean({
	        force: true,
	        read: false
	    }));
	});

###恶心的回调

	var exec = require('child_process').exec;
	gulp.task("sss", function(cb) {
	    exec('gulp htmlbty', function(err) {
	        console.log('finished bty');
	
	        exec('gulp htmlhint', function(err) {
	            console.log('finished lint');
	
	            exec('gulp switchPaths', function(err) {
	                console.log('finished replace');
	
	                exec('gulp compressor', function(err) {
	                    console.log("finished compressed");
	                });
	            });
	        });
	    });
	});
	
	
###Return a stream

###Q.promise