---
layout: post
title: "57期 - 备份策略 - 第5部分 Dropbox"
date: 2012-09-22 13:35
comments: true
categories: issue57 HOW-TO backup-strategy
---

#备份策略 - 第5部分 Dropbox

Written by Allan J. Smithie

作者:Allan J. Smithie   翻译：陈嘉杰

The Cloud back-up and storage market is getting crowded with new players offering ever more ludicrous amounts of free space, but we couldn't run this series without looking at one of the established 'brand names'; Dropbox is one of the most popular Cloud storage and file sharing programs, and has built up quite a following in the last couple of years.

云备份和存储的市场，因为新的服务商能提供更多可以用可笑荒谬来形容的免费空间而显的日益拥挤，但是我们不能仅凭借这点就去使用它，而忽略了“品牌”的成熟度；Dropbox是时下最流行的云存储和分享的应用之一，而且在几年之前就建立起品牌了。

## View from the Top

## 纵向审视

Dropbox is a reliable on-line data backup service that lets you access and share files from almost any computer or mobile device - using native clients or its web interface. It is one of the few truly platform-agnostic services, with client software for Windows, Mac, and Linux; you'll find a .deb package for the Dropbox client in the 11.10 Ubuntu Software Center for a painless, one-click install of a client we can happily report 'just works.' Add to that mobile clients for iPad, iPhone, Android, and Blackberry, and you can see the Dropbox bid for ubiquity across devices that gives it an appeal beyond its competitors. I'd have to say some of those mobile apps do look a little thin on functions, but that's not unique to Dropbox.

Dropbox提供一个可靠的在线数据备份服务，它可以让你通过使用客户端或者其它的web接口，在几乎任何计算机或是移动设备上，存取和分享文件。它是少数几个能够真正提供跨平台服务的服务商之一，具有Windows，Mac，以及Linux操作系统的客户端软件；你能在11.10版的Ubuntu软件中心里，很轻松的找到一个Dropbox客户端的.deb包，一键式的客户端安装模式让我们可以愉快的进行“工作”。Dropbox新增了iPad, iPhone, Android，以及Blackberry所对应的移动客户端，从这些争取实现全设备支持的做法中你可以看到，Dropbx从其他竞争者中脱颖而出。我不得不说这些移动应用看起来功能还有点少，但Dropbox所拥有的功能不只是这些。

From our corner, the current Linux client is a mature development over previous, ahem, 'idiosyncratic' versions, so now the free package of 2GB online storage with a high reliability desktop client, collaboration features and continuous development, is quite sufficient for home users starting out in the Cloud. By way of an incentive, Dropbox has an attractive referrals programme for increasing your initial free allocation from 2GB of free space up to a usable 8GB by referring friends. 

从我们的角度来看，当前Linux客户端较之前版本来说已经成熟多了，啊哈，还是“特别发行版”，现在2GB的免费在线存储空间包装在一个具有高可靠行的桌面客户端中，云服务的可协作性和持续发展性，对用户的初次使用来说是十分有必要的。Dropbox有一套很诱人的奖励方式，让用户邀请更多的好友注册，来将初始的2GB的免费空间升级至8GB。

## Feel the Width

## 横向感受

The paid plans (above 2GB) go up to 50GB (Pro 50 at $9.99 a month) and 100GB (Pro 100 at $19.99 a month). Beyond that, Dropbox will do you a deal on the Teams plan for storage space in the Terrabytes. The paid service at times looks a bit pricier than competing online data backup services, depending on the current offers in the market, whilst the help and support options are a little limited. You can contact Dropbox support only by email at present. I'm guessing the margins are too thin to afford technical and customer support by chat or telephone as well. The online Help Center is fairly rich, organized by topic and operating system. Dropbox also hosts a product tour, a forum, and a wiki. That said, turnaround on simple queries seems to occur within a couple of hours.

Dropbox的付费模式：2GB版（2GB以下免费使用），50GB版（50GB空间每月9.99美元），100GB版（100GB空间每月19.99美元）。如果需要更多的空间，Dropbox会专门为你定制一份TB级别的存储空间。Dropbox的有偿服务从目前的云服务市场来看，它与其他提供在线数据备份的服务商相比，价格显得有些昂贵，同时它的支持和帮助服务也有些限制。目前你只能通过电子邮件来获得Dropbox的帮助。我觉得可能是因为用人工或电话服务来提供技术支持的话，可能会使其成本变高。但是Dropbox的在线帮助系统还是比较丰富的，按照话题和操作系统有条理的组织。Dropbox还有产品演示，官方论坛，以及wiki页面
。也就是说，换成这种简单的查询方式也许能节省好几个小时的时间。

## Features

## 功能

Dropbox was one of the early services to enable 'blind' public links for sharing files over the web, which is one of the things I do most. You can share individual files, whole folders, or image galleries - that are viewable by anyone, either by creating a public link or by sharing them with a controlled group. Create the folder that contains the items you want to share, and then enter the email addresses to which you want to send the sharing invitation. Two more of the Dropbox features worth outlining are Versioning and Sync. 

Dropbox也是最早的几个能够提供全网“blind”公共链接分享服务的服务商之一，这也是我最常使用的功能。你可以创建公共链接或是分享到指定的圈子里，来分享单个的文件，整个文件夹，或是让所有人都可以看得到的图片库。创建一个文件夹包含你想要分享的内容，然后输入好友的邮箱地址发出分享邀请吧。Dropbox还有两个更值得概述的功能分别是版本控制和同步管理。

Anything stored on the Dropbox servers has one-month history – that is, any files deleted can be recovered with the next thirty days; it's a simple feature for home users’ convenience rather than any kind of version-control for writers, programmers or designers. There is unlimited 'versioning,' called Pack-Rat, or Dropbox Rewind for businesses, which is a paid add-on.

任何存储在Dropbox服务器上的文件都有一个月的历史记录，也就是说，被删除的文件都可以在接下来的一个月内恢复；这个功能对用户来说，比使用那些专门为作家，程序员或是设计师所用的版本控制软件要方便的多。通过付费可以实现无限的“版本纪录”，也就是所谓的Pack-Rat，或者企业版的Dropbox Rewind。
	
The Sync feature will help a lot when you spread your work across multiple devices. Installing Dropbox on each device registered with your account will enable the automatic synchronize function whenever you change, add or delete a file. It's quite flexible in the choices available:

当你要在多个设备上进行工作时，同步功能可以提供很大的帮助。在每个设备上安装Dropbox的客户端，再注册个帐号登录，并打开自动同步功能，这样无论你什么时候进行了修改，添加，或是删除操作，Dropbox都能为之同步。这还有几个灵活多变的选项可供选择：

- what to sync - select the folders you want to sync
- with whom to sync – you select the people (using email invitation) with whom you want to sync a particular folder .

- what to sync - 选择你想要同步的文件夹
- with whom to sync - 选择好友（通过邮件邀请）分享一个指定的文件夹。

Anything you do on individual machines can also be managed from the web interface, so you don't need to have a Dropbox client installed on shared machines in order to have access to your data wherever you go. 

你能做的任何操作都可以通过web接口来实现，所以无论在哪，你都不必为了获取数据而在所使用的机器上专门安装Dropbox的客户端软件。

The only negative point I really have against Dropbox is conflict management; I don't mean it's like a war zone, but sometimes you have issues if different people access a file at the same time and modify it. It's a tricky technical issue in networking and databases at the best of times, so this is not a surprise 'feature' of a Cloud storage service, particularly when Dropbox is pushing the collaborative and sharing side of operations.

我对Dropbox唯一不满的的地方就是它的冲突管理。有些时候如果你有一份期刊，不同的人在同一时间打开它并进行了修改，这种做法会造成混乱，但我的意思不是说这种情况就好像战场般凌乱。即使在网络和数据库都在最优的情况下，这仍是一个棘手的技术性问题，所以这并不是云存储服务的一种奇特的“功能”，尤其是在Dropbox推进同步和分享的业务时候。

One thing that isn't supported is sycning files outside of the centralised Dropbox folder. You can work around this by linking, but when other operating systems have implemented virtual folders ('libraries'), we could do with a sync service that's able to do the same.

Dropbox无法将指定文件夹外的内容进行同步。你可以通过链接技术来解决这个问题即使当我们换了一个操作系统来创建虚拟文件夹（“资料库”）时，我们仍可以通过类似的操作来进行同步服务。


## Security

## 安全性

This is always the potential pitfall of the Cloud. Dropbox uses the SSL Secure Socket Layer protocol for transfers, and encrypts all files using AES-256 before storing them on its servers; anything shared is then made visible by exception. Public folders are viewable by anyone who can find them. Photo gallery links give access to anyone with whom you share the link to the gallery, but they cannot access other areas of your account.

这一直都是云服务的潜在隐患。Dropbox使用SSL安全套接字层协议来进行传输，并在文件存入服务器之前，使用AES-256加密算法对文件进行加密；公共文件夹对任何找到的人来说都是可见的。你可以通过图片库链接，让你分享到的圈子内的所有人都可以看到图片库的内容，但是他们不能获取你帐号上其它区域的数据。

I think the mechanism of sharing by email invitation needs some work. The next feature release needs to link Dropbox users by account, thereby securing sharing within the bounds of Dropbox security. I believe this is how the Teams product works, so this needs to filter down to the consumer level.

我觉得使用邮件邀请来进行分享的这个机制的安全性还需要进一步加强。下一个功能的发布时，对于这个机制应该要链接至用户的Dropbox帐号后再进行操作，这样分享时的安全性就能在Dropbox的可控范围内。我相信这就是团队工作的方式，所以当所需的就是渗透到用户级别。

One thing I found a little unsettling was the April 2011 change to the Dropbox privacy policy. “We may disclose to parties outside Dropbox files stored in your Dropbox, and information about you that we collect, when we have a good faith belief that disclosure is reasonably necessary.” In other words, the encryption keys are known to Dropbox staff. This, too, is not unique to Dropbox, but it should serve as a reminder that the convenience of the Cloud may be offset by the loss of control over your personal data.
 
唯一一件令我感到小小的不安的事情就是，在2011年的四月份，Dropbox的隐私政策发生了改变。“当我们有足够的理由相信，有必要披露你在Dropbox所存储的文件和你的个人信息时，我们会将这些所收集到的内容公之于众。”换言之，密钥对Dropbox的员工来说是可见的。这一点，也并不是针对Dropbox，但是作为云服务商至少应该担任提醒者的角色，这点便利性也许能补偿下那些失去私人数据控制权的用户。
 

## Conclusion

## 结论

I haven't had to worry too much, this last year. Dropbox sits quietly in my notification area, reliably getting on with the job; background syncing is no trouble, it doesn't hog my bandwidth when on-line, and the availability across platforms makes for a break-out experience, whether at home or at work.

在过去的一年中，我对Dropbox没有太多的顾虑。Dropbox一直悄悄地待在我的通知区里，可靠的进行工作；后台同步没有什么问题，上网时它也没有占用多少带宽，而且它跨平台的易用性，让我不管是在家还是在工作时都能消停会。

Allan J. Smithie is a journalist and commentator based in Dubai. His blog, 'No Expert,' is at: [http://allanjsmithie.wordpress.com](http://allanjsmithie.wordpress.com)

Allan J. Smithie是一名新闻记者和评论员，在迪拜工作。他的博客“No Expert”的地址是：[http://allanjsmithie.wordpress.com](http://allanjsmithie.wordpress.com)

