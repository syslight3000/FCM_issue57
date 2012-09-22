---
layout: post
title: "57期 - Closing Windodws 网络与无线网络设置"
date: 2012-09-22 13:34
comments: true
categories: issue57 closing-windows
---

`Written by:`

`Ronnie Tucker (KDE)`

`Jan Mussche (Gnome)`

`Elizabeth Krumbach (XFCE)`

`Mark Boyajian (LXDE)`

`David Tigue (Unity)`

Examining your network or wireless settings in Windows is actually quite confusing, not to mention intimidating. You can see them by going to the Control Panel and choosing Network Connections. What you see isn’t exactly user friendly, but I suppose it does the job.<!-- 在Windows中检查你的网络或无线网络设置实在让人很困惑，更不用说让人感到害怕了。你可以在控制面板中选择网络连接来查看网络或无线网络设置。虽然你看到的东西对用户而言并不友好，但我觉得那些足够了。-->

### Kubuntu:<!--Kubuntu：-->

The network and wireless settings (above) are available through the System Settings window, but a quick short-cut (and a better way to manage it) is the icon in your taskbar (far right) that looks like a network plug and socket. Clicking that gives you quick access to not only your settings, but also to find which wireless networks are available to you. <!--上面提到的网络与无线网络设置可以通过系统设置窗口获得，但在你的任务栏最右边有一个快速启动项，(它同时也是一个很好的管理网络与无线网络设置的方法)它看起来有些像一个网络插头和一个网络插口。点击它后你不仅能对网络和无线网络进行快速设置，还能查看有哪些无线网络可用。-->

### Gnome-Shell:<!--Gnome-Shell：--> 

The Gnome-Shell version does not have such a nice settings-screen .The screens to set and change the network connections look like this:<!--在Gnome-Shell版本中并没有这样一个漂亮的设置界面。设置和改变网络连接的界面是这样的：-->

The settings can be found at: System > Preferences > Network Connections, but also top right in the panel. Here you see an icon with two anti-parallel arrows. Click the icon > Edit Connections. A third way is through the Control Center (System Settings) - which can be found in the drop menu connected to the Shutdown button at the top-right on your screen. <!-- 设置通过下面的方式获得：System （系统）> Preferences（首选项） > Network Connections（网络连接），但它也位于面板的右上角。这里你看到一个带有两个反向平行箭头的图标。点击图标选择编辑连接。第三种方式就是通过控制中心（系统设置）获得，它位于屏幕右上角的关机按钮的下拉菜单中。-->

To change a connection, click the name of the connection > Edit button. You will now see a new window with 4 TABs. Of these 4 TABs, 1 is important and that is the ‘IPv4 Settings’ tab - where you select how your connection needs to operate. The most common way is to select Automatic (DHCP). This can be done when your computer makes contact with a router with a build-in DHCP server. The DHCP (Dynamic Host Control Protocol) server generates IP-addresses for all connected computers (which are set to Automatic-DHCP). As can be seen in the next picture, you don’t need to set anything (Address, Netmask, Gateway, DNS server, and Search domain) yourself, just let the system handle this.<!--如果要改变连接，点击连接的名称，按下编辑按钮。你会看到你一个带有4个标签页的新窗口。这4个标签页中，第一个很重要，它是‘IPv4 Settings’ 标签页，你从中选择你的连接需要如何操作。最通用的方法就是选择自动(DHCP)。在你的电脑同一个带有内置DHCP服务器的路由器进行连接时，此法是可行的。DHCP（自动域名控制服务）服务器为所有已连接的设置了自动DHCp的计算机提供IP地址。在下张图片中可以看到，你不必做任何设置（地址，子网掩码,网关，DNS服务器，搜索域名），就让系统自行处理就是了。-->

For a wireless connection, after setting things straight, you still need to make contact with your wireless network. For this, right-click the network icon in the top panel, and choose the network you want to connect to. If it is a secure network, type the password you’ve assigned, and you should be connected in seconds.<!-- 对于无线连接，在你设置后，你仍需要连接你的无线网络。你需要右键点击顶部面板上的网络图标，选择你想要连接的网络。如果它是一个有安全机制的网络，输入分配给你的密码后，你会马上连上该网络。-->

### Xubuntu:<!--Xubuntu：--> 

Xubuntu uses the nm-connection-editor from Gnome, it is available for launching through Settings > Network Connections, or by right-clicking on the network indicator icon in the top panel and selecting “Edit Connections...”. However, for basic wireless setup, you will want to right-click on the network indicator icon in the top panel, and simply select the wireless network you wish to connect to. <!-- Xubuntu使用Gnome中的nm连接编辑器，你可以通过点击Settings（设置） > Network Connections（网络连接）或者通过右键点击顶部面板上的网络指示器选择“Edit Connections...”（编辑连接）来启动它。但是，对于无线网络的初级设置你需要右键点击顶部面板上的网络指示器，然后选择你想要连接的无线网络即可。-->

### Lubuntu:<!--Lubuntu：-->

Settings are made in the same way as described for Gnome-Shell; however, opening the Network Connections window is, not surprisingly, done differently. The easiest way is to click on the network icon in the Panel; by default it’s on the right-hand side.<!--在Lubuntu中进行设置和在Gnome-Shell中描述的一样；但网络连接窗口的打开方法不一样。最简单的办法就是点击面板上的网络图标，它默认位于面板的右侧。-->
                
Alternatively, you can access it through the main menu by clicking System Tools > Lubuntu Control Center.<!--另外，你也可以通过点击System Tools （系统工具）> Lubuntu Control Center（Lubuntu控制中心）打开的主菜单来进行设置。-->

From the Control Center, click the Network icon.<!--点击控制中心的网络图标。-->

Once in the Network Connections window, you configure your network settings for Wired and Wireless (and other) connections as described for Gnome-Shell or Ubuntu.<!--在网络连接窗口中，你可以像在Gnome-Shell和Ubuntu中描述的一样来配置有线和无线（还有其他方式）连接的设置。-->

Next month we'll discuss the formatting of media such as USB sticks, hard drives and SD cards.<!--下个月我们将讨论介质（比如U盘，硬盘和CD光盘的格式化。-->
