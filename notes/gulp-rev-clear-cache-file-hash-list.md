	
	var rev = require('gulp-rev-append');
	var revTime = require('gulp-rev-mtime');
	var uncache = require('gulp-uncache');
	var revHash = require('gulp-rev-hash');
	var hash_src = require("gulp-hash-src"); //值得好好研究
	
	
	/**
	 * 限制就是html中引用的东东必须有 ?rev=@@hash
	 * 使用的正则表达式为：(?:href|src)="(.*)[\?]rev=(.*)[\"]
	 * 要想满足 url() 和 自定义 asyncLoadJs() 也支持需要重新构造regexp
	 * @return {[type]} [description]
	 */
	gulp.task('rev-append', function() {
	    gulp.src('./home.html')
	        .pipe(rev())
	        .pipe(gulp.dest('./dist'));
	});
	
	/**
	 * 不需要修改html结构
	 * 只支持css,js不支持背景图片，实现不依赖于regexp，使用dom元素对象
	 * @return {[type]} [description]
	 */
	gulp.task('rev-append-time', function() {
	    gulp.src('./home.html')
	        .pipe(revTime({
	            'cwd': '',
	            'suffix': 'rev',
	            'fileTypes': ['css','js']
	        }))
	        .pipe(gulp.dest('./dist'));
	});
	
	/**
	 * 限制就是html必须有<!--uncache-->
	 * 可支持rename，这个超赞
	 * @return {[type]} [description]
	 */
	gulp.task('uncache', function() {
	    return gulp.src('./home.html')
	    .pipe(uncache({
	        append: 'hash',
	        rename: false // srcDir: '/static/webapp/', // distDir: './dist' // template: '{{path}}{{name}}.{{extension}}?v={{append}}'
	    }))
	    .pipe(gulp.dest('./dist'));
	});
	
	/*
	 * 限制是必须有html comment <!- rev-hash -> 
	 * 使用正则表达式去匹配
	 * 要实现url() 和自定义的 asyncLoadJs()需要修改源码
	 */
	gulp.task('rev-hash', function() {
	    gulp.src('./home.html')
	        .pipe(revHash())
	        .pipe(gulp.dest('./dist'));
	});
	
	/**
	 * 
	 * 只支持href=,src=,url()三种形式的替换，如果需要匹配自定义的asyncLoadJs需要自己去修改源码更改中的正则表达式
	 * 不需要修改任何html结构，直接搞即可
	 * @type {[type]}
	 */
	gulp.task("hash-src", function() {
	    return gulp.src('./*.html')
	    .pipe(hash_src({
	        build_dir: "/", //js/css/images所在的文件根目录
	        src_path: "./", //要替换引用的html文件目录
	        hash: 'md5',
	        enc: 'base64', //hex，
	        exts: ['.js', '.css'],
	        query_name: "v"
	    }))
	    .pipe(gulp.dest("./build"));
	});