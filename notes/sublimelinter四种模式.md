###SublimeLinter有四种模式###
    1. true：用户输入时在后台进行即时校验
    2. false：只有在初始化时候才进行校验
    3. "load-save"：只有在加载的时候进行校验
    4. "save-only"：在保存的时候就会进行校验

###配置SublimteLinter的校验引擎
    "sublimelinter_executable_map":
    {
        "javascript":"D:/nodejs/node.exe",
        "css":"D:/nodejs/node.exe"
    }
    
###SublimeLinter默认使用jshint的options
    "jshint_options":
    {
        "strict": true,
        "noarg": true,
        "noempty": true,
        "eqeqeq": true,
        "undef": true,
        "curly": true,
        "forin": true,
        "devel": true,
        "jquery": true,
        "browser": true,
        "wsh": true,
        "evil": true
    }
    
###CSSLinter校验CSS的options
    "csslint_options":
    {
        "adjoining-classes": "warning",
        "box-model": true,
        "box-sizing": "warning",
        "compatible-vendor-prefixes": "warning",
        "display-property-grouping": true,
        "duplicate-background-images": "warning",
        "duplicate-properties": true,
        "empty-rules": true,
        "errors": true,
        "fallback-colors": "warning",
        "floats": "warning",
        "font-faces": "warning",
        "font-sizes": "warning",
        "gradients": "warning",
        "ids": "warning",
        "import": "warning",
        "important": "warning",
        "known-properties": true,
        "outline-none": "warning",
        "overqualified-elements": "warning",
        "qualified-headings": "warning",
        "regex-selectors": "warning",
        "rules-count": "warning",
        "shorthand": "warning",
        "star-property-hack": "warning",
        "text-indent": "warning",
        "underscore-property-hack": "warning",
        "unique-headings": "warning",
        "universal-selector": "warning",
        "vendor-prefix": true,
        "zero-units": "warning"
    }
    
*[本文来自网络](http://www.cnblogs.com/lhb25/archive/2013/05/02/sublimelinter-for-js-css-coding.html)*