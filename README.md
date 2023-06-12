# db-tb-router
## 技术要点
springboot-starter初始化配置，AOP切面，哈希寻址，ThreadLocal，MyBatis拦截器，正则匹配
## 注解
### `1.@DBRouter(key)`
功能：分库，从动态数据库中确定数据源。  
位置：接口方法。  
参数：key字符串类型，自定义默认值，分库路由字段。  

### 2.`@DBRouterStrategy(splitTable)`
功能：分表，Mabatis拦截器捕获SQL执行分表。  
位置：Mapper映射接口  
参数：splitTable布尔类型，默认为false。

## 配置文件
>mini-db-router:
>>jdbc:
>>>datasource:
>>>>dbCount: 分库数n  
>>>>tbCount: 分表数2n  
>>>>default: 默认数据库  
>>>>routerKey: 默认路由字段  
>>>>list: 额外数据库  
>>>>db00: 数据库信息
>>>>>driver-class-name:  
>>>>>url:  
>>>>>username:  
>>>>>password:  

## 注意
本组件基于Mybatis插件对SQL的修改，因此litTable=True时，对应SQL语句不可加具体表。
