---
layout: docwithnav
assignees:
- ashvayka
title: Kafka插件动作

---
	Kafka是一种高吞吐量的分布式发布订阅消息系统，它可以处理消费者规模的网站中的所有动作流数据。
##简介

该组件允许通过将设备属性和消息数据替换为可配置模板来创建Kafka消息。
#配置

在操作配置期间，您可以指定以下内容：

- 设置标志以确认交货
- Kafka话题名称
- kafka body模板

Body Template语法基于Velocity ，已在报警处理器文档中描述。

