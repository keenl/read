.. _201212_obama_fundraising_website:

奥巴马筹款网站的制作过程
===========================================

`ruanyifeng.com <http://www.ruanyifeng.com/blog/2012/12/obama_fundraising_website.html>`__

1.

Kyle Rush是一个网站工程师。

2011年6月，他加入\ `BarackObama.com <http://www.barackobama.com/>`__\ ，负责设计2012美国大选的奥巴马官网。

（图为2011年6月的奥巴马官网）

除了宣传，官网的主要目的就是筹款。

上一次大选，奥巴马筹到了6.9亿美元。这是一个很大的数字，但由于过去4年美国经济一直没有起色，本次大选势必要投入更多的资金，团队内部估计资金需求将达到创纪录的10亿美元。

一个筹集10亿美元的网站，历史上从来没有过。Kyle
Rush不知道自己能否做到，但是他很清楚，如果筹不到钱，奥巴马没法赢得大选。

2.

2012年美国大选现在已经结束了，奥巴马有惊无险地击败了罗姆尼。他最终筹到了11亿美元，成为历史上筹款金额最高（也是花钱最多）的总统候选人。（排在第二位的就是罗姆尼，他也筹到了10亿美元。）

这11亿美元之中，线下筹集了4.1亿，线上筹集了6.9亿。单单BarackObama.com一个网站，就创造了2.5亿美元的捐款。

在6个月的时间里，BarackObama.com共有

    　　\* 17,807,917个访问者，81,548,259次页面访问

    　　\* 4,276,463次捐款

    　　\* 捐款转化率24%（每四个访问者，就有一人会捐款）

这样辉煌的成绩，是如何取得的？

3.

制作一个超大流量的、体验良好的、能够说服人们捐款、并能安全快速处理这些捐款的网站、绝非易事。

最近，Kyle
Rush写了一篇\ `文章 <http://kylerush.net/blog/meet-the-obama-campaigns-250-million-fundraising-platform/>`__\ ，披露了许多内幕，从技术角度总结了BarackObama.com的制作心得。下面，我们就来看看奥巴马的技术团队是怎么做到的。

（图为2012年5月的奥巴马官网）

网站的制作班子，从2011年下半开始组建，Kyle
Rush是第一个加入的前端工程师，负责网页的外观和用户体验。

一开始，网站放在团队自购的服务器上，运行和捐款都还算平稳。但是，随着竞争不断加剧，局势变得令人担忧了。到了2012年5月，罗姆尼当月的筹款金额第一次\ `超过 <http://delicious.com/redirect?url=http%3A//news.xinhuanet.com/world/2012-06/09/c_123257721.htm>`__\ 了奥巴马。

竞选总部决定，网站必须改版，尽一切可能争取捐款。于是，技术团队开始大规模的扩充，全职的前端工程师从1个人扩充到了14个人，其中6人专门负责制作筹款页面。

4.

技术团队做出的第一个决定是，使用静态网站生成器\ `Jekyll <http://jekyllrb.com/>`__\ ，用静态网页取代动态网页，加快网页打开速度。网站的打开应该\ `越快越好 <http://www.stevesouders.com/blog/2010/05/07/wpo-web-performance-optimization/>`__\ 。有研究称，打开速度每慢100毫秒，Amazon的销售额就下降1%。

第二个决定是，将全部网页放上CDN，使用的服务商是\ `Akamai <http://www.akamai.com/>`__\ 。它是世界最大的CDN供应商，共部署了50000多台服务器，美国各地都能获得理想的访问速度。奥巴马芝加哥竞选总部，可以在20毫秒内载入官网的HTML网页。

第三个决定是，将捐款的后台做成\ `API调用 <http://tools.bluestatedigital.com/pages/quick-donate>`__\ 。这是因为有23%的访问者使用移动设备，所以必须部署多个前端（Web端和移动端）。使用API，可以让不同前端以相同方式与后台通信，彼此之间用JSON格式传递信息。

第四个决定是，后台用PHP语言开发，放在Amazon的EC2平台上。

第五个决定是，为了避免宕机，开发两个后台。一旦一个系统停止工作，立刻自动切换到另一个。这点很重要，因为宕机不仅影响士气，而且经济损失巨大。因为捐款每分钟都在涌入，最高记录是一小时300万美元，你不能让它停下来。

5.

新网站初步完成后，使用\ `webpagetest.org <http://www.webpagetest.org/>`__\ 进行测试，结果令人鼓舞。

原版页面4秒钟后还没载入，新版只用1秒就可以看到。整个平台的访问速度上升了60%，捐款转化率增加了14%。

接下来，就是微调页面的各种细节，一共进行了240次\ `a/b测试 <http://en.wikipedia.org/wiki/A/B_testing>`__\ ，也就是说，至少迭代了240个版本。

调整后的页面，视觉效果和用户体验都有了巨大的提升（点击看大图），捐款转化率因此又提高了49%。。

随着奥巴马的当选，BarackObama.com共进行了1101次前端部署。

6.

事实证明，整个开发方案非常成功，顺利完成筹款任务，没有一分钟宕机。

Kyle
Rush感到有必要总结，留下记录。除了上面的开发过程，他还提到前端团队使用的工具：版本控制\ `Github <https://github.com/>`__
，a/b测试管理\ `Optimizely <https://www.optimizely.com/>`__\ ，代码编译\ `CodeKit <http://incident57.com/codekit/>`__\ 。

Kyle Rush最后总结说：

    “我百分之百肯定，这是我经历过的最好的开发环境。我们不断调整，捐款转化率的提高令人难以置信。整个团队感到无比满足。但是，最高兴的还是看到，2013年1月21日巴拉克·奥巴马依然是美国总统！”

| （完）

.. note::
    原文地址: http://www.ruanyifeng.com/blog/2012/12/obama_fundraising_website.html 
    作者: 阮一峰 

    编辑: 木书架 http://www.me115.com