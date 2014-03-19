---
title: '晒你妹'
layout: post
guid: 2014/03/18/shainimei.html
tags:
    - scrapy 
    - flask
    - beansdb
    - gunicorn
---

经常逛豆瓣，请不要害羞等几个小组亮瞎了我的双眼，不能直视，三观全毁。在内心里默默念道以后再也不上这些小组了。..., 可意识坚定敌不过菇凉白花花的大腿。然后每天就翻这些帖子，可翻这些帖子太花时间了。我只喜欢看菇凉不喜欢看评论神马的，然后就动手把小组里的图片抓下来然后以瀑布流的形式展示。独乐乐，不如众乐乐，但不要叫我雷锋...

抓取用scrapy，每一个小时抓取一次，然后把结果保存为json文件。豆瓣对访问次数有限制，我用了<http://www.samair.ru/proxy-by-country/China-01.htm>上的代理，获取这些代理以后需要验证是否是匿名代理，并且验证访问豆瓣的速度，目前滤掉了连接和读取时间超过3s的代理。

定时脚本然后把数据录入到数据库中，把图片存放到beansdb中。

网页程序了用了我最喜欢的flask，除了可以参考flask的官方文档外还可以参考<http://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world>， 前端用了bootstrap,masonry。

部署采用nginx+gunicorn, gunicorn作为python-cgi的容器，可以参考<http://www.onurguzel.com/how-to-run-flask-applications-with-nginx-using-gunicorn/>, 顺便吐槽下开始准备用uwsgi，在网上找了半天资料都没有搞定然后转投gunicorn了..

网址是http://115.29.140.202/， 域名还在备案中, <http://shainimei.com>



