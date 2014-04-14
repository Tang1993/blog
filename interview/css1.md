#CSS面试题2

##css隐藏一个元素
两种方法

1. { display: none; /* 不占据空间，无法点击 */ }
2. { visibility: hidden; /* 占据空间，无法点击 */ }
3. display:none; 完全隐藏这个元素，像不存在一样
4. { opacity: 0; filter:Alpha(opacity=0); /* 占据空间，可以点击 */ }
5. { position: absolute; opacity: 0; filter:Alpha(opacity=0); /* 不占据空间，可以点击 */ }

更多详细信息参考[可能不知道的CSS元素隐藏“失效”以其妙用](http://www.zhangxinxu.com/wordpress/2012/02/css-overflow-hidden-visibility-hidden-disabled-use/)