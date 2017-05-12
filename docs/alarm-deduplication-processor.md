---
layout: docwithnav
assignees:
- ashvayka
title: 重复报警删除处理器

---
##摘要

该处理生成唯一的报警，可指定报警ID和报警主体。当组件处理传入设备消息时，将消息值和设备属性替换为模板。报警唯一性由报警ID的结果值控制。如果处理器检测到唯一的警报，它将添加以下元数据：

- 是新报警的布尔值为TRUE；
- 报警ID字符串；
- 报警主体字符串。

![img](/images/process.png)

#配置
使用某些上下文完成报警主体，主体用基于设备消息和属性的值填充。并可使用cs/ss/shared等变量名称属性值。

- CS		客户端属性
- SS		服务端属性
- shared	共享属性

遥测值使用其键直接推送到上下文。上下文也填充保留的日期对象。例如，以下模板：

``` javascript
[$date.get('yyyy-MM-dd HH:mm:ss')] Device $cs.get('serialNumber')($cs.get('model')) temperature is $temperature.valueAsString!
```

将被转化成

``` 
[2016-01-02 03:04:05] Device SN-001(A) temperature is 100!
```

对设备来说

 - 客户端属性 **serial number** = SN-001
 - 客户端属性 **model** = A

测量数据为

```json
{"temperature":100}
``` 

我们建议将报警的日期和一些唯一的设备属性包含在alarm id模板中。这将确保您不会频繁地为相同的设备问题生成报警。
