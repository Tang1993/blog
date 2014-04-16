# Javascript 数组面试题
##数组去重
我们的直觉是这样写

	function unique(arr) {
	  var ret = []
	 
	  for (var i = 0; i < arr.length; i++) {
	    var item = arr[i]
	    if (ret.indexOf(item) === -1) {
	      ret.push(item)
	    }
	  }
	 
	  return ret
	}

直觉往往很靠谱，在现代浏览器下，上面这个函数很正确，性能也不错。但前端最大的悲哀也是挑战之处在于，要支持各种运行环境。在 IE6-8 下，数组的 indexOf 方法还不存在。直觉方案要稍微改造一下：

	var indexOf = [].indexOf ?
	    function(arr, item) {
	      return arr.indexOf(item)
	    } :
	    function indexOf(arr, item) {
	      for (var i = 0; i < arr.length; i++) {
	        if (arr[i] === item) {
	          return i
	        }
	      }
	      return -1
	    }
	 
	function unique(arr) {
	  var ret = []
	 
	  for (var i = 0; i < arr.length; i++) {
	    var item = arr[i]
	    if (indexOf(ret, item) === -1) {
	      ret.push(item)
	    }
	  }
	 
	  return ret
	}

写到这一步，正确性已没问题，但性能上，两重循环会让面试官们看了不爽.
看一下优化的方案

	function unique(arr) {
	  var ret = []
	  var hash = {}
	 
	  for (var i = 0; i < arr.length; i++) {
	    var item = arr[i]
	    var key = typeof(item) + item
	    if (hash[key] !== 1) {
	      ret.push(item)
	      hash[key] = 1
	    }
	  }
	 
	  return ret
	}

核心是构建了一个 hash 对象来替代 indexOf. 注意在 JavaScript 里，对象的键值只能是字符串，因此需要var key = typeof(item) + item 来区分数值 1 和字符串 '1' 等情况。

但优化真的很容易带来坑，比如上面的实现，对下面这种输入就无法判断：

	unique([ new String(1), new Number(1) ])
可以继续修改代码，做到性能和正确性都很好。但往往，这带来的结果并不好。

