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


## 数据采集

该插件主要负责

- 连续持久的最新传输过来的数据的属性更新；
- 连续持久的最新传输过来的数据到内部数据存储;
- 提供服务器端API查询和订阅数据更新。

该插件功能对于仪表板中的数据可视化至关重要，因此一般由系统管理员在系统级别进行配置。企业管理员也可以自定义自己的数据收集插件。

![img](/images/plugin-telemetry.png)

 
## 时间校准
校时插件，主要负责处理设备的“getTime”请求，它表明设备可以通过各种连接协议发送RPC请求，以执行服务器端逻辑并获取结果。

您可以指定**时间格式**配置参数。

作为租户管理员，您可以查看插件 - >校时插件中的插件示例。

![img](/images/plugin-gettime.png)

## RPC

RPC插件主要负责：

- 提供REST API以将RPC请求从服务器端应用程序发送到设备;
- 通过可用的协议向设备发送RPC请求：[MQTT]()，[CoAP]()或[HTTP]()协议;
该插件由系统管理员在系统级进行配置。企业管理员可在自己的级别上配置自己的插件实例，并可自定义RPC插件功能.


可在插件配置中设置RPC的默认超时时间。


RPC插件API可参考[RPC]()的相关资料。

可在“插件->RPC插件”中查看插件详细信息。

![img](/images/plugin-rpc.png)

##　设备间RPC

该RPC插件可通过服务器实现各种物联网设备之间的通信。因此设备只有在属于同一个客户时才能交换消息。插件实现可以定制，以涵盖更复杂的安全功能。


配置界面，您可以指定以下配置参数：

- 每个客户的最大设备数量
- 默认请求超时
- 最大请求超时


设备RPC API有两个：*getDevices*和*sendMsg*。下面以MQTT为例进行说明，CoAP和HTTP可参照执行。

#####获取设备列表API
为了向其他设备发送消息，您需要使用设备标识符。设备可以使用*getDevices* RPC调用来请求属于同一客户的其他设备的列表。
执行命令如下：

	{% capture tabspec %}mqtt-get-device-list
	A,mqtt-get-device-list.sh,shell,resources/mqtt-get-device-list.sh,/docs/reference/plugins/resources/mqtt-get-device-list.sh
	B,mqtt-get-device-list.js,javascript,resources/mqtt-get-device-list.js,/docs/reference/plugins/resources/mqtt-get-device-list.js
	C,response.json,javascript,resources/mqtt-get-device-list.json,/docs/reference/plugins/resources/mqtt-get-device-list.json{% endcapture %}

#####发送消息 API

设备可以使用sendMsg RPC调用向同一客户的其他设备发送消息。
下面的示例将尝试从设备“Test Device A1”发送消息到设备“Test Device A2”。
执行命令如下：

	{% capture tabspec %}mqtt-send-msg-fail
	A,mqtt-send-msg.sh,shell,resources/mqtt-send-msg.sh,/docs/reference/plugins/resources/mqtt-send-msg.sh
	B,mqtt-send-msg.js,javascript,resources/mqtt-send-msg.js,/docs/reference/plugins/resources/mqtt-send-msg.js{% endcapture %}

可能接收到如下消息：

```json
{"error":"No active connection to remote device!"}
```

让我们启动目标设备A2的仿真器，并再次发送消息

	{% capture tabspec %}mqtt-receive-msg
	A,mqtt-receive-msg.sh,shell,resources/mqtt-receive-msg.sh,/docs/reference/plugins/resources/mqtt-receive-msg.sh
	B,mqtt-receive-msg.js,javascript,resources/mqtt-receive-msg.js,/docs/reference/plugins/resources/mqtt-receive-msg.js{% endcapture %}

因此，您应该从设备收到以下响应：

```json
{"status":"ok"}
```
请注意，目标设备ID，访问令牌，请求和响应实体将被硬编码为脚本并对应于演示设备。
可在“插件->设备RPC消息插件”中查看插件详细信息。

![img](/images/plugin-rpcmessage.png)

##　电子邮箱

邮件插件负责发送由相应的规则操作触发的电子邮件。

您可以指定以下参数：

- 邮件服务器主机
- 邮件服务器端口
- 用户名和密码
- 其他的邮箱配置信息。

您可能需要更新用户名和密码以匹配账户并开始接收电子邮件。
可在“插件->邮箱插件”中查看插件详细信息。

![img](/images/plugin-mail.png)

此插件不提供任何服务器端API。

##　REST

Rest API插件负责将HTTP请求发送到由特定规则触发的特定端点
您可以指定以下配置参数：

- http端点服务器主机
- http端点服务器端口
- http请求的基本路径
- http认证方式。目前没有授权或基本支持
- 用户名，如果是基本的验证方法
- 基本auth方法的密码

在本例中，我们将演示如何配置Rest API Call扩展，以便每当设备的新的遥测消息到达时，能够将POST或PUT请求发送到特定的REST端点。

继续之前的先决条件REST API呼叫扩展配置：

- 事件板已启动并运行
- 能够接收POST或PUT请求的第三方HTTP服务器和特定端点启动并运行
#####REST插件配置

我们首先配置REST API Call plugin。转到插件菜单，点击'+'按钮并创建新的插件：

![image](/images/rest-api-call/rest-api-call-plugin-config-1.png)

![image](/images/rest-api-call/rest-api-call-plugin-config-2.png)

请为要转移请求的REST端点设置正确的URL，端口，路径和身份验证方法。保存插件并点击“激活”插件按钮：

![image](/images/rest-api-call/rest-api-call-activate-plugin.png)

#####REST调用规则

现在是时候创建适当的规则了。

![image](/images/rest-api-call/rest-api-call-rule-config.png)

添加POST_TELEMETRY消息类型的过滤器

![image](/images/rest-api-call/post-telemetry-filter.png)

点击“添加”按钮添加过滤器。
然后在插件字段的下拉框中选择“REST API调用插件”：

![image](/images/rest-api-call/rest-api-call-plugin-selection.png)

Add action that will send temperature telemetry of device to particular REST action-path. In the action you can provide request type and result code that you expected from the REST endpoint in case of successful call.

![image](/images/rest-api-call/rest-api-call-rule-action-config-1.png)

![image](/images/rest-api-call/rest-api-call-rule-action-config-2.png)

Click ‘Add’ button and then activate Rule.
#####REST示例

Now for any of your devices send Telemetry message that contains ‘temp’ telemetry:
```json
{"temp":73.4}
```

You should see ‘73.4’ as a body request in appropriate rest endpoint once you’ll post this message.
Here is an example of a command that publish single telemetry message to locally installed Thingsboard:
mosquitto_pub -d -h "localhost" -p 1883 -t "v1/devices/me/telemetry" -u "$ACCESS_TOKEN" -m '{"temp":73.4}'

```bash
mosquitto_pub -d -h "localhost" -p 1883 -t "v1/devices/me/telemetry" -u "$ACCESS_TOKEN" -m '{"temp":73.4}'
```

## Kafka

Kafka插件负责向特定规则触发的Kafka经纪人发送消息

卡夫卡的配置参数如下：

- 引导服务器 – 卡夫卡经纪人列表
- 如果连接失败，尝试重新连接到卡夫卡的次数
- 在客户端上单元批量的消息数
- 发送到卡夫卡经纪人之前在本地进行缓冲的时间（以ms为单位）
- 客户端缓冲区最大大小
- 必须承认写入的最小副本数
- 主题键序列化程序默认情况下 - org.apache.kafka.common.serialization.StringSerializer
- 主题值序列化程序默认情况下 - org.apache.kafka.common.serialization.StringSerializer
- 可以为kafka代理连接提供任何其他附加属性


无相关配置

在这个例子中，我们将演示如何配置此扩展，以便每当设备的新遥测消息到达时，能够向Kafka主题发送消息。
继续前提条件Kafka扩展配置：

- 卡夫卡经纪人正在运行
- 创建适当的Kafka主题
- 事件板已启动并运行

#####Kafka插件配置

我们首先配置Kafka插件。转到插件菜单并创建新的插件：

![image](/images/kafka/kafka-plugin-config-1.png)

![image](/images/kafka/kafka-plugin-config-2.png)

请设置正确的Kafka Bootstrap服务器URL和插件配置部分中适用于您的案例的任何其他参数，以便Kafka扩展能够连接到Kafka代理。

点击*“Active”*插件按钮：

![image](/images/kafka/kafka-activate-plugin.png)

#####kafkad调用规则

现在是时候创建适当的规则了。

![image](/images/kafka/kafka-rule-config.png)

添加POST_TELEMETRY消息类型的过滤器

![image](/images/kafka/post-telemetry-filter.png)

点击*“ADD”*按钮添加过滤器。
然后在*“PLUGIN”*字段的下拉框中选择*“Kafka Plugin”*：

![image](/images/kafka/kafka-plugin-selection.png)

添加将设备温度遥测的特定卡夫卡主题的操作：

![image](/images/kafka/send-temp-telemetry.png)

点击*“ADD”*按钮，然后激活规则。
#####Kafka示例

现在，您的任何设备发送包含*“temp”*遥测的遥测信息：
{"temp":73.4}

一旦您发布此消息，您应该在适当的Kafka主题中看到**'73.4'**消息。

以下是一个将单个遥测消息发布到本地安装的事件板的命令示例：

```bash
mosquitto_pub -d -h "localhost" -p 1883 -t "v1/devices/me/telemetry" -u "$ACCESS_TOKEN" -m '{"temp":73.4}'
```

## RabbitMQ

RabbitMQ插件负责将消息发送到由特定规则触发的RabbitMQ实例



您可以指定以下配置参数：

- rabbitmq实例主机
- rabbitmq实例端口
- rabbitmq虚拟主机
- 授权用户名
- 授权密码
- 在发生故障时启用自动化连接重新发送
- 连接超时
- 握手超时
- 可用于连接到特定的rabbitmq实例的其他客户端属性

在本例中，我们将演示如何配置RabbitMQ扩展，以便每当设备的新遥测消息到达时，能够将消息发送到特定队列。
继续前提RabbitMQ扩展配置：

- 事件板已启动并运行
- RabbitMQ实例已启动并运行
#####RabbitMQ插件配置

我们首先配置RabbitMQ插件。转到插件菜单，点击'+'按钮并创建新的插件：
![image](/images/rabbitmq/rabbitmq-plugin-config-1.png)

![image](/images/rabbitmq/rabbitmq-plugin-config-2.png)
请设置正确的主机，端口和凭据，以便扩展能够连接到RabbitMQ代理。
保存插件并点击“激活”插件按钮：

![image](/images/rabbitmq/rabbitmq-activate-plugin.png)

#####RabbitMQ调用规则

现在是时候创建适当的规则了。

![image](/images/rabbitmq/rabbitmq-rule-config.png)

添加POST_TELEMETRY消息类型的过滤器

![image](/images/rabbitmq/post-telemetry-filter.png)

点击“添加”按钮添加过滤器。
然后在插件字段的下拉框中选择“RabbitMQ插件”：

![image](/images/rabbitmq/rabbitmq-plugin-selection.png)

添加将特定RabbitMQ队列发送设备温度遥测的操作：

![image](/images/rabbitmq/rabbitmq-rule-action-config.png)

点击“添加”按钮，然后激活规则。
#####RabbitMQ示例

现在，您的任何设备发送包含“temp”遥测的遥测信息：

```json
{"temp":73.4}
```
一旦您发布此消息，您应该在适当的RabbitMQ队列中收到消息'73 .4'。
以下是一个将单个遥测消息发布到本地安装的事件板的命令示例：
```bash
mosquitto_pub -d -h "localhost" -p 1883 -t "v1/devices/me/telemetry" -u "$ACCESS_TOKEN" -m '{"temp":73.4}'
```

