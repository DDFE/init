###input事件不连续执行某操作

*背景：输入联想的时候每次输入都会发送ajax请求，这个地方主要是控制请求的*

	<!doctype html>
	<html lang="en">
	<head>
	<meta charset="UTF-8">
	<title>持续发送Ajax请求怎么节约请求</title>
	</head>
	<body>
	<input type="text" id="txt_test"></input>
	<script type="text/javascript">
	window.addEventListener("DOMContentLoaded",function(ev){
		var txt = document.getElementById("txt_test");
		var count = 0, stack = [], timeout = 0;
	
		/**
		 * [description]
		 * @param  {[type]} ev [description]
		 * @return {[type]}    [description]
		 */
		txt_test.addEventListener("input",function(ev){
			count++;
			stack.push(ev.target.value);
			console.log("数组为："+stack.join(",") +" count: "+ count+ " length: "+ stack.length);
			if(count === stack.length){
				timeout = setTimeout(function(){
					if(stack[stack.length-1]){
						console.log("ajax request: "+stack[stack.length-1]);
					}
					count = 0;
					stack = [];
				},600);
			}else{
				clearTimeout(timeout);
			}
	
		},false);
	
		/**
		* 不能监听到组合键、clipData发生的改变
		* @param  {[type]} ev [description]
		* @return {[type]}    [description]
		*/
		// txt_test.addEventListener("keyup",function(ev){
			// 	console.log("sdsd");
		// },false);
	
	},false);
	</script>
	</body>
	</html>