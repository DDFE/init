###gulp-complier-list
	
	/**
	* google-closure-complier
	*/
	gulp.task('colsureComplier', function() {
	   gulp.src('src/*.js')
	       .pipe(closureCompiler({
	           compilerPath: 'bower_components/closure-compiler/compiler.jar',
	           fileName: 'build.js'
	       }))
	       .pipe(gulp.dest('dist'));
	});
	
	/**
	* html compressor
	*/
	gulp.task('htmlmin', function() {
	   gulp.src('src/*.html')
	       .pipe(compressor({
	           'remove-intertag-spaces': true,
	           'simple-bool-attr': true,
	           'compress-js': true,
	           'compress-css': true
	       }))
	       .pipe(gulp.dest('html_min'));
	});
	
	/**
	* js compressor
	*/
	gulp.task('jsmin', function() {
	   gulp.src('src/*.js')
	       .pipe(compressor())
	       .pipe(gulp.dest('js_min'));
	});
	
	/**
	* css compressor
	*/
	gulp.task('cssmin', function() {
	   gulp.src('src/*.css')
	       .pipe(compressor())
	       .pipe(gulp.dest('css_min'));
	});
	
	/**
	* htmlminify
	*/
	gulp.task('minify', function() {
	   gulp.src('./src/*.html')
	       .pipe(htmlmin({
	           collapseWhitespace: true
	       }))
	       .pipe(gulp.dest('./html_min'));
	});
	
	/**
	* cssminify
	*/
	gulp.task('minify-css', function() {
	   gulp.src('./src/*.css')
	       .pipe(minifyCSS({
	           keepBreaks: false
	       }))
	       .pipe(gulp.dest('./css_min2/'));
	});
	
	/**
	 * imagemin
	 */
	gulp.task('imgmin', function() {
	    return gulp.src('images/*')
	    .pipe(imagemin({
	        progressive: true,
	        svgoPlugins: [{
	                removeViewBox: false
	            }],
	        use: [pngcrush()]
	    }))
	    .pipe(gulp.dest('images_min'));
	});
