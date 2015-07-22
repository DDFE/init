##Javascript编译器



###1. [Closure Compiler](https://developers.google.com/closure/compiler/?csw=1)

-----

####What are the benefits of using Closure Compiler?

- Efficiency. The Closure Compiler reduces the size of your JavaScript files and makes them more efficient, helping your application to load faster and reducing your bandwidth needs.

- Code checking. The Closure Compiler provides warnings for illegal JavaScript and warnings for potentially dangerous operations, helping you to produce JavaScript that is less buggy and easier to maintain.

####How can I use the Closure Compiler?


- An open source Java application that you can run from the command line.
- A simple web application.
- A RESTful API.
 
####How do I start

- Work through the [UI Compiler Introduce](https://developers.google.com/closure/compiler/docs/gettingstarted_ui) ＝》[UI Compiler](http://closure-compiler.appspot.com/home)
- Work through the [API Hello World](https://developers.google.com/closure/compiler/docs/gettingstarted_api) ＝》[Closure Compiler API Config](https://developers.google.com/closure/compiler/docs/api-tutorial1)
- [Download the appliction](https://dl.google.com/closure-compiler/compiler-latest.zip)
- [Getting Started with the Closure Compiler Application](https://developers.google.com/closure/compiler/docs/gettingstarted_app)
- [Advanced Compilation and Externs](https://developers.google.com/closure/compiler/docs/api-tutorial3)

###2. [YUI Compressor](https://github.com/yui)

----------

1. [Download YUI Compressor](https://github.com/yui/yuicompressor/blob/master/README.md)
2. [Documents](https://github.com/yui/yuicompressor/blob/master/README.md)
3. `java -jar yuicompressor-x.y.z.jar myfile.js -o myfile-min.js` 
4. `java -jar yuicompressor-x.y.z.jar myfile.js -o myfile-min.js --charset utf-8`

[yuicompressor](http://yui.github.io/yuicompressor/)


####options

	java -jar yuicompressor-x.y.z.jar
	Usage: java -jar yuicompressor-x.y.z.jar [options] [input file]
	
	  Global Options
	    -h, --help                Displays this information
	    --type &lt;js|css&gt;           Specifies the type of the input file
	    --charset &lt;charset&gt;       Read the input file using &lt;charset&gt;
	    --line-break &lt;column&gt;     Insert a line break after the specified column number
	    -v, --verbose             Display informational messages and warnings
	    -o &lt;file&gt;                 Place the output into <file> or a file pattern.
	                              Defaults to stdout.
	
	  JavaScript Options
	    --nomunge                 Minify only, do not obfuscate
	    --preserve-semi           Preserve all semicolons
	    --disable-optimizations   Disable all micro optimizations
	
	GLOBAL OPTIONS
	
	  -h, --help
	      Prints help on how to use the YUI Compressor
	
	  --line-break
	      Some source control tools don't like files containing lines longer than,
	      say 8000 characters. The linebreak option is used in that case to split
	      long lines after a specific column. It can also be used to make the code
	      more readable, easier to debug (especially with the MS Script Debugger)
	      Specify 0 to get a line break after each semi-colon in JavaScript, and
	      after each rule in CSS.
	
	  --type js|css
	      The type of compressor (JavaScript or CSS) is chosen based on the
	      extension of the input file name (.js or .css) This option is required
	      if no input file has been specified. Otherwise, this option is only
	      required if the input file extension is neither 'js' nor 'css'.
	
	  --charset character-set
	      If a supported character set is specified, the YUI Compressor will use it
	      to read the input file. Otherwise, it will assume that the platform's
	      default character set is being used. The output file is encoded using
	      the same character set.
	
	  -o outfile
	
	      Place output in file outfile. If not specified, the YUI Compressor will
	      default to the standard output, which you can redirect to a file.
	      Supports a filter syntax for expressing the output pattern when there are
	      multiple input files.  ex:
	          java -jar yuicompressor.jar -o '.css$:-min.css' *.css
	      ... will minify all .css files and save them as -min.css
	
	  -v, --verbose
	      Display informational messages and warnings.
	
	JAVASCRIPT ONLY OPTIONS
	
	  --nomunge
	      Minify only. Do not obfuscate local symbols.
	
	  --preserve-semi
	      Preserve unnecessary semicolons (such as right before a '}') This option
	      is useful when compressed code has to be run through JSLint (which is the
	      case of YUI for example)
	
	  --disable-optimizations
	      Disable all the built-in micro optimizations.
