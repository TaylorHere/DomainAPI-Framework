一个基于领域树形图的API框架

​	使用一个树形的描述语言描述具体业务

​	通过解析描述，自动生成大部分model，view等代码

​	每个树节点原则为一个暴露服务或暴露服务的集合

​	每个树节点描述了该节点的所有字段

​	每个树节点描述了该节点的检查

​	每个节点能映射为一个数据库model

​	任意一个树上节点能由顶节点开始遍历到，并以此为访问路由

​	描述语言代替了MVC中大部分VC端的工作

方案选择：

​	树形描述语言采用baidu团队开发的kitymind（km），其源文件为结构明确的json文件

方便遍历和查找。

​	工作流程：

​	文件合法性检查与km2python-object：

​		json检查

​		data数据(km中描述节点的key)的note-json检查

​		以上两步在km文件转化为python对象时同步完成

​	遍历节点，并记录遍历路径，遍历节点后，将该节点的note部分内容转换为api-python代码，使用遍历作为路由。

​	api-python部分技术选型：

​		使用SinglePage框架，SinglePage是我另一个开源项目，对RESTful风格的API建设支持良好。
		Django，Django是一个使用广泛且功能完善的Python Web框架

方案任务：

​	描述文件检查器

​		检查描述文件并转换为python对象
		17.6.30:
			对象遍历生成路由

​	解释器

​		遍历python对象并将各节点使用构造器构造

​	构造器

​		将参数构造成api-python模块



​	