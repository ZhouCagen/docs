<mark>✅ RAISERROR 的基本语法格式</mark>  
标准写法：
```
RAISERROR (message_text, severity, state);
```
``` 
参数	            作用  
message_text	错误消息（N'中文也可以'）  
severity	    错误严重级别（常用 16）  
state	        0~255 的号码，一般写 1 就行  
```

<mark>✅ 三个参数的详细解释</mark>

① message_text（错误消息内容） 

必须是 N'...'（N 表示支持 Unicode/中文）  
你可以写任何你想显示给用户的文本  

示例：
```
RAISERROR(N'年龄不合法', 16, 1);
```
② severity（错误严重级别）

必须掌握：  
```
级别	   描述	           用途
10	    消息，不算错误	 提示性信息
11~16	用户级错误	    我们最常用：16
17~19   系统级错误	    不建议自己用
20+	     致命错误	 会断开连接，千万别乱用
```


③ state（状态）

范围：0 ~ 255  
没啥特别含义，只是一个编号  
