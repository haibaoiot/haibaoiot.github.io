---
layout: docwithnav
assignees:
- ashvayka
title: RPC插件

---

##简介
RPC插件主要负责：

- 提供REST API以将RPC请求从服务器端应用程序发送到设备;
- 通过可用的协议向设备发送RPC请求：[MQTT](/docs/reference/mqtt-api/#rpc-api)，[CoAP]()或[HTTP]()协议;
该插件由系统管理员在系统级进行配置。企业管理员可在自己的级别上配置自己的插件实例，并可自定义RPC插件功能.

##配置
可在插件配置中设置RPC的默认超时时间。

#服务端API
RPC插件API可参考[RPC](/docs/user-guide/rpc/#server-side-rpc-api)的相关资料。
##查看
可在“插件->RPC插件”中查看插件详细信息。

![img](/images/plugin-rpc.png)
