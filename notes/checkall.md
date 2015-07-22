	
	 // 选择对象
	 var chk_All = document.getElementById("chk_All")
	     , chk_Items = document.getElementsByName("chk_Item")
	     , hid_Items = document.getElementsByName("hid_Item");
	
	 /*全选checkbox注册click事件*/
	 chk_All.onclick = function (event) {
	     for (var i = 0, len = chk_Items.length; i < len; i++) {
	         chk_Items[i].checked = this.checked ? true : false;
	     }
	 };
	
	 /*数据行中所有checkbox注册click事件处理程序*/
	 chk_Items.onclick = function (event) {
	     if (!this.checked) {
	         chk_All.checked = false;
	     } else {
	         chk_All.checked = haveCheckedAll() ? true : false;
	     }
	 };
	
	 /*数据行中是否所有的checkbox都被勾选*/
	 function haveCheckedAll() {
	     for (var i = 0, len = chk_Items.length; i < len; i++) {
	         if (!chk_Items[i].checked) {
	             return false;
	         }
	     }
	     return true;
	 };