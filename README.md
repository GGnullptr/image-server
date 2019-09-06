# image-server
实现一个HTTP服务器用来存储图片，实现以下功能：
     ○ 上传图片（得到一个url）
     ○ 根据图片的url访问图片 获取图片内容
     ○ 获取图片属性
     ○ 删除图片

#分为两个模块：
     ##数据存储模块
	• 使用数据库存储图片信息
	• 图片内容存储在磁盘上
     
     ##服务器模块
	• API具体设计
	1. 上传图片
	请求
		POST /image HTTP/1.1
		Content-Type:application/x-www-form-urlencoded----------提交表单 
		[内容]
	响应
		HTTP/1.1 200 OK
		(
			ok:true
		)
	2. 查看所有图片信息
	请求
		GET /image
	响应
		HTTP/1.1 200 ok
		[
			{
				"image_id":1,
				"image_name":"test.png,
				"type":"image/png",
				"md5":"abcdef",
				……
			}
			……
		]
	3. 查看指定图片
	请求
		GET /imgae/156151
	响应
	HTTP 200 OK
	{
		"image_id":1,
		"image_name":"test.png,
		"type":"image/png",
		"md5":"abcdef",
		……
	}
	4. 查看指定图片内容
	请求
		GET /show/:image_id
	响应
		HTTP/1.1 200 OK
		Content-type:image/png
		[body 图片内容数据]
	5. 删除图片
	请求
		DELETE /image/:image_id
	响应
	HTTP/1.1 200 OK
	(
		ok:true
	)



