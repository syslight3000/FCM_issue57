---
layout: post
title: "57期 - Ubuntu 游戏 Crayon Physics Deluxe"
date: 2012-09-22 13:33
comments: true
categories: issue57 Ubuntu-Games
---

#Ubuntu游戏 蜡笔物理学豪华版

Written by Riku Järvinen

作者：Riku Järvinen

翻译：陈嘉杰

# Crayon Physics Deluxe

#蜡笔物理学豪华版

This month we take a look at a game that also has potential as a science teaching tool in comprehensive schools. Some time ago, I grabbed Humble Bundle 3, including Crayon Physics Deluxe - a thoroughly planned collection of physics puzzles you solve by drawing different shapes. As I’m also a student of physics, I was intrigued to test the realism of the game. It turned out to be pretty much what I expected -- and more. Plus, it was created by the Finnish game developer Petri Purho of Kloonigames.

这个月我们看到了一款十分有潜力成为综合学校教学工具的游戏。前一段时间，我攫取到了独立游戏软件合集Humble Bundle的第三弹，其中包括蜡笔物理学豪华版——一个通过描绘事物来解决物理迷题的收集类游戏。因为我也是一名物理系的学生，所以我对游戏的真实性测试很感兴趣。测试结果和我预期的一样好————甚至更好。再补充下，它是由芬兰游戏开发商Kloonigames的Petri Purho所创。

## Installation & Overview

##安装 &amp; 概述

There was no trouble getting the game going, I just downloaded the .deb file and installed it with:

获取游戏没有什么困难，我只是下载了.deb文件，然后使用如下命令来安装它：

    sudo dpkg -i package_name.deb

The minimum requirements, at 1 GHz, 512 MB RAM, and 128 MB graphics RAM, are easily met (if in doubt, you can download the demo at [http://www.crayonphysics.com](http://www.crayonphysics.com) to test your specs). When you start Crayon, you are asked to register for additional features but this is not obligatory.

最低配置要求，处理器主频1GHz，512MB内存，以及128MB显存，很容易达到要求(如果不信的话，你可以在[http://www.crayonphysics.com](http://www.crayonphysics.com)下载试玩版，来测试你电脑的规格)。当你开始游戏，你会被询问是否进行注册以获得附加功能，但这并不是强制性的。

Because of the really calm music and bright-coloured graphics, my first impression was that this is probably a game for children or something. The levels seemed very easy, and I hacked through forty of them before realizing I had completely missed the point. Crayon is about elegance. Not only is it enough to find a solution to a problem: it must be “a good one”, i.e. meaning not to draw unnecessary objects. To complete each level perfectly, you have to come up with three different ones: elegant, old school, and awesome. The awesome solution is something you can choose freely among the ones you have developed to solve the problem. 

因为真实的轻音乐还有色彩斑斓的图像，我对游戏的第一印象就是，它可能面向的是儿童之类的群体。游戏等级看起来很简单，当我意识到我已经完全错过游戏的重点时，我已经打通四十关了。 蜡笔物理学旨在追求雅致。它不仅仅是为了找到一个问题的答案：而是找到“最好的答案”，即意味着不要画多余的物体。为了完美地完成每一关，你必须要想出三种方案：最优(elegant),老牌(old school),出色(awesome)。出色的解决方案就是你可以自由的根据已有的方案来解决问题。

## Gameplay & Features

## 游戏玩法 &amp; 游戏特点

Basically, you control a pen with your mouse, and draw objects of various dimensions to create dynamical movement. In each problem, your goal is to move a ball in such a manner that it will collide with a star, or, in some cases, multiple stars in one run. You can cheat by clicking on the ball to give it a small initial movement boost; this is not allowed in proper solutions. Actually, you can go further and realize that by adding objects beneath the ball you increase the potential energy (the energy associated with “higher ground” that is readily transformable to movement) of the ball, thus having an “infinite” supply of energy (in practice, the energy is limited by the height of the screen). Once you notice this little trick, there is no point in finding just some solution: it has to be a reasonable one, using the properties of the laws of physics instead of “faking energy”. 

你主要就是使用鼠标控制一根笔，然后画一些不同尺寸的物体造来成动态运动。在所有问题中，你的目标都是通过某种方式移动一个小球，来碰到一颗星星，或者，在某些情况下，一局中要碰到多颗星星。你可以使用点击小球这种投机的方式，来给小球一个小小的初始动力；但这不是正确的做法。事实上，你可以通过在小球下面增加一些物体来进一步增加小球的势能(“较高地势”的能量可以很容易的转移到运动中)。因此就有了一个“无限”的能量供应(在实际中，能量受到屏幕高度的限制)。一旦你注意到这个小技巧，那再找其他解决方案就没有什么意义了：它必须是有根据的一个方案，使用正确的物理规则来代替“伪能量”。

As for the gameplay itself, everything works as it should. Controls are introduced along the way so there is no need for a separate tutorial. Physics modelling is good. Only one slight problem occurs when you have multiple objects very close to one another. If you try to delete a specific one, another might accidentally disappear. This is not a real problem, though, if you play by the rules, in which case you need only a few objects for a good solution.

至于游戏本身，一切都很正常。操作会在游戏中介绍，所以不再需要单独的教程。物理现象塑造的非常好。只有一个小问题，发生在你创造的多个物体离得太近时。如果你试着删除指定的一个物体，那么另一个离得较近的物体也许会偶然地消失。虽然这不是什么真正的问题，但如果你按照规则来玩，一般情况下只需要少量的物体就可以得到一种好的通关方法。

The rotating castle problem and its solution are presented. The huge green-colored “arm” drags the bridge down, and gives the ball a movement boost towards the star. Most solutions, like this one, are developed by making small adjustments to known solutions (of course, in the beginning there are no “known solutions”, so you have to create one). 

接下来介绍下旋转城堡(rotating castle)这一关，还有它的通关方法。一根巨大的绿色“臂杆(arm)”把桥拖了下来，并给了小球一个初始动力移向星星。大多数通关方法，都和这个相似，都是通过对已知的方法进行小的调整开发出来的(当然，在一开始并没有“已知方法”，所以你首先要自己创造一种)。

The offline game alone has over 70 levels to provide tens of hours of excitement, if one commits to find all the elegant solutions without extra help. Registration gives access to extra content, and there is also a level editor for creating custom physics models of one’s own. Some of the levels towards the end are very, very difficult: I noticed that my physics background did not help me much.  In one custom scenario, a rocket is used to guide the path of the ball. A rocket is one of the standard components of Crayon Physics.

离线游戏就有超过70关，如果一个人能保证找到所有关的最优解(elegant solutions)而不借助其他帮助，那离线游戏可以让他兴奋好几十个小时。注册可以得到额外的游戏内容，而且还包括一个可以创建自定义物理模型的关卡编辑器。到了后面有些关会变的非常，非常难：我发现我的物理学背景没有给我提供更多的帮助。在某个自定义场景中，火箭常用于给小球引路。火箭也是蜡笔物理学中的一个标准组件。

## Crayon Physics as a teaching and learning tool

## 蜡笔物理学作为一个教学工具

I started my university studies to become a physics teacher, and, as far as my experience can tell, this game would be an awesome tool in comprehensive school. It makes Newton’s laws become real through meaningful experiences, not just some non-living graphs in textbooks (which, by definition, are boring: games aren’t). This is important, since the scientific research in physics education has shown students experience clear conceptual difficulties dealing with “real physics” (as opposed to problem-solving skills, which still could be excellent).

为了成为一名物理老师，我进入大学学习，然后直到我的经验告诉我，这个游戏也许能在综合学校中成为一个出色的教学工具。它让牛顿定律成为了真正有意义的经验，而不是教科书上死板的图表(概念定义是无聊的：游戏却不是)。这是非常重要的，因为物理教育的科学研究已经表明学生在“真实物理”的概念上理解有困难。


If I was to teach school physics now, I would contact the developer for a permission to use the game during lessons.

如果我现在在学校里教物理，那我会向游戏开发商申请在课堂教学中使用此游戏。

## Where to get it

## 获取游戏的方式

If you did not catch the Humble Bundle, Crayon Physics Deluxe can be bought at the Developer’s website [http://www.crayonphysics.com](http://www.crayonphysics.com). Although a bit pricey compared with the Bundle, it’s still a good choice. I’d recommend it to anyone into puzzles and physics!

如果你没有得到独立游戏软件合集Humble Bundle的话,那可以在游戏开发商的网站[http://www.crayonphysics.com](http://www.crayonphysics.com)购买蜡笔物理学豪华版。尽管价格与合集相比会高一点，但它仍是一个不错的选择。我会把这个游戏推荐给所有对物理有困惑的人。

Riku Järvinen (rierjarv) is a CS major student from Finland who delves into the Linux and Open Source gaming world once in a while.

作者Riku Järvinen (rierjarv)是芬兰的一位主修计算机科学的学生，他时不时地会钻研下Linux操作系统，还有开放源代码的游戏。

