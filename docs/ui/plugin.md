---
layout: page
title: 插件
---

	插件，执行插件操作

- [数据采集](#数据采集)
- [时间校准](#时间校准)
- [RPC](#RPC)
- [设备间RPC](#设备间RPC)
- [电子邮箱](#电子邮箱)
- [REST](#REST)
	- [REST插件配置](#REST插件配置)
	- [REST调用规则](#REST调用规则)
	- [REST示例](#REST示例)
- [Kafka](#Kafka)
	- [Kafka插件配置](#Kafka插件配置)
	- [Kafka调用规则](#Kafka调用规则)
	- [Kafka示例](#Kafka示例)
- [RabbitMQ](#RabbitMQ)
	- [RabbitMQ插件配置](#RabbitMQ插件配置)
	- [RabbitMQ调用规则](#RabbitMQ调用规则)
	- [RabbitMQ示例](#RabbitMQ示例)

##
插件管理UI页显示系统和租户特定插件的表。每个插件有一个单独的卡。
你可以做以下操作：
-导入或创建新插件
-导出插件到JSON
-暂停并激活特定插件
-删除插件
见* *规则引擎*（/文件/用户指南/规则引擎）文档的更多细节。

![](http://help.gzhaibaogd.com/images/user-guide/ui/plugins.png)

！[图片]（/图片/用户指南/ UI /插件）
# #插件的细节
每个插件是一个单独的卡表示。您可以编辑插件配置，并在插件详细信息面板中查看插件事件。

![](http://help.gzhaibaogd.com/images/user-guide/ui/plugin-details.png)

！[图像]（/图片/用户指南/ UI /插件详细信息）
您还可以在邮件处理过程中查看插件生命周期事件、统计信息和错误。
请注意，在频繁的错误的情况下，错误消息进行采样。

![](http://help.gzhaibaogd.com/images/user-guide/ui/plugin-events.png)

！[图像]（/图片/用户指南/ UI /插件事件）
# #插件导入/导出
# # # #插件出口
你可以导出你的插件的JSON格式，导入到同一个或另一个thingsboard实例。
为了导出插件，你应该导航到**插件页面，点击位于特定插件卡上的导出按钮。

![](http://help.gzhaibaogd.com/images/user-guide/ui/plugin-export.png)

！[图片]（/图片/用户指南/ UI /插件导出）
# # # #插件导入
类似的，导入插件，你应该导航到**插件页面，然后点击屏幕右下角的大“+”按钮，然后点击“导入”按钮。

![](http://help.gzhaibaogd.com/images/user-guide/ui/plugin-import.png)

！[图像]（/图片/用户指南/ UI /插件导入）
**笔记*所有进口插件处于暂停状态。导入后不要忘记*激活你的插件。
# # # #故障排除
插件导入时可能出现的问题：
-相应的插件API令牌已*已* *。可以在源JSON中选择其他标记并直接编辑它。
-相应的插件实现**不在服务器的路径可用* *。


