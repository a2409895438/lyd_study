# 1.MQ的概念

MQ全称为Message Queue, 是在消息传输过程中保存消息的容器。多用于分布式系统之间进行通信。

![image-20220614193830727](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20220614193830727.png)

# 2.MQ的优势和劣势

## 2.1 MQ的优势

- 应用解耦

系统的耦合性越高，容错率就越低，可维护性也越低

使用MQ可以使得应用间解耦

- 异步提速

![image-20220614194518562](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20220614194518562.png)

提升用户体验和系统吞吐量

- 削峰填谷

![image-20220614194819738](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20220614194819738.png)

可以提高系统的稳定性

## 2.2 MQ的劣势

- 系统的可用性降低

系统引入的外部依赖越多，系统的稳定性就会降低。如何保证MQ的高可用

- 系统的复杂度提高

MQ的加入大大增加了系统的复杂度，以前系统间是同步的远程调用，现在是通过MQ进行异步调用。如何保证消息没有被重复消费？怎么处理消息丢失的情况和消息传递的顺序性。

- 一致性的问题

B、C系统处理成功，D系统失败，如何保证消息数据处理的一致性？

## 2.3 使用MQ需要满足的条件

1. 生产者不需要从消费者处获得反馈。引入消息队列之前的直接调用，其接口的返回值应该为空，这才让明明下层的动作还没有做，上层却当做动作做完后继续往后走，即所谓异步成了可能。
2. 容许短暂的不一致性。
3. 确实是用了有效果。即解耦、提速、削峰方面的收益超过加入MQ和管理MQ的成本。

# 3.常见的MQ产品

![image-20220614195850008](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20220614195850008.png)

## 3.1 RabbitMQ简介

AMQP即Advanced Message Queuing Protocol(高级消息队列协议)，是一个网络协议，是应用层协议的一个开放标准，为面向消息的中间件设计。基于此协议的客户端与消息中间件可传递消息，并不受客户端/中间件不同产品，不同开发语言等条件的限制。2006年，AMQP规范发布，类比HTTP。

![image-20220614200549315](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20220614200549315.png)

RabbitMQ基础架构

![image-20220614200731874](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20220614200731874.png)

## 3.2 RabbitMQ的6中工作模式：

- 简单模式
- work queues
- publish/subscribe
- Routing
- Topics
- RPC

## 3.3 JMS（API的规范接口）

即Java消息服务的应用程序接口，是一个Java平台中关于面向消息中间件的API

JMS是JavaEE规范的一种，类比JDBC

很多消息中间件都实现了JMS规范，如ActiveMQ。RabbitMQ官方没有提供JMS的实现包，但是开源社区有

