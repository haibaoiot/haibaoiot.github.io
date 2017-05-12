---
layout: docwithnav
assignees:
- ashvayka
title: REST API调用插件动作

---

##简介

该组件允许通过将设备属性和消息数据替换为可配置模板来创建POST / PUT正文请求。
##配置
在操作配置期间，您可以指定以下内容：

- 设置标志以确认交货
- http端点的操作路径
- 请求方法 - POST或PUT
- http响应中的预期结果代码
- 请求的主体模板Body 

Template语法基于 [Velocity](https://velocity.apache.org/)，并已在报警处理器文档中描述。