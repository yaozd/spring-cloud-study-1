> 验证地址
1. 服务器端：
    - [http://localhost:12000/config-client,config/dev](http://localhost:12000/config-client,config/dev)
2. 客户端：
    - [http://localhost:13000/info](http://localhost:13000/info)
    - [http://localhost:13000/yzdinfo](http://localhost:13000/yzdinfo)


> 参考推荐
- [SpringCloud Config Server和Client的配置使用](https://blog.csdn.net/liqi_q/article/details/81158002)
- [Spring Cloud Config（配置中心）](https://www.cnblogs.com/boboooo/p/8796636.html)
- [基于Spring Cloud的微服务架构演变史-文章中的config部分](https://mp.weixin.qq.com/s/4roticzIrT68Fv-yoEeICg)

> 匹配规则
```
模式匹配和多仓库:
在{application}和{profile}参数中使用模式匹配可以支持更多复杂的需求。模式的格式是一组逗号分隔的{application}/{profile}，其中的参数可以使用通配符。例如：
如果{application}/{profile}没有匹配到任何模式，它将使用默认的仓库地址:spring.cloud.config.server.git.uri。上面的例子中，"simple"仓库匹配的是“simple/*”（它仅仅匹配一个仓库simple，在所有的环境下）。"local"仓库将匹配所有{application}的名字以“local”开头的，并且也是在所有的环境下。“/*”前缀自动添加到所有没有设置{profile}的模式中。
```

> "灰度"更新配置-(但使场景很少一般用不到)
```
从配置变化的通知机制上看，如果有100个应用节点，都依赖于统一配置，如果修改了配置，只想让某几个节点"灰度"更新配置，
spring cloud config server更容易做到，这一点相对disconf更灵活（后面会详细讲解
参考：

```

> 当git上面的配置发生更新后，需要在服务器端进行查看验证，如：
```
http://localhost:12000/config-client,config/dev
---
config-client,config 代表配置文件的名称
```
