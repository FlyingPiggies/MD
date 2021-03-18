# Message Queue

分布式系统中重要组件，使用较多的有**RabbitMQ**、**Kafaka**， 部分数据库如**Redis**，**MySql**也可实现消息队列。

线上的消息队列服务：

**Azure Service Bus Queue**       
**Aws SQS**

## 使用场景

***

1. 应用解耦

2. 异步处理

3. 限流削峰

## 消息模型

***

1. Point to Point 
    
    - 点对点的消费模式，不可重复消费。

2. Publish/Subscribe
    
    - 发布/订阅的消费模式，可重复消费。

## 工作模式

***

RabbitMQ有三种工作模式：单机模式，普通集群模式，镜像集群模式。

- 单机模式  
	不能保证高可用

- 普通集群模式
	只是通过集群部署的方式提高了消息的吞吐量，没有实现消息队列的高可用。

- 镜像集群模式
	需要在后台新增镜像集群模式策略，要求把queue中的元数据和消息同步到所有其他RabbitMQ的节点。当进行消息消费时，连接其他服务器的节点一样也能获取到数据。

## Questions

***

- RabbitMQ如何保证高可用的？
- RabbitMQ如何保证高吞吐的？
- RabbitMQ的消息是有序的吗？
- RabbitMQ的消息局部顺序是如何保证的?
- RabbitMQ事务消息的实现机制？
- RabbitMQ会有重复消费的问题吗？如何解决？
- RabbitMQ支持什么级别的延迟消息？如何实现的？
- RabbitMQ是推模型还是拉模型？
- Consumer的负载均衡是怎么样的？
