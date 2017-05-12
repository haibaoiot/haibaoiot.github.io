---
layout: docwithnav
assignees:
- ashvayka
title: 数据采集插件

---
##简介
该插件主要负责

- 连续持久的最新传输过来的数据的属性更新；
- 连续持久的最新传输过来的数据到内部数据存储;
- 提供服务器端API查询和订阅数据更新。

该插件功能对于仪表板中的数据可视化至关重要，因此一般由系统管理员在系统级别进行配置。企业管理员也可以自定义自己的数据收集插件。

![img](/images/plugin-telemetry.png)

##服务端API

数据采集插件API可参考设备的[属性](/docs/user-guide/attributes/) 和[数据](/docs/user-guide/telemetry/) 指导。 
