---
layout: page
title: 属性
---

thingsboard提供指定自定义属性，您的设备和管理能力。属性被处理键值对。灵活和简单的关键值格式允许轻松和无缝集成与几乎任何物联网设备在市场上。

所有属性可用于规则引擎组件：过滤器、处理器和操作。本指南提供了上面列出的功能的概述和一些有用的链接，以获得更多的细节。

属性分为三个主要组：
客户端属性通过设备应用程序进行报告和管理。例如：目前的软件/固件版本，硬件规格等

![](/images/client-side-attributes.svg)

服务器端属性由服务器端应用程序进行报告和管理。设备应用程序不可见。一些秘密的数据，可以通过thingsboard规则但不应提供给装置。

![](/images/server-side-attributes.svg)

共享属性由服务器端应用程序进行报告和管理。可见设备应用程序。例如：客户订阅计划，目标软件/固件版本。

![](/images/shared-attributes.svg)

设备属性的API
thingsboard提供以下API的设备应用程序：
将客户端属性上载到服务器
请求来自服务器的客户端和共享属性。
订阅共享属性的更新。
属性API是特定于每个支持的网络协议。您可以在相应的参考页中查看API和示例：
MQTT API参考
COAP API参考
HTTP API参考
遥测插件
thingsboard包括核心服务和可插拔模块插件。遥测插件负责将属性数据保存到内部数据存储；提供服务器端API来查询和订阅属性更新。由于遥测插件功能在仪表板的数据可视化的目的的关键，它是由系统管理员配置系统级。高级用户或平台开发人员可以定制遥测插件功能。
内部数据存储
thingsboard使用Cassandra NoSQL数据库。这个数据库是用于时间序列数据存储优化。卡桑德拉负责数据的复制和提供可扩展、可靠和容错存储。
属性存储在attributes_kv_cf列族。
虽然你可以直接查询数据库，thingsboard提供平安和WebSocket API，简化了这一过程，并运用一定的安全政策：
租户管理员用户能够管理属于相应的承租人所有未分配的设备属性。
客户用户只能对分配给相应客户的设备进行属性管理。
数据查询API
遥测插件提供以下API来获取设备属性：
属性键的API
您可以使用以下URL获取请求获取特定设备ID的所有属性键的列表
	http(s)://host:port/api/plugins/telemetry/{deviceId}/keys/attributes
Attribute values API

You can fetch list of latest values for particular device id using GET request to the following URL
	http(s)://host:port/api/plugins/telemetry/{deviceId}/values/attributes?keys=key1,key2,key3

Data visualization

Thingsboard provide ability to configure and customize dashboards for data visualization. This topic is covered in separate guide.

Rule engine

Thingsboard provide ability to configure data processing rules. Device attributes can be used inside rule filters. This allows to apply rules based on certain device properties. You can find more details in a separate guide.