---
layout: page
title: 遥测数据
---

thingsboard提供丰富的遥测数据相关的特征：
从设备使用MQTT采集数据、协议或HTTP协议。
存储时间序列数据的卡桑德拉（高效、可扩展性和容错的NoSQL数据库）。
查询最新的时间序列数据值或在指定的时间间隔内的所有数据。
订阅使用WebSocket数据更新（可视化、实时分析）。
将时间序列数据的使用配置和高度可定制的部件和仪表盘。
使用灵活的规则引擎（文档/用户指南/规则引擎）过滤和分析数据。
根据收集的数据生成警报。
数据转发到外部系统使用插件（如卡夫卡或RabbitMQ插件）。
本指南提供了上面列出的功能的概述和一些有用的链接，以获得更多的细节。

![](/images/telemetry.svg)

设备遥测上载API
thingsboard提供API上传时间序列的关键值数据。灵活和简单的关键值格式允许轻松和无缝集成与几乎任何物联网设备在市场上。遥测上载API是特定的每个支持的网络协议。您可以在相应的参考页中查看API和示例：
MQTT API参考
COAP API参考
HTTP API参考
遥测插件
thingsboard包括核心服务和可插拔模块插件。遥测插件负责持续的时间序列数据的内部数据存储；提供服务器端API查询和订阅数据的更新。由于遥测插件功能在仪表板的数据可视化的目的的关键，它是由系统管理员配置系统级。高级用户或平台开发人员可以定制遥测插件功能。
内部数据存储
thingsboard使用Cassandra NoSQL数据库。这个数据库是用于时间序列数据存储优化。卡桑德拉负责数据的复制和提供可扩展、可靠和容错存储。
设备，发送数据到服务器接收数据传送确认当数据存储在卡桑德拉。现代MQTT客户允许未提交数据的临时本地存储。因此，即使一个节点的thingsboard下山，设备不会丢失数据，可以把它推到其他服务器。
数据存储到多个列族中：
ts_kv_cf原数据通过设备ID分区和分区，数据的关键
ts_kv_partitions_cf -分区存储列表为每个设备的ID和数据的关键，允许对数据的高效查询的执行。
ts_kv_latest_cf店新值的快速访问。
虽然你可以直接查询数据库，thingsboard提供平安和WebSocket API，简化了这一过程，并运用一定的安全政策：
租户管理员用户可以对属于相应的租户全部未分配设备获取数据。
客户用户只能为分配给相应客户的设备获取数据。
数据查询API
遥测插件提供以下API来获取设备数据：
时间序列数据键的API
您可以使用以下URL获取请求获取特定设备ID的所有数据键的列表

	http(s)://host:port/api/plugins/telemetry/{deviceId}/keys/timeseries

Timeseries data values API

You can fetch list of latest values for particular device id using GET request to the following URL
	http(s)://host:port/api/plugins/telemetry/{deviceId}/values/timeseries?keys=key1,key2,key3

You can also fetch list of historical values for particular device id using GET request to the following URL
	http(s)://host:port/api/plugins/telemetry/{deviceId}/values/timeseries?keys=key1,key2,key3&startTs=1479735870785&endTs=1479735871858&interval=60000&limit=100&agg=AVG
The supported parameters are described below:
keys - comma separated list of telemetry keys to fetch.
startTs - unix timestamp that identifies start of the interval in milliseconds.
endTs - unix timestamp that identifies end of the interval in milliseconds.
interval - the aggregation interval, in milliseconds.
agg - the aggregation function. One of MIN, MAX, AVG, SUM, COUNT, NONE.
limit - the max amount of data points to return or intervals to process.
Thingsboard will use startTs, endTs and interval to identify aggregation partitions or sub-queries and execute asynchronous queries to Cassandra that levarage built-in aggregation functions.
get-telemetry-values.sh

Websocket API

Websockets are actively used by Thingsobard Web UI. Websocket API duplicates REST API functionality and provides ability to subscribe to device data changes. You can open a websocket connection to a telemetry plugin using following URL
	ws(s)://host:port/api/ws/plugins/telemetry?token=$JWT_TOKEN
Once opened, you can send subscription commands and receive subscription updates:
where
cmdId - unique command id (within corresponding websocket connection)
deviceId - unique device identifier
keys - comma separated list of data keys
timeWindow - fetch interval for timeseries subscriptions, in milliseconds. Data will be fetch within following interval [now()-timeWindow, now()]
startTs - start time of fetch interval for historical data query, in milliseconds.
endTs - end time of fetch interval for historical data query, in milliseconds.
Complete example is coming soon!
Data visualization

Thingsboard provide ability to configure and customize dashboards for data visualization. This topic is covered in separate guide.

Rule engine

Thingsboard provide ability to configure data processing rules. Each rule consists of
filters - to filter incoming data feed,
processor - to generate alarms or enrich incoming data with some server-side values
action - to apply certain logic to filtered data. You can find more details in a separate guide.