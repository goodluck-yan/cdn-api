# cdn-api
python，实现调用阿里云cdn的api接口，实现自动刷新

刷新方法：
	1, 把accesskey+accesssecet放到aliyun.ini(前提准备：在阿里云的RAM中，增加一个子用户，并创建AccessKey)
	2，执行python cdn.py Action=RefreshObjectCaches ObjectType=File ObjectPath=http://yourdomain/1.txt
	3，其他接口都一样，看一下文档，传参数即可


程序使用环境：
    linux  + python2.7



后续加工修改：
	1.修改代码中的接口的版本，为阿里云的最新版本。
	Version=2018-05-10
	
	2.修改代码中的初始参数，TimeStamp中的大写S字母，为小些，应为新的接口用的小写s
	 'Timestamp'         : timestamp, \
	
	3.修改代码中的ObjectPath传参，支持多个url刷新功能，将传入的字符串\n,转换成实际的换行符。
	parameters[key] = user_params[key].replace(r'\n','\n')
	
	4.增加自动请求api接口，刷新cdn的功能。


示例：
	支持多文件刷新，用\n分割
	python cdn.py Action=RefreshObjectCaches ObjectType=File 'ObjectPath=https://wywl.0256.cn/h5/parkmall/index.html\nhttps://wywl.0256.cn/h5/petroleumCard/html/chai.html'
	
	支持目录刷新
	python cdn.py Action=RefreshObjectCaches ObjectType=Directory 'ObjectPath=https://wywl.0256.cn/h5/parkmall/\nhttps://wywl.0256.cn/h5/petroleumCard/'




