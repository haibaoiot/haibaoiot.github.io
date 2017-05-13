---
layout: page
title: 执行器
---

- [遥测插件动作](#遥测插件动作)
- [发送邮件执行器](#发送邮件执行器)
- [REST API](#rest-api)
- [RPC PLUGIN](#rpc-plugin)
- [Kafka插件动作](#kafka插件动作)
- [RabbitMQ插件动作](#rabbitmq插件动作)

## 遥测插件动作

此组件允许将传入属性和时间序列请求转发到遥测插件。

该组件没有特定配置。

作为系统管理员，您可以查看“ 规则” - >“系统遥测规则” - >“操作” - >“遥测插件操作”中的操作示例。

![img](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/action-telemetry.png)

## 发送邮件执行器

该组件允许通过将设备属性和消息数据替换为可配置模板来构建电子邮件消息。

在操作配置期间，您可以指定以下模板：from, to, cc, bcc, subject and body。
模板语法基于 [Velocity](https://velocity.apache.org/) ，并已在[报警处理器]()文档中描述。
另外，您可以指定发送标志属性。这是一个可选属性，可以与isNewAlarm组合使用或留空。

作为租户管理员，您可以查看Rules- > Demo Alarm Rule-> Actions-> Send Mail Action中的动作示例。

！![img](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/action-sendmail.png)

## REST API

该组件允许通过将设备属性和消息数据替换为可配置模板来创建POST / PUT正文请求。

在操作配置期间，您可以指定以下内容：

- 设置标志以确认交货
- http端点的操作路径
- 请求方法 - POST或PUT
- http响应中的预期结果代码
- 请求的主体模板Body 

Template语法基于 [Velocity](https://velocity.apache.org/)，并已在报警处理器文档中描述。

## RPC PLUGIN
该组件允许将传入的rpc请求转发到各种插件。

该组件没有特定配置。


作为租户管理员，您可以在Rules-> Demo Time RPC Rule-> Actions-> RPC Plugin Action中查看操作示例。

![img](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/action-rpc.png)

## Kafka插件动作

---
	Kafka是一种高吞吐量的分布式发布订阅消息系统，它可以处理消费者规模的网站中的所有动作流数据。

该组件允许通过将设备属性和消息数据替换为可配置模板来创建Kafka消息。

在操作配置期间，您可以指定以下内容：

- 设置标志以确认交货
- Kafka话题名称
- kafka body模板

Body Template语法基于Velocity ，已在报警处理器文档中描述。

## RabbitMQ插件动作


该组件允许通过将设备属性和消息数据替换为可配置模板来创建RabbitMQ消息。


在操作配置期间，您可以指定以下内容：

- 设置标志以确认交货
- rabbitmq交换名称
- rabbitmq队列名称
- rabbitmq消息属性（BASIC，MINIMAL_BASIC，MINIMAL_PERSISTENT_BASIC，PERSISTENT_BASIC，PERSISTENT_TEXT_PLAIN，TEXT_PLAIN）
- rabbitmq消息体模板Body Template语法基于Velocity ，已在报警处理器文档中描述。
