## com.cdyfsz.svc.xxx.context：

      1. DDD中对应界限上下文，如果微服务根据界限上下文拆分，那么没有这一层。项目名为context
      2. 两个context调用，调用端在application发起，只能调用interfaces层接口。

## interfaces：

      1. 对应用户UI接口层，与接口文档1对1匹配。接口命名来自于接口文档。
      2. 提供内部微服务调用接口
      3. 约束校验（空值，正则）
      4. 参数：dto
      5. 返回值：vo
      6. message: mq消息接收

## application:

       1. 协调多个聚合的服务和领域对象完成服务编排和组合，协作完成业务操作。
       2. 事务，日志，约束。
       3. 服务间调用在这一层发起。
       4. 复杂的服务编排放在orchestration里面（超过3次微服务调用）。具体业务逻辑必须下沉到领域层。

## domain:（项目核心）

        1. aggregation: 映射DDD中的聚合。命名方式来自于DDD设计
        2. entity: 实体。命名方式来自于DDD设计英文名
        3. valueobject：值对象。命名方式来自于DDD设计英文名
        4. factory： 复杂实体或值对象，通过工厂创建。命名方式 实体名/值对象+Factory
        5. service： 聚合、实体、值对象采用贫血模式，核心业务放在服务内。这个服务映射到DDD中的执行命令。
        6. repository: 仓库接口，

## infrastructure：
        1. db 数据库实现，complexquery 跨context查询
        2. message 消息中间件
        3. file 文件
        4. cache 缓存
        5. config 配置管理
        6. common 通用
