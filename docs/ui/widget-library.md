---
layout: docwithnav
assignees:
- ashvayka
title: Widgets Library
description: Thingsboard Dashboard Widgets Library

---

* TOC
{:toc}

#**小部件包**#

系统提供的小部件包默认分为六组，一共超过30个小组件可以使用，另外也可以自己添加自己的组和部件。

![img](/images/ui-widget-1.png)

##组件类型
默认情况下有四种类型的小部件可用：

- 最新值 - 显示特定设备属性或时间序列数据点的最新值。
- 时间序列 - 在特定时间窗口中显示所选时间段的最新值或最新值的历史值。
- RPC - 允许向设备发送RPC命令并处理/可视化设备的回复。
- 静态 - 显示静态可定制的HTML内容。

![img](/images/ui-widget-12.png)

##数据源类型
每个部件都需要对数据源进行数据的可视化显示，数据源的数据类型取决于组件类型。

- 目标设备 - 此数据源类型用于RPC。基本上，您需要指定RPC小部件的目标设备
- 设备 - 此数据源类型用于时间序列和最新值小部件。基本上，您需要指定目标设备和时间序列键或属性名称。
- 功能 - 此数据源类型用于时间序列和最新值小部件，用于调试目的。基本上，您可以指定将从设备模拟数据的javascript函数，以调整可视化。

##Digital Gauges
用于温度，湿度，速度和其他整数或浮点值的可视化。

![img](/images/ui-widget-2.png)

##Analog Gauges

类似于数字仪表，但具有不同的风格。

![img](/images/ui-widget-3.png)

##Charts

用于通过时间窗口可视化历史或实时数据。
 
![img](/images/ui-widget-4.png)

##GPIO widgets

可用于目标设备的GPIO状态的可视化和控制。

![img](/images/ui-widget-5.png)

##Maps widgets

对于设备的可视化有用，地理位置和轨道设备都以实时和历史模式进行路由。
 
![img](/images/ui-widget-6.png)

##Cards
可用于表格或卡片小部件中的时间序列数据或属性的可视化。

![img](/images/ui-widget-7.png)

##小部件包捆绑导入/导出
#####小部件包捆绑导出
您可以将窗口小部件包导出为JSON格式，并将其导入到相同或另一个Thingsboard实例。
为了导出窗口小部件包，您应该导航到“ 窗口小部件库”页面，然后单击位于特定窗口小部件包卡上的导出按钮。

![img](/images/ui-widget-8.png)

#####小部件包捆绑导入

类似地，要导入小部件包，您应该导航到“ 小部件库”页面，然后单击屏幕右下角的大“+”按钮，然后单击导入按钮。

![img](/images/ui-widget-10.png)

弹出窗口小部件包导入窗口，弹出提示您上传json文件。
##小部件导入/导出
#####小部件导出
您可以将特定的小部件类型从小部件包导出为JSON格式，并将其导入到相同或另一个Thingsboard实例。
为了导出窗口小部件类型，您应该导航到窗口小部件库页面，然后打开所需的窗口小部件包，最后单击特定窗口小部件类型卡上的导出按钮。

![img](/images/ui-widget-9.png)

#####小部件类型导入
类似地，要导入窗口小部件类型，您应该导航到窗口小部件库页面，然后打开您的窗口小部件包，然后单击屏幕右下角的大“+”按钮，然后单击导入按钮。

![img](/images/ui-widget-11.png)

弹出窗口小部件类型导入窗口，系统将提示您上传json文件。