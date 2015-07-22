##Gulp一个牛逼的构建工具－－简易&快速入门

[gulp一个牛逼的构建工具](https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md)
[参考1](http://qianduanblog.com/post/nodejs-learning-14-gulp.html)
[参考2](http://blog.segmentfault.com/laopopo/1190000000372547)

###不解释，gulp前端构建工具快速入门

1. 自备node和npm开发环境。
1. `npm install gulp -g` -- 不解释
2. 进入工作目录，然后`npm install gulp --save-dev` -- 不解释
3. `npm install <Plugin name> --save-dev` like `gulp-concat`|`gulp-upfily` -- 不解释
4. `touch gulpfile.js` -- 不解释
5. coding  
	
		/**
		 * gulp构建工具使用
		 * @type {Gulp|exports}
		 */
		var mGulp = require('gulp');
		
		/**
		 * 引入构建所需插件
		 * @type {exports}
		 */
		var mUglify = require('gulp-uglify');
		var mRename = require('gulp-rename');
		var jshint = require("gulp-jshint");
		var concat = require("gulp-concat");
		
		/**
		 * 定义js检查任务
		 */
		mGulp.task('checkjs', function () {
		    return mGulp.src("./src/*.js")
		        .pipe(jshint())
		        .pipe(jshint.reporter('default'));
		});
		
		/**
		 * 定义压缩任务
		 */
		mGulp.task('minjs', function () {
		    return mGulp.src('./src/*.js')  // 源地址
		        .pipe(mUglify({  // 压缩
		            preserveComments: 'some' // 保留注释部分
		        }))
		
		        .pipe(mRename({ // 重命名
		            extname: '.min.js' // 文件后缀
		        }))
		
		        .pipe(mGulp.dest('./compressed/')); // 目标地址
		});
		
		/**
		 * 定义合并任务
		 */
		mGulp.task("concat",function(){
		    return mGulp.src('./src/*.js') //原文件为src下的js文件
		        .pipe(concat('all.js')) // 合并为all.js
		        .pipe(mGulp.dest('dist')) // 将合并后的all.js放到dist下
		        .pipe(mUglify()) // 压缩合并后的all.js
		        .pipe(mRename('all.min.js')) //重命名为all.min.js
		        .pipe(mGulp.dest('dist')); // 放到dist下
		});
		
		
		
6. run `gulp` 执行默认任务
7. `gulp concat` 执行指定任务
	
	一次性执行所有任务，或者执行特定的任务