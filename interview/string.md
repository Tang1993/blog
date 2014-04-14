#Javascript 字符串面试题

##得到字符串中出现次数最多的字母
方法一

var str ="adadfdfseffserfefsefseeffffftsdg"; 
var maxLength = 0; 
var result = ""; 

	while( str != '' ){ 
	        oldStr = str; 
	        //也可以用charAt
	        getStr = str.substr(0,1); 
	        str = str.replace(new RegExp(getStr,"g"),"")  
	
	        if( oldStr.length-str.length > maxLength ) { 
	                maxLength = oldStr.length-str.length; 
	                result = getStr + "=" + maxLength 
	        }
	}  
	alert(result) //弹出结果  

方法二

	var str = 'asdfssaaasasasasaa';
	//用于保存结果
	var json = {};
	for (var i = 0; i < str.length; i++) {
	        if(!json[str.charAt(i)]){
	                json[str.charAt(i)] = 1;
	        }else{
	                json[str.charAt(i)]++;
	        }
	};
	var iMax = 0;
	var iIndex = '';
	for(var i in json){
	        if(json[i]>iMax){
	                iMax = json[i];
	                iIndex = i;
	        }
	}

##求一个字符串的字节长度，中文算两个

	var str = '22两是';
	
	alert(getStrlen(str))
	
	function getStrlen(str){
	        var json = {len:0};
	        var re = /[\u4e00-\u9fa5]/;
	        for (var i = 0; i < str.length; i++) {
	                if(re.test(str.charAt(i))){
	                        json['len']++;
	                }
	        };
	        return json['len']+str.length;

