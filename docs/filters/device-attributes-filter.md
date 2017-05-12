---
layout: docwithnav
assignees:
- ashvayka
title: 设备属性过滤器

---
##摘要
过滤器通过设备的属性来过滤传入的消息，主要应用于设备的某些子集。过滤器表达式是一个JavaScript表达式，并且基本上定义了这个子集。您可以使用任何属性类型。

![image](/images/filter-attribute.png)

##配置

您可以使用以下变量编写布尔JavaScript表达式：

- cs		客户端属性
- ss 		服务器端属性
- shared	共享属性

如果您不确定某个属性是否存在，您可以添加检查它的类型是否定义。例如，如果客户端属性“firmware_version”设置为等于“1.0.0”。
##举例
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
