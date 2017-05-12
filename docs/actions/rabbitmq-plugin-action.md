---
layout: docwithnav
assignees:
- ashvayka
title: RabbitMQ插件动作

---

##简介
该组件允许通过将设备属性和消息数据替换为可配置模板来创建RabbitMQ消息。

#配置

在操作配置期间，您可以指定以下内容：

- 设置标志以确认交货
- rabbitmq交换名称
- rabbitmq队列名称
- rabbitmq消息属性（BASIC，MINIMAL_BASIC，MINIMAL_PERSISTENT_BASIC，PERSISTENT_BASIC，PERSISTENT_TEXT_PLAIN，TEXT_PLAIN）
- rabbitmq消息体模板Body Template语法基于Velocity ，已在报警处理器文档中描述。
