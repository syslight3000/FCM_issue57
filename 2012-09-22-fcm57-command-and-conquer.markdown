---
layout: post
title: "57期 - 决胜命令行"
date: 2012-09-22 13:33
comments: true
categories:  issue57 command-and-conquer
---

<!--翻译：黄傲妮（我添加的注释适当的可以删掉的哦!我翻译的可能有些问题，辛苦一校了。）-->
Using SSH And Rsync
<!--SSH(注:专为远程登录会话和其他网络服务提供安全性的协议)和Rsync(注:Unix下的一款应用软件，它能同步更新两处计算机的档案与目录，并适当利用差分编码以减少数据传输。)的用法-->

Written by Lucas Westermann
<!--Lucas Westermann著-->

Back in issue #37, I wrote about configuring an SSH server on your computer, in order to use it as a SOCKS proxy. Since I imagine not all that many people want to use it as such, I decided to focus on my second-most used command (my first-most used command is “pacman” - ArchLinux's solution to package management). Before I get into what that command is, I'll briefly explain why you might be interested in this solution. Specifically, it lets you sync directories and files between two computers over the LAN (and, if properly configured, over the Internet as well). I use it in order to keep my music synced between my laptop and my PC, keep my configuration files up-to-date, and to copy anything I need from one device to the other. There are a few choices of commands you could use, two of which would be scp (secure copy), and rsync. I'll be focusing on rsync in this article, because it offers progress information, update features, and useful switches like --ignore-existing.
<!--为了能够像使用SOCKS（注：一种网络传输协议，主要用于客户端与外网服务器之间通讯的中间传递）代理一样使用SSH，早在37期，我就写了如何在你自己的电脑上配置一台SSH服务器。因为我觉得不是每个人都想那样去使用它，所以我决定把重点放在第二个我常用的命令上（第一个我最常使用的命令是“pacman”— ArchLinux的包管理的解决方案）。之前我一直在想这个命令到底是什么，我会给你解释为什么你会对此方案感兴趣。具体来说，它可以让你在局域网中同步你的两台电脑上的目录和文件（而且，如果配置正确的话，也可以在互联网中实现）。我使用它是为了保持我的音乐同步到我的笔记本和PC上，保持我的配置文件最新，另外我可以从一个设备到另一个设备拷贝任何我需要的。你可以使用几种可供选择的命令，其中两个是scp(安全拷贝)和rsync。这篇文章的重点说的就是rsync，因为它提供了进度信息，更新特征，以及有用的开关像（注：这里翻译的“开关像”不太确定。）——忽视－存在。-->

A few of you may be asking why I don't just use Dropbox, an external hard drive, or a USB stick (for smaller files). The answer is quite simple: Dropbox offers a limited amount of space, and the other options require me to remember to do this regularly. If you have SSH configured on your “sender” (in this case, my PC from which I transfer the files), and an SSH client (no server required) on your “receiver” (my laptop, in this case), then you can easily write a small script to run a cron (in other words, regularly, and without any input). If you want to automate this, you will need to configure SSH to use keys instead of passwords, so that you can access your server without having to input anything. This is fairly simple (using ssh-keygen to create the keys, and then copying the public key to the server), and is explained in plenty of places (see the Links section below for a link to a Wiki).
<!--你可能会问我为什么不仅仅使用Dropbox，一个外部硬盘，或者一个USB存储（较小的文件）。答案很简单：Dropbox提供数量有限的空间，另外有一些其他的选项要求我得记得定期做。如果在你的“发件器”（在这中情况下，我可以从我的PC机上转移文件）上有SSH配置，而且在“收件器”（在这种情况下，我的电脑）上有一个SSH客户端（没有服务器需求），然后你就可以写一个简单的脚本去运行cron（换句话说，大体上，没有任何输入）。如果想让它自动执行，那你就需要用密钥而不是密码来配置你的SSH，如此一来你就不需要任何的输入就可以访问你的服务器。这是非常简单的（用ssh-keygen去创建这个密钥，然后将公共密钥复制到服务器上），并且在很多地方都有解释（以下部分有一个Wiki链接）。-->

Once you have SSH configured, it's time to think about how the script should appear. I won't supply an example script, simply because I haven't implemented a decent one yet. There are some things you should take into consideration when designing your script, such as:
The script should only do something if you're on your home network (this can be done by checking the ESSID of your wireless, or, if you connect your laptop to the LAN by cable when at home, checking if eth0 is active, or simply deciding on a specific time the script should run). The reason for this is because otherwise you'll have lots of failed SSH connections when doing this in a location besides your home network. I recommend thinking about your habits, and finding a solution that works best for you. Then write it into an if-statement in the script.
<!--一旦你配置了SSH，就该考虑一下这个脚本应如何显示了。我没办法提供一个示例脚本，因为我还没有执行过一个像样点的脚本。在设计脚本的时候，有一些你应该考虑的，比如：
如果你用的是你家里的网络，这个脚本就只能做一些事（通过检查你的无线网ESSID这是可以被做到的，或者，如果在家里你可以通过电缆把你的电脑链接到局域网，检查eth0是否是活跃的，或者仅仅决定一个脚本应该运行的特别的时间）。这样做的原因是，在某一位置当你做这个时候你会有很多失败的SSH链接，除了你的家庭网络。我建议你考虑一下你平时的习惯以及找一种最适合你的解决方案。然后把它写进这个脚本的if语句中。-->

How many files/directories do you want to sync, and which ones exactly? You can either hard-code each file or directory into the script, or create a text-based list of locations on your machines, and then use a while statement and readline to handle each line separately. A few files I would recommend: .bashrc (or your rc file for the shell you use), .Xdefaults (for terminal colors), Music, Pictures, any configuration files for window managers (XMonad, DWM, etc.)
<!--你想同步多少文件／目录，其中哪一个是确切的呢？你要么硬编码每个文件或目录到这个脚本，要么在你机器上创建一个存储单元的基于文本的列表，然后用一个while语句和readline使每一行都分开。我推荐几个文件：.bashrc（或者你是用的shell的rc文件），.Xdefaults（终端颜色），音乐，图片，窗口管理的各种配置文件（XMonad，DWM，等等。）-->

Do you want to update (meaning newest copies of the files are the ones to keep), or ignore files if they already exist on the receiver (useful for music and pictures), do you need to be recursive (that means following a directory tree). There are some other useful options to consider that rsync offers (see the second section of this article).
<!--如果它们已经在接收器中你想更新（意味着最新的文件副本是仍然保持），或者忽视文件（对于音乐和图片来说是有用的）吗，你需要递归（这意味着一颗目录树）吗。还有一些rsync提供的有用的选项（见本文第二部分）。-->

Is the destination folder and the source folder in the same location? If not, you'll need to keep track of where each file is supposed to go (similar to #2).
<!--目标文件夹和资源文件夹在同一个地方吗？如果没有，你就应该保持跟踪每个文件的去向（较小的去#2）。-->

Space – do you have enough space on your receiver for all the files from your sender, and, if not, what are you going to do about it? You can either reduce your list of sync files, or build a check into the script using df -h to set a limit (i.e. if there are only 9GB left, stop syncing entirely, and email you/prompt you).
<!--空间——在你的接收器上有足够的空间放置所有来自发件器的文件吗，如果没有，你要做什么?或者减少你的同步文件清单，或者建立一个查看脚本用df -h设置一个限制（即，如果只有9GB，完全停止同步，并且发邮件给你或者提示你）。-->

Once you've taken these points into consideration, it's time to write the script. I recommend you have at least 2 checks in the script (if you're connected to the right network, and if the sender is currently online). The rest of the script is entirely up to you, including when and how to run it. Back in issue #24, I wrote an article on cron, and since then have used plenty of examples, so I will only briefly discuss your options. When configuring the cron job, you can either dump the script in /etc/cron.hourly, or /etc/cron.daily. The other option is to edit your crontab (crontab -e <username>). In the crontab you can then create a line for the script that either runs every set number of hours/days, or set it to run at a specific time (or a specific date), and so on. I think a script that runs once a day is going to be quite enough for this.
<!--一旦你已经考虑到这些点，那么该写脚本了。我建议你在脚本中至少有两项检查（网络连接是否正确，还有发件人当前是否在线）。脚本剩余部分完全由你决定，包括什么时候以及怎样运行它。想想在24期中，我写了一篇关于cron的文章，而在那时我已经用了大量例子，因此在这里我就简单说一下你的选择。配置cron工作时，你可以转储脚本在/etc/cron.hourly，或者/etc/cron.daily下。另一种选择是编辑你的crontab（crontab -e <username>）。在crontab中你可以创建一行脚本或者运行每一小时／天设置一次行数，或者设置它在一个特定的时间（或者某个特定的日期）运行，等等。我认为每天运行一次已经足够了。-->

rsync
<!--rsync（注：Unix下的一款应用软件，它能同步更新两处计算机的档案与目录，并适当利用差分编码以减少数据传输。）-->

As you can see from point 3 above, rsync offers a lot of checks to avoid copying more files than necessary. Some useful ones are:
<!--正如你从上述3点所看到的，rsync为了避免复制过多的文件提供了大量检查。以下是一些有用的例子：-->

    -u (--update): Skips files that are newer on the receiver
    --inplace: updates files in-place
    --append: adds data on to the ends of shorter files
    -x: Avoid crossing filesystem boundaries (i.e. stick to one partition)
    --existing: Do not create new files on the receiver, only update existing files
    --ignore-existing: Ignore files that already exist on receiver
    --max-size=SIZE: Don't copy any files larger than this (--min-size also exists, though less useful in this case)
    --exclude=PATTERN: Excludes any file matching the pattern
    --exclude-from=FILE: Reads the pattern(s) from the file
    --partial: Keep partially copied files
<!--
-u (--update): 跳过接收器上较新的文件
--inplace: 原位更新文件 
--append: 较短的文件两端添加文件
-x: 避免越过文件系统界限（即，坚持一个分区）
--existing: 不要在接收器上创建一个新的文件，仅仅更新已存在的文件。
--ignore-existing: 忽略接收器已存在的文件
--max-size=SIZE: 不要复制任何比这大的文件（--min-size 也存在，尽管在这种情况下用处不大）
--exclude=PATTERN: 排除任何文件匹配模式
--exclude-from=FILE: 从文件读取模式
--partial: 保留部分复制的文件
-->

Some other useful switches for rsync:

    --delay-updates: Puts updated files into place at the very end.
    -r (--recursive): Follows directory trees.
    -d: Copy directories without recursing (by default rsync doesn't enter any directory at all)
    -l (--links): Copy symlinks as symlinks
    -E (--executability): Keep files executable (useful for scripts)
    -h: Human-readable sizes and output
    --progress: Display a progress bar for each file
<!--
rsync的其他一些有用的转换：

--delay-updates: 把更新的文件放在最后
-r (--recursive): 如下目录树
-d: 非递归复制目录（默认的rsync根本不进入任何目录）
-l (--links): 复制符号连接作为符号连接
-E (--executability): 保持文件可执行（有用的脚本）
-h: 人类可读的大小和输出
--progress: 为每个文件显示进度栏
-->

For the full list, check rsync's manpage.
<!--完整的列表，检查rsync的手册。-->

The basic format for rsync commands is:
<!--rsync命令的基本格式是：-->

    rsync <switches> <source> <destination>


So, if I wanted to update all files from ~/scripts on my PC with ~/.bin on my laptop, I'd write:
<!--因此，如果我想更新我的PC机上~/scripts和我的笔记本上的~/.bin中的所有文件的话，我会写：-->

    rsync -ru lswest@127.0.0.1:/home/lswest/scripts ~/.bin

This will then copy it over. Logically, you'll want to use the actual IP of your PC instead of the localhost IP, but this is only an example.
<!--然后将它复制过来。从逻辑上讲，你想用你的PC机的实际IP代替本地主机IP，但这仅仅是一个例子。-->

As we round off this article, I'd like to make a few notes on off-site syncing: Syncing over the Internet, while useful, should be kept to a minimum, simply because the traffic, while encrypted, will be rather large, and might cause issues with an admin, or any kind of data limit you might have. Also, ssh keys are (generally) more secure than passwords, so I highly recommend using them wherever possible.
<!--为了圆满结束这篇文章，我想做几点syncing之外的笔记：
在互联网上同步，虽然有用，但是应该保持一个最低限度，仅仅因为交通，虽然加密，但是将是相当庞大，而且可能造成管理问题，或者你可能有任何种类的数据限制。再者，ssh键比密码跟安全，所以无论如何我强烈推荐使用他们。
-->

If there is a large influx of requests for an actual example script, I will happily deliver it next month. I do, however, recommend you try writing your own, or customize any example scripts you find to suit your needs. If you're of the opinion you'd like one, please let me know in an email (address is below). If you have some concrete questions about a script you're writing yourself, you're also welcome to email me about it.
<!--如果有真实例子脚本的大量请求，我会很乐意在下个月提供它。然而，我建议你尝试写自己的，或者定义任何适合你的需求的例子脚本。如果你有你的观点，请发邮件让我知道（地址如下）。如果你自己的脚本有具体问题，你也可以发邮件给我。-->

If anyone has questions, concerns, or simply wants to share a script they've implemented, feel free to email me at lswest34@gmail.com. If you do email me, remember to include C&C or FCM in the title, so that I don't overlook it.
<!--如果任何人有问题，忧虑，或者仅仅想分享已经实现的脚本，我的邮箱任何时候为你开放lswest34@gmail.com。如果你发邮件给我，记得在标题中包含C&C和FCM，以便于我不会忽视它。-->

Links: https://wiki.archlinux.org/index.php/SSH_Keys#Generating_an_SSH_key_pair>
<!--链接：https://wiki.archlinux.org/index.php/SSH_Keys#Generating_an_SSH_key_pair>-->
