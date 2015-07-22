###Gulp-plugins-list

	
	npm install gulp-csslint --save-dev
	npm install gulp-jshint --save-dev
	npm install jshint-stylish --save-dev
	npm install --save-dev gulp-htmlhint
	
	npm install --save-dev gulp-cssbeautify
	npm install --save-dev gulp-csscomb
	npm install --save-dev gulp-esformatter
	npm install gulp-prettify --save-dev
	
	npm install gulp-concat --save-dev
	
	npm install --save-dev gulp-closure-compiler
	npm install gulp-compressor --save-dev
	npm install gulp-htmlmin --save-dev	
	npm install --save-dev gulp-imagemin
	npm install --save-dev gulp-minify-css
	npm install --save-dev gulp-uglify
	
	npm install --save-dev gulp-replace
	
	
	

###beautifier

1. [gulp-cssbeautifier](https://www.npmjs.org/package/gulp-cssbeautify/)
2. [gulp-csscomb](https://www.npmjs.org/package/gulp-csscomb/)
3. [gulp-esformattor](https://www.npmjs.org/package/gulp-esformatter/) [option](https://github.com/millermedeiros/esformatter/blob/master/lib/preset/default.json)
4. [gulp-beautify](https://www.npmjs.org/package/gulp-beautify/)
4. [gulp-htmlprettity](https://www.npmjs.org/package/gulp-prettify/)

注意：[jsbeautifier](http://jsbeautifier.org/) 比esformattor配置少一些，sublime有jsformat用的jsbeautifier插件，所以建议将sublime中的jsformat插件换成esformattor [sublime-esformatter](https://github.com/piuccio/sublime-esformatter)


###lint&hint

1. [gulp-csslint](https://www.npmjs.org/package/gulp-csslint/)
2. [gulp-jshint](https://www.npmjs.org/package/gulp-jshint/)
3. [gulp-jshint-stylish]()
4. [gulp-htmlhint](https://www.npmjs.org/package/gulp-htmlhint/)

###concat

1. [gulp-concat](https://www.npmjs.org/package/gulp-concat/)

###minify

1. [gulp-colsure-complier](https://www.npmjs.org/package/gulp-closure-compiler/)
2. [gulp-compressor](https://www.npmjs.org/package/gulp-compressor/)
		
		1. html minify is use htmlcompressor,all configs are valid.
		2. css and js minify is use yuicompressor,all configs are valid too.      
4. [gulp-minify-html](https://www.npmjs.org/package/gulp-minify-html/)
3. [gulp-htmlmin](https://www.npmjs.org/package/gulp-htmlmin/)
	-> [html-minifier](https://github.com/kangax/html-minifier)
2. [gulp-uglify](https://www.npmjs.org/package/gulp-uglify/) 
4. [gulp-imagemin](https://www.npmjs.org/package/gulp-imagemin/)
5. [gulp-minify-css](https://www.npmjs.org/package/gulp-minify-css/)
 
	- keepSpecialComments - * for keeping all (default), 1 for keeping first one only, 0 for removing all
	- keepBreaks - whether to keep line breaks (default is false)
	- benchmark - turns on benchmarking mode measuring time spent on cleaning up (run npm run bench to see example)
	- root - path to resolve absolute @import rules and rebase relative URLs
	- relativeTo - path with which to resolve relative @import rules and URLs
	- processImport - whether to process @import rules
	- noRebase - whether to skip URLs rebasing
	- noAdvanced - set to true to disable advanced optimizations - selector & property merging, reduction, etc.
	- compatibility - Force compatibility mode to ie7 or ie8. Defaults to not set.
	- debug - set to true to get minification statistics under stats property (see test/custom-test.js for examples)     

7. [gulp-jsmin](https://www.npmjs.org/package/gulp-jsmin/)

###replace

1. [gulp-replace](https://www.npmjs.org/package/gulp-replace/)
2. [gulp-assetpaths](https://www.npmjs.org/package/gulp-assetpaths/)


###images

1. [retina-sprites](https://www.npmjs.org/package/gulp-retina-sprites/)
2. [gulp-imagemin](https://www.npmjs.org/package/gulp-imagemin/) 
	3. [imageminplugin](https://www.npmjs.org/browse/keyword/imageminplugin) 

###others

1. [gulp-sftp](https://www.npmjs.org/package/gulp-sftp/)
2. [gulp-clean](https://www.npmjs.org/package/gulp-clean)
3. [gulp-rev-append](https://www.npmjs.org/package/gulp-rev-append/)
4. [gulp-rev-nocache](https://www.npmjs.org/package/gulp-uncache/)
5. [gulp-rev-mtime](https://www.npmjs.org/package/gulp-rev-mtime/)
6. [gulp-rev-hash](https://www.npmjs.org/package/gulp-rev-hash)
7. [gulp-buster](https://www.npmjs.org/package/gulp-buster)
8. [gulp-hash-src](https://www.npmjs.org/package/gulp-hash-src)
9. [gulp-hash-]