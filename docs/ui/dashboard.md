---
layout: page
title: 仪表板
---

- [仪表板管理](#仪表板管理)
- [仪表板导出](#仪表板导出)
- [仪表板导入](#仪表板导入)

仪表板即最终终端用户可直观查看的类似仪器仪表的面板，通过数字化的处理，可直接查看实时数据、历史变化曲线、简单统计处理、仪表盘面板，以及一些其他的数据信息。

## 仪表板管理

管理员可为最终用户定义默认的仪表板，这样客户登陆后即为默认的仪表板界面,需执行如下操作：

1. 创建仪表板并分配给客户。
2. 打开“客户 -> 用户 ”，并使用屏幕右上角的编辑按钮切换到编辑模式。
3. 选择物联网IoT仪表板。从列表中选择IoT仪表板并应用更改。

	注意：可以设置“始终全屏”，以防止用户切换到不同的仪表板

![仪表板](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/ui-dashboard-1.png)

## 仪表板导出

可以将仪表板导出为JSON格式，并将其导入到相同的另一个实例中。
为了导出仪表板，首先应该切换到仪表板页面，然后单击位于要导出的仪表板卡片上的导出按钮。

![仪表板](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/ui-dashboard-2.png)

## 仪表板导入
同样的，要导入仪表板，首先应该导航到仪表板页面，并单击屏幕右下角的“+”按钮，然后单击导入按钮。

![仪表板](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/ui-dashboard-3.png)

在弹出“仪表板导入”窗口，系统将提示您上传json文件。

![仪表板](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/ui-dashboard-4.png)

 一旦点击“导入”按钮，需要指定设备别名。这允许设置哪些设备对应于仪表板设备的别名。
