---
layout: docwithnav
assignees:
- ashvayka
title: 设备数据过滤器

---
##摘要
该过滤器允许通过数据值来过滤传入遥测消息，尤其适用于根据某些数据值来应用规则。

![image](/images/filter-telemetry.png)

##配置

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


