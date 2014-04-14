#Javascript 字符串面试题
###求一个字符串中出现次数最多的字符以及它出现的次数
方法1：

	var str = "adadfdfseffserfefsefseeffffftsdg"; 
	var maxLength = 0; 
	var result = ""; 
	while(str!=''){ 
		oldStr = str; 
		getStr = str.charAt(0);
		str = str.replace(new RegExp(getStr,"g"),"");
		if( oldStr.length-str.length > maxLength){
			maxLength = oldStr.length-str.length; 
			result = getStr + "=" + maxLength; 
		}
	}
	alert(result);
