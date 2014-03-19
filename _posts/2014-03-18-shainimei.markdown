---
title: '大胆晒'
layout: post
guid: 2014/03/18/shainimei.html
tags:
    - scrapy 
    - flask
    - beansdb
    - gunicorn
---

经常逛豆瓣，请不要害羞等几个小组亮瞎了我的双眼，不能直视，三观全毁。在内心里默默念道以后再也不上这些小组了。..., 可意识坚定敌不过菇凉白花花的大腿。然后每天就翻这些帖子，可翻这些帖子太花时间了。我只喜欢看菇凉不喜欢看评论神马的，然后就动手把小组里的图片抓下来然后以瀑布流的形式展示。独乐乐，不如众乐乐，但不要叫我雷锋...

这些菇凉晒的尺度为什么这么大啦？我想原因大概如下：

1. 豆瓣是一个陌生人社区，小组里的人基本上在现实社会中没有交集，所以基本上没有心理负担。

2. 这些菇凉想迅速的让他人了解，认可。菇凉常常会说如果评论超过500楼，会上高清、正面的大图，喜欢的数目、评论的数目、yp豆油的数目她们都很在意的，这些数字反应了他人对她外表的认可。

3. 还有一部分是偶尔空虚寂寞冷发图的。

下面说说大胆晒的技术实现细节。

1. 抓取用scrapy，每一个小时抓取一次，然后把结果保存为json文件。豆瓣对访问次数有限制，我用了<http://www.samair.ru/proxy-by-country/China-01.htm>上的代理，获取这些代理以后需要验证是否是匿名代理，并且验证访问豆瓣的速度，目前滤掉了连接和读取时间超过3s的代理。

2. 定时脚本然后把数据录入到数据库中，把图片存放到beansdb中。

3. 网页程序了用了我最喜欢的flask，除了可以参考flask的官方文档外还可以参考<http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world>， 前端用了bootstrap,masonry。

4. 部署采用nginx+gunicorn, gunicorn作为python-cgi的容器，可以参考<http://www.onurguzel.com/how-to-run-flask-applications-with-nginx-using-gunicorn/>, 顺便吐槽下开始准备用uwsgi，在网上找了半天资料都没有搞定然后转投gunicorn了..

5. 后台的人工审核，定时会把漏点或低质的图片删掉。

网址是http://115.29.140.202/， 域名还在备案中, <http://dadanshai.com>



