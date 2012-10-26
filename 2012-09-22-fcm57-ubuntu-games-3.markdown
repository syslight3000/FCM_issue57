---
layout: post
title: "57期 - Ubuntu 游戏 Installing Minecraft"
date: 2012-09-22 13:33
comments: true
categories: issue57 Ubuntu-Games
---

#Ubuntu游戏 安装《我的世界》

Written by Peter Liwyj

作者：Peter Liwyj

翻译：陈嘉杰

This article assumes you have Ubuntu installed and ready to go, and you’re sitting looking at a Unity desktop [I’ll add Kubuntu notes where I can - Ed]. 

这篇文章假设你已经装有Ubuntu系统并准备使用，而且你使用的是Unity桌面,[有机会的话我会加入Kubuntu环境下的安装笔记- Ed]。

First, you need a 3D video driver. On your nice new Unity desktop, which is probably confusing you, click on "Dash home" on the top left of the Unity desktop.

首先，你需要3D视频驱动。在你新潮的Unity桌面上，这可能混淆你，点击Unity桌面左上角的“开始菜单(Dash home)”。

At the bottom of the screen you'll see some icons.  Click on the Pencil/Pen/Ruler icon.

在屏幕的底部你将会看到一些图标。点击铅笔/笔/橡皮样子的图标。

Top left of the next screen, you'll see "Additional Drivers." This is for your video card, and perhaps other things. (For Kubuntu, click K > Applications > System > Additional Drivers). Select an appropriate video driver, then click on "Activate." Enter your password in the box that pops up. Let the driver download and install. You’ll probably have to reboot to load the drivers. The little gear shape at the top right of the Unity desktop has the shutdown option in it.

在接下来出现的画面左上角，你将会看到“额外驱动(Additional Drivers)。”这是为你的显卡，或者其它设备提供的。(Kubuntu下，点击 K &gt; Applications &gt; System &gt; Additional Drivers)。选择一个合适的视频驱动，然后点击“激活(Activate)。”在弹出的对话框输入你的密码。让驱动自动下载和安装。你可能要重启电脑来装载驱动。在Unity桌面的左上角,有一个小齿轮形状的按钮里有关机选项。

Now it’s time to install Java. If you previously installed the “restricted extras,” you probably have it already. If not, click on the "Ubuntu Software Centre." It starts out as the 5th icon up on the left side of the Unity desktop, looks like a shopping bag. (In Kubuntu, it’s K > Applications > System > Muon Software Centre.)

现在是时候装Java了。如果你之前已经装过“受限制的额外设备(restricted extras)”，那你可能就装过Java了。如果没有，点击“Ubuntu软件中心”。它是Unity桌面的左侧第五个图标，看起来像一个购物包。(在Kubuntu下，点击 K &gt; Applications &gt; System &gt; Muon Software Centre。)

Search for "Java."

搜索“Java”。

You'll get several options, you want "OpenJDK6 Java runtime" (not seven - you want JDK six). Install it.

你将会得到几个选项，你需要的是“OpenJDK6 Java runtime”(不是 7 - 你需要的是JDK 6)。安装它。

Go to Minecraft.net and download the minecraft.jar file by saving it on your desktop, or wherever you like. First, open it in your favorite archive manager, and poke around. You're looking for the favicon.png file. It's a picture of a Minecraft block, save a copy of it somewhere out of the way for later.

登录[Minecraft.net](http://www.Minecraft.net)并下载minecraft.jar文件到你的桌面上，或者其它你喜欢的位置。首先，用你最喜欢的文档管理器打开它，然后做点别的事情。你会看到favicon.png文件。这是我的世界的图片中的一块，稍后把它存个拷贝放到别的不碍事的地方。

Go back to your minecraft.jar file, right click on it, and select ‘properties’ at the bottom of the menu. In the BASIC tab, click on the picture and navigate to the favicon.png you saved earlier. In the PERMISSIONS tab, check the "allow executing this file as a program" (“Is Executable” in Kubuntu) check box, and in the OPEN WITH tab (In Kubuntu you get this by right-clicking the file and selecting “Open With...”), and select OpenJDK Java 6 runtime - and make it default while you're there.

回到你的minecraft.jar文件，用右键点击它，接着在菜单的底部选择“属性(properties)”。在基本(BASIC)标签页，点击图片接着进入之前你存放favicon.png文件的路径。在权限(PERMISSIONS)标签页，勾选“允许以程序执行文件(allow executing this file as aprogram)”(在Kubuntu里是“是否允许执行(Is Executable)”)的选项，接着在打开方式(OPEN WITH)标签页(在Kubuntu你可以通过右键点击文件再选择“打开方式(Open With...)”)，再选择OpenJDK Java 6 运行环境，最后使之成为默认选项。

TIP: You can also enter:

提示：你也可以键入：

    java -jar

as the starting application to the ‘open with’ window in Kubuntu. You can also create a desktop ‘widget’ shortcut to the jar file in Kubuntu.

就像在Kubuntu中用'打开方式(open with)'的窗口来启动应用一样。你可以在Kubuntu中为jar文件创建一个桌面'小部件'。

That's it! Run Minecraft, it'll download what it needs, and go.

大功告成！运行我的世界(Minecraft)，它就会自动下载它需要的东西，然后开始。

I have it running at about 50 to 80 frames per second at 1024 X 768 resolution...on a 32 inch Toshiba TV! The 3D anaglyph is mind-blowing, by the way... I was afraid of the depth at first (heights make me nervous), and those holes into the bedrock gave me the willies!

我运行游戏时大约50到80帧每秒，用的是1024×768像素，32寸的东芝电视！3D立体效果令人兴奋，附带着说一句。。。我一开始对声音感到害怕(太大的声音让我紧张)，还有那些基石洞穴的声音令我毛骨悚然！

Your system may vary slightly or a great deal, but that's how I got mine going perfectly.

你的系统可能会略有不同或者差异很大，但至少在我这里它运行的很完美。

