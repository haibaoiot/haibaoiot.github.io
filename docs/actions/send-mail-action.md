---
layout: docwithnav
assignees:
- ashvayka
title: 发送邮件操作

---

##简介
该组件允许通过将设备属性和消息数据替换为可配置模板来构建电子邮件消息。
##配置
在操作配置期间，您可以指定以下模板：from, to, cc, bcc, subject and body。
模板语法基于 [Velocity](https://velocity.apache.org/) ，并已在[报警处理器](/docs/reference/processors/alarm-deduplication-processor/#configuration)文档中描述。
另外，您可以指定发送标志属性。这是一个可选属性，可以与isNewAlarm组合使用或留空。
#查看
作为租户管理员，您可以查看Rules- > Demo Alarm Rule-> Actions-> Send Mail Action中的动作示例。

！![img](/images/action-sendmail.png)
