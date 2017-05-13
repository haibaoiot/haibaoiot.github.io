---
layout: page
title: 邮箱设置
---

邮箱为系统推送邮箱，即发送账号激活、找回密码、官方报警通知等的邮箱服务器，可通过API，也可通过现有邮箱smtp登录发送的方式，本例为我方企业邮箱来发送完成。

邮箱配置配置系统发送邮箱，即发送账号激活、找回密码、官方通知邮件等的发送邮箱。即客户接收到的系统发送邮件的邮箱，都是在这里设置的。

![image](https://raw.githubusercontent.com/haibaoiot/haibaoiot.github.io/master/images/ui-mailset.png)

上图为采用腾讯企业邮箱的设置，注意发件人”<>”内的邮箱要与下方登录用户名一致。

如果采用其他邮箱，则根据实际情况设置，如126邮箱，则smtp协议为smtp而不是smtps，smtp主机为smtp.126.com，端口为25，最下方为126邮箱的账户名和密码（注意126邮箱需开启外部smtp支持）。

最后注意要保存并发送测试邮件，以测试是否成功。 