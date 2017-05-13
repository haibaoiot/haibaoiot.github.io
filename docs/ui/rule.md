---
layout: page
title: 规则
---

- [管理](#管理)
- [详情](#详情)
- [导入与导出](#导入与导出)
	- [规则导出](#规则导出)
	- [规则导如](#规则导入)
	- [故障排除](#故障排除)
- [](#)

## 管理
规则为管理用户界面页显示系统和租户特定规则的表，每个规则有一个单独的卡。

你可以做以下操作：

- 导入或创建新规则
- 导出规则到JSON
- 暂停并激活特定规则
- 删除规则

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/rules.png)

## 详情
每个规则都表示为单独的卡。您可以编辑规则组件并在规则详细信息面板中查看规则事件。

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/rule-details.png)

还可以在消息处理过程中检查规则生命周期事件、规则统计和错误。
请注意，在频繁的错误的情况下，错误消息会进行采样，故会丢失部分错误

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/rule-events.png)

## 导入与导出

### 规则导出

你可以导出你的规则以JSON格式导入到同一个或另一个thingsboard实例。
为了导出规则，您应该导航到**规则**页，然后单击位于特定规则卡上的导出按钮。

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/rule-export.png)

### 规则导入

类似的，导入规则，你应该导航到**规则**页，然后点击屏幕右下角的大“+”按钮，然后点击“导入”按钮。

![](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/rule-import.png)


注意：所有导入规则均处于暂停状态。别忘了在导入后激活你的规则。

### 故障排除

导入规则时可能出现的问题：

- 相应的目标插件**未导入**。
- 相应的目标插件**未激活**。
