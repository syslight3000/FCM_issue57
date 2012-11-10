---
layout: post
title: "57期 - Linux 实验室"
date: 2012-09-22 13:33
comments: true
categories: issue57 LINUX-LAB
---
 
#Mana World Server On Old Hardware
#在旧硬件上安装Mana World服务器

作者: Charles McColm
翻译：VinoCos
校对：Kitty


Traditionally our family has two periods of the year that we do a big cleanup - spring cleaning and at the start of a new year. This year, instead of tossing out our old Athlon64, I decided to reuse it as a development server for our existing MMORPG server. I first became aware of The Mana World (TMW) in late 2007 when the client software, tmw, appeared in the universe repositories of Ubuntu 7.10, Gutsy Gibbon. At the time, the TMW client was primitive but quite functional. Over the past several years, the game has advanced both on the client and server side.

我家里有每年要进行两次大扫除的传统：一次在春天，另一次是在新年的时候。不过今年我并不打算扔掉我那古董处理器Athlon64，而是要把它改造成家里已有的MMORPG游戏服务器的开发服务器。我第一次听说The Mana World (TMW)是07年末的事情了，当时tmw客户端软件出现在了Ubuntu 7.10，Gutsy Gibbon的通用库里。那时候的TMW还很简易不过相当好用。现在经过几年的发展，这个游戏在客户端和服务器方面都有了长足的进步。

The great thing about running a TMW server is that it doesn’t require a lot of horsepower if you plan on running a small server for friends and family. We originally set up our server on a Pentium III 1.1 GHz CPU with 256 MB of RAM (mind you the hard drives were lightning fast 15,000 RPM SCSI drives). This setup was enough to host 5 simultaneous players over the Internet on our ADSL connection. Currently, we host the Auldsbel server on a hyperthreaded Pentium 4 2.8 GHz system with 2 GB of RAM, and that also runs the front facing web server. Hosting a web server is helpful for getting the client software to show who else is online, but it’s not necessary to get the server running.

TMW服务器有一个非常棒的优点：你并不需要太多资源就可以运行一个给朋友和家人共享的小型服务器。我们本来把服务器搭建在了内存为256 MB且主频为1.1GHz的Pentium CPU上（不过硬盘可是快如闪电的15,000转SCSI硬盘）。这个系统足以供五个玩家同时在我们的ADSL网络里进行游戏。最近，我们在一个2GB内存的超线程Pentium 4 2.8 GHz系统上运行了一个Auldsbel服务器，上面也运行着web前端服务器。运行一个网络服务器可以帮助客户端软件显示还有哪些玩家在线，不过并非需要此服务器一直运行。

We used a server install of Ubuntu 10.04 LTS as the base for our server, and used a notebook running the client software to test the configuration. You may want to install the server on a desktop version of Ubuntu if you plan on using a single machine for the server and client. The TMW server is based on the eAthena (newer TMW server software exists that’s written from scratch, but the main server still uses modified eAthena code) project.

我们把安装了Ubuntu 10.04 LTS的服务器作为我们的基站服务器，并用一个笔记本运行客户端软件来测试它的配置。如果你想用一个机器来同时运行服务器和客户端，可以试着把服务器安装在Ubuntu的桌面版本上。TMW的服务器是基于eAthena（新版本的TMW服务器也有用scratch编写的，但主服务器依然使用修改过的eAthena编码）项目的。

eAthena was originally developed as an open-source server Ragnarok, but TMW developers have done a great job modifying it for the Mana World client. To begin, you need to install git-core, build-essential, flex, and bison:

eAthena原本是为Ragnarok的开源服务器开发的，不过TMW的开发人员对它做了漂亮地修改以将其用于Mana World客户端上。要开始配置TMW服务器，你需要先安装git-core、build-essential、flex和bison:

    sudo apt-get install git-core build-essential flex bison

Next you create a directory to hold the server software, and download and build the tmw-ea server software:

接下来，你需要创建一个文件夹来存放服务器软件并下载和运行TMW-EA服务器软件：

    mkdir ~/tmw-ea

    cd ~/tmw-ea

    git clone git://gitorious.org/tmw-eathena/mainline.git eathena

    git clone --recursive git://gitorious.org/+tmw-admins/tmw/tmwa-server-test.git eathena-data

    cd eathena

Be patient while git clones the repositories. Depending on which version of Ubuntu you’re running, you may run into problems with Make being older than version 3.82 (the version developers recommend you use to make the project). If you run into problems making the project, run the next step:

请耐心等待git复制资料库。根据你运行的Ubuntu版本的不同，可能会遇到一些低于3.82版本的Make（开发者推荐使用3.82版本来管理项目）而带来的问题。如果你在make项目时遇到了这些问题，执行下面的步骤：

    mkdir -p obj/{common,login,char,map,ladmin,tool}

    make

Multiple servers can be run from the same point, but the tmw-ea main server binaries should be copied to a standard folder:

你可以在同一处运行多个服务器，不过TMW-EA的主服务器文件必须被复制到一个标准文件夹里：

    sudo cp login-server char-server map-server ladmin /usr/local/bin/

The next step is to add git hooks to allow updating of the client data. Without this step, you’ll still be able to run the server software, you just won’t be able to pull updates from the git repositories.

下一步是添加git hooks来帮助客户端进行数据更新。若没有这一步，你仍然可以运行服务器软件，但是不能够从git数据库来更新本地仓库。

    cd ../eathena-data

    ln -s ../../git/hooks/post-merge .git/hooks/

    ln -s ../../../git/hooks/post-merge client-data/.git/hooks/

The last little bit of setup is to make the config files, and checkout client data and funky music:

最后，你需要make一下配置文件并checkout出客户端数据和那些有趣的音乐：

    cd client-data

    git checkout master

    cd music

    git checkout master

At this point, our server is set for us to log-in locally. I set up a static IP for the development server in our Tomato-MLPPP Linksys WRT54L router, and assigned it the same hostname I assigned the production system. Before we can test the server, we have to load 3 server processes: the character server, the login server, and the map server (the configuration files for these three servers are what we’ll modify later for an Internet facing server). For now we’ll load the server executables to test the server:

现在，我们的服务器已经可以本地登录了。在Tomato-MLPPP Linksys WRT54L路由器里我为这个开发服务器创建了一个静态IP地址，并给它分配了跟系统同样的主机名。在我们能够测试服务器之前，我们需要加载三个服务器进程：角色服务器，登录服务器和地图服务器（我们将会在后面为面向网络服务器调配这三个服务器的配置文件）。现在，我们就能加载服务器的可执行文件来测试服务器了：

    cd ~/tmw-ea/eathena-data

    ./char-server & ./login-server & ./map-server &


When you log in to the server for the first time, you’ll see the character log-in on the terminal you launch the server from. 

当你第一次登录服务器的时候，在启动服务器的终端里将看到角色登录。

From my notebook I loaded the TMW client:

我在笔记本上加载了TMW客户端：

    sudo apt-get install tmw

There are a number of TMW clients. The one in the Ubuntu 10.04 repository is a bit dated and freezes for GM’s when they entered a room where clients were logged in. Better to use the manaplus client available from http://manaplus.evolonline.org/ if you intend to expose your server to the rest of the world.

这里有很多不同的TMW客户端。Ubuntu 10.04数据库里的那个有点过时而且会在GM进入用户登录的房间时卡死。如果你打算在网上公开你的服务器，最好用http://manaplus.evolonline.org/ 里的manaplus客户端。

When the TMW client is loaded, click the Custom Server button, and enter the hostname you gave your server (or domain-name/dynamic DNS name). At this point, we’re just confirming the server is working locally and setting ourselves up to be GM - before exposing it to the rest of the world.

TMW客户端加载好以后，单击Custom Server按钮，并输入你给服务器设置的主机名（或者域名/动态DNS名）。这样，服务器在网络上公开之前我们就确认了它能在本地运行，同时也把自己设置为了GM。

When the client connects, click the register button. Note: you cannot register through the client if you intend to play on the official Mana World server. On the main server, you have to register through the web site, and wait for approval. On your own server you just register a username.

当客户端连接时，点击注册按钮。注意：如果你打算在官方Mana World服务器上游戏的话，就不能够通过这个客户端来注册。在主服务器上，你必须通过网页来注册，并且等待许可。在你自己的服务器上，你可以随意注册一个用户名。

The next screen is the character management screen where you choose a character. Since this is the first time you’ve logged on, all the character slots will be blank. Create a character and assign statistics on the next screen. You can also change hair color and hair style. As you might have guessed, one user login can have multiple characters.

下一个界面是角色管理界面，在这里你可以选择角色。因为这是你第一次登录游戏，所有的角色栏都将是空的。创建一个角色，并在下一个界面上分配数值。你也可以改变发型和头发颜色。跟你想的一样，一个登录用户可以拥有多个游戏角色。

You want to make sure you create a character before inviting anyone else to the server so you can set the first character to be the game master (GM). The TMW variation of eathena stores character data in ~/tmw-ea/eathena-data/login/save. The file account.txt stores character information. The file gm_accounts.txt is where you set up who will be GM on your server. GM’s and developers normally are assigned special levels. You can find these levels in the file ~/tmw-ea/eathena-data/world/map/conf/atcommand_local.conf. What’s important is that you set yourself up as a level 99 GM. If you assign other GMs set their level to 60 so they have limited GM power. The gm_accounts.txt file is formatted in the following fashion:

在你邀请其他玩家来这个服务器前，你得确认你已经创建了一个角色，这样你才可以设置第一个角色为游戏管理员（GM）。TMW版本的eAthena把角色资料存储在~/tmw-ea/eathena-data/login/save目录下。角色信息存储在名为account.txt的文件中，而gm_accounts.txt则是你用来管理GM的文件。GM和开发者的账号一般都被分配了特殊等级。你可以在~/tmw-ea/eathena-data/world/map/conf/atcommand_local.conf文件里找到这些等级。重要的一点是，把你自己设为99级的GM。这样，如果你给其他GM设置为60级，他们便会受限于GM。gm_accounts.txt文件的格式如下：

    account_number gm_level

The first user account is normally assigned a number of 2000000. Subsequent accounts increment the user account number by 1, so the next user account created would be 2000001. So to make the first user account GM we would give the gm_account.txt the following information:

第一个用户一般被分配2000000这个数字。接下来的账号号码则依次在原有数字上加1，所以下一个帐号将会是2000001。要将第一个用户设置为GM，你需要给gm_account.txt写入如下信息：

    20000000 99

The ~/tmw-ea/eathena-data/login/save/gm_accounts.txt file can be modified while you’re logged in to your server. Once you’ve given yourself GM level, you can try some of the GM commands. All GM commands begin with an @ symbol. @help will give you a list of GM commands in the debug tab. The keen-eyed will notice that many of the @gm commands scroll right off the screen. To correct this problem we need to adjust the amount of lines available in the chat window of the client software. In the top right corner of the tmw client software, click the Setup button, then click the chat tab, and adjust Limit max lines in chat to 120.

你可以在登录服务器时修改~/tmw-ea/eathena-data/login/save/gm_accounts.txt文件。一旦你给了自己GM级别后，便可以尝试使用一些GM的命令。所有的GM命令都以符号@开头。@help会在调试栏里显示GM的命令列表。眼尖的读者可能已经发现许多@gm命令在滚动到屏幕右边时就消失了。我们需要修改客户端软件聊天窗口中的显示行数来解决这个问题。点击客户端右上角的设置按钮，再选择聊天页面并调整最大行数上限到120。

GM’s have the power to create items, spawn monsters, warp to players, warp players to other places, even launch an all-out player versus player war, so choose your GMs carefully. GM actions are logged in a plain text file tmw-ea/eathena-data/world/map/gm.log.year.month (for example tmw-ea/eathena-data/world/map/gm.log.2012.01). We found that looking at the gm log files from the main server gave us a better understanding of the @gm commands and how they’re used. Luckily the main server is transparent with their log files, and they can be viewed online at http://server.themanaworld.org/gm.

GM的权限包括创建物品、孵化怪兽、转换玩家以及将玩家转移到其他地点，甚至发动一个全面PVP战争，所以一定要谨慎选择你的GM。GM的行为会被记录在tmw-ea/eathena-data/world/map/gm.log.year.month（比如 tmw-ea/eathena-data/world/map/gm.log.2012.01）这个文本文件里。阅读官方服务器的gm日志文件可以帮助我们更好地理解@gm命令以及它们的用法。官方服务器公开了他们的日志文件，你可以在http://server.themanaworld.org/gm 里阅读它们。


##Putting your server online

##把你的服务器放到网络上

In order to make your server available to everyone on the Internet, you’ll need to punch some holes in the firewall of your router. In particular, TCP and UDP for ports 5122, 6122, and 6901. You’ll also need to modify the configuration files for the server executables. There are a lot of configuration files, in a few places. The configuration files we want are all suffixed with _local.conf. In particular we want to modify the following files:

为了使你的服务器可以在网络上被其他用户使用，你需要在路由器的防火墙上凿开一些洞呢：尤其是TCP和UDP的端口5122，6122和6901。你还需要修改服务器执行文件的配置。这里有非常多的配置文件散布在不同的文件夹里，不过我们需要修改的文件都带有_local.conf后缀。下面就是我们需要修改的文件：

    ~/tmw-ea/eathena-data/world/conf/char_local.conf
    ~/tmw-ea/eathena-data/world/map/conf/map_local.conf
    ~/tmw-ea/eathena-data/login/conf/ladmin_local.conf

There are 3 variables we want to set, the IP addresses for the login server, the character server, and the map server. If you’re using a dynamic DNS service, the dynamic DNS name can be used in the place of the character and map server, but you should use your local address for the login server (on our test server we used 127.0.0.1 and it worked fine for the login server). Note that if your DNS changes while the server is online the server may be unavailable. Our ISP offers a very inexpensive static IP address, which is what we use in place of the character and map server variables. Our char_local.conf looks something like this:

在这儿我们需要设置3个变量：登陆服务器、角色服务器和地图服务器的IP地址。如果你采用动态获取DNS，也可以在角色和地图服务器里使用这个动态DNS，但你必须要用你的本地IP地址来设置登陆服务器（测试中，我们使用的是127.0.0.1本地回坏地址，在登录服务器上它运行良好）。需要注意的是，当你服务器在线时，如果改变DNS会让服务器挂掉的。我们的互联网提供商（ISP）提供了一个非常便宜的静态IP地址，所以我们可以把它用做角色和地图服务器的IP变量。我们的char_local.conf文件应该是这样的：

    // Comment : Login server IP
    login_ip: 127.0.0.1
    // Comment : Character server IP
    char_ip: auldsbel.dyndns.org

Similarly our map_local.conf looks like this:

同样的，我们的map_local.conf如下所示：

    // Character Server IP
    char_ip: auldsbel.dyndns.org
    // Map server IP
    map_ip: auldsbel.dyndns.org

The ladmin_local.conf file is an important configuration file used by the ladmin tool. Using ladmin, the administrator can execute a variety of administrative tasks without using the client to log in to the server.

ladmin_local.conf文件是一个用于ladmin工具的重要配置文件。通过ladmin，管理员可以在使用客户端登陆服务器的情况下执行多种管理任务。

You can find a number of other configuration files in the ~/tmw-ea/eathena-data/world/map/conf directory. If you want to have magic in your world, you’ll want to look at the magic.conf.template file and the build-magic.sh shell script. The help.txt file in this directory is the same help file that gets displayed to GMs who issue the @help command. You will also likely want to customize the motd.txt (message of the day) file.

你可以在~/tmw-ea/eathena-data/world/map/conf文件夹下找到许多其他的配置文件。如果你想在你的世界中使用魔法，可以看看magic.conf.template文件和build-magic.sh脚本。此文件夹里的help.txt文件与@help命令显示的内容是一样的。你还可以自定义motd.txt（今日公告message of the day）文件里的内容。

Like a lot of Linux software, the Mana World eAthena server is highly customizable. While you can run a server identical to the main server, you’ll probably want to customize your server more extensively. Good sources for information on further customization can be found on the Mana World forums, wiki, and in the How to Develop sections of the Mana World web site.

跟许多其他的Linux软件一样，Mana World eAthena服务器具有高的可自定义性。当你运行一个与官方服务器完全相同的服务器时，也许希望它能够变得更加丰富些。有关自定义客户端的资料可以在Mana World论坛，wiki和How to Develop sections of the Mana World网站中找到。

URLs of Interest:

有兴趣的读者可以看看这些链接：

The Mana World - http://www.themanaworld.org/
TMW Forums - http://forums.themanaworld.org/
TMW Wiki - http://wiki.themanaworld.org/
How to Develop (& server set-up) - http://wiki.themanaworld.org/index.php/How_to_Develop
Auldsbel TMW server: http://auldsbel.org/



Charles is a step-father, husband, and Linux fan who runs a not-for-profit computer refurbishing project. When not breaking hardware/servers he maintains a blog at [http://www.charlesmccolm.com/](http://www.charlesmccolm.com/).

Charles是一个和蔼的继父，体贴的丈夫，还是一位运营着一个非盈利电脑翻新项目的Linux系统的狂热粉丝。在硬件和服务器安好时，他还维护着一个博客[http://www.charlesmccolm.com/](http://www.charlesmccolm.com/)。
