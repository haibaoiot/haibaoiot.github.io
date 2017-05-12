---
layout: page
title: 过滤器
---

	过滤器执行过滤操作

- [设备属性过滤器](#设备属性过滤器)
- [设备数据过滤器](#设备数据过滤器)
- [消息类型过滤器](#消息类型过滤器)
- [方法名称过滤器](#方法名称过滤器)

## 设备属性过滤器

过滤器通过设备的属性来过滤传入的消息，主要应用于设备的某些子集。过滤器表达式是一个JavaScript表达式，并且基本上定义了这个子集。您可以使用任何属性类型。

![image](/images/filter-attributes.png)

您可以使用以下变量编写布尔JavaScript表达式：

- cs		客户端属性
- ss 		服务器端属性
- shared	共享属性

如果您不确定某个属性是否存在，您可以添加检查它的类型是否定义。例如，如果客户端属性“firmware_version”设置为等于“1.0.0”。

假设有以下设备属性及其类型
客户端属性：firmware_version	country
服务器属性：balance
共享属性：subscription_plan

以下过滤器将匹配位于美国的正平衡的所有高级订阅设备，固件版本等于1.1.0

```javascript
cs.firmware_version=='1.1.0' && cs.country=='USA' && shared.subscription_plan=='premium' && ss.balance > 0
```

如果您不确定设备是否存在所有属性，则应使用以下语法来添加所有必需的“空”检查

```javascript
typeof cs.firmware_version !== 'undefined' && 
typeof cs.country !== 'undefined' && 
typeof shared.subscription_plan !== 'undefined' && 
typeof ss.balance !== 'undefined' && 
cs.firmware_version=='1.1.0' && cs.country=='USA' && shared.subscription_plan=='premium' && ss.balance > 0
```

## 设备数据过滤器

该过滤器允许通过数据值来过滤传入遥测消息，尤其适用于根据某些数据值来应用规则。

![image](/images/filter-telemetry.png)

您可以使用与您的遥测消息的键匹配的绑定来编写布尔JavaScript表达式。如果你不确定某个键是否存在于你的消息中，你可以添加检查它的类型为*undefined*。
例如，下面的过滤器将匹配**温度** > **100**度。

```javascript
typeof temperature !== 'undefined' && temperature > 100
```

假设从发动机控制器设备上载的遥测消息：

```json
{"temperature":1100, "enabled":true, "mode":"A"}
``` 

过滤器将匹配，如果设备启用，操作模式' A '和温度大于1000度

```javascript
temperature > 1000 && enabled == true && mode == 'A'
```

如果你不能保证所有的temelemtry数据点的消息，你应该使用下面的语法，添加所有必要的“零”检查

```javascript
typeof temperature!== 'undefined' && typeof enabled !== 'undefined' && typeof mode !== 'undefined' && 
temperature > 1000 && enabled == true && mode == 'A'
```

## 消息类型过滤器

该过滤器允许按类型过滤传入的消息，因此非常有用。建议在几乎每个规则中使用此过滤器来快速忽略不相关的消息。

- Get Attributes——获取设备的属性
- Post Attributes——发送设备属性
- Post Telemetry——发送数据
- RPC Request——RPC请求

![img](/images/filter-message.png)

## 方法名称过滤器

过滤器通过方法名称过滤传入的RPC请求消息。此过滤器将RPC请求转发给处理它们的特定插件非常有效。

一个过滤器中可选择多个方法名称。
例如，有两个插件，插件A允许获取当前时间getTime，插件B允许获得天气getWeather”。在这种情况下，需要配置两个规则：规则A指向基于“getTime”方法过滤器的插件A，规则B指向基于“getWeather”方法过滤器的插件B.

![image](/images/filter-method.png)
