---
layout: docwithnav
assignees:
- ashvayka
title: 方法名称过滤器

---
## 摘要
过滤器通过方法名称过滤传入的RPC请求消息。此过滤器将RPC请求转发给处理它们的特定插件非常有效。
## 配置
一个过滤器中可选择多个方法名称。
例如，有两个插件，插件A允许获取当前时间getTime，插件B允许获得天气getWeather”。在这种情况下，需要配置两个规则：规则A指向基于“getTime”方法过滤器的插件A，规则B指向基于“getWeather”方法过滤器的插件B.

![image](/images/filter-method.png)
