---
layout: page
title: 插件
---

- [插件管理](#插件管理)
- [插件细节](#插件细节)
- [插件导入导出](#插件导入导出)
	- [插件导出](#插件导出)
	- [插件导入](#插件导入)
	- [故障排除](#故障排除)

## 插件管理

插件管理UI页显示系统和租户特定插件的表。每个插件有一个单独的卡。

你可以做以下操作：

- 导入或创建新插件
- 导出插件到JSON
- 暂停并激活特定插件
- 删除插件

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/plugins.png)


## 插件细节

每个插件是一个单独的卡表示。您可以编辑插件配置，并在插件详细信息面板中查看插件事件。

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/plugin-details.png)


您还可以在邮件处理过程中查看插件生命周期事件、统计信息和错误。

请注意，在频繁的错误的情况下，错误消息进行采样。

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/plugin-events.png)

## 插件导入导出

### 插件导出

你可以导出你的插件的JSON格式，导入到同一个或另一个thingsboard实例。

为了导出插件，你应该导航到**插件**页面，点击位于特定插件卡上的导出按钮。

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/plugin-export.png)

### 插件导入

类似的，导入插件，你应该导航到**插件**页面，然后点击屏幕右下角的大“+”按钮，然后点击“导入”按钮。

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/plugin-import.png)


**注意**所有导入插件处于暂停状态。导入后不要忘记**激活**你的插件。

### 故障排除

插件导入时可能出现的问题：

- 相应的插件API令牌**已使用**。可以在源JSON中选择其他标记并直接编辑它。
- 相应的插件实现在服务器路径**不可用**。


