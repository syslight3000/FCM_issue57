---
layout: post
title: "57期 - 决胜命令行"
date: 2012-09-22 13:33
comments: true
categories:  issue57 command-and-conquer
---

#Using SSH And Rsync
#使用SSH和Rsync
Written by Lucas Westermann

`Lucas Westermann 著 翻译：黄傲妮 校对：Kitty`

Back in issue #37, I wrote about configuring an SSH server on your computer, in order to use it as a SOCKS proxy. Since I imagine not all that many people want to use it as such, I decided to focus on my second-most used command (my first-most used command is “pacman” - ArchLinux's solution to package management). Before I get into what that command is, I'll briefly explain why you might be interested in this solution. Specifically, it lets you sync directories and files between two computers over the LAN (and, if properly configured, over the Internet as well). I use it in order to keep my music synced between my laptop and my PC, keep my configuration files up-to-date, and to copy anything I need from one device to the other. There are a few choices of commands you could use, two of which would be scp (secure copy), and rsync. I'll be focusing on rsync in this article, because it offers progress information, update features, and useful switches like --ignore-existing.

早在37期，我就写了一篇文章关于如何在你自己的电脑上配置一个SSH服务器，目的是为了能够将SSH用作SOCKS代理。而我觉得不是每个人都想那样去用它，所以决定把重点放在第二个我常用的命令上（第一个我最常使用的命令是“pacman”— ArchLinux的包管理的解决方案）。在告诉你这个命令是什么玩意儿之前，我会先简要解释一下为什么你将会对此方案感兴趣。明确地说，它可以让你在局域网中同步两台电脑上的目录和文件（而且，如果配置正确的话，也可以在互联网中实现）。我使用它是为了同步我的笔记本和PC上的音乐、持续更新我的配置文件，而且还能随我需要将任何东西从一台设备拷贝到另一台上。这儿有几个命令供你选择，其中两个就是scp(安全拷贝)和rsync。此篇文章，我们将重点关注rsync，因为它提供了进度信息、更新特性，以及有用的开关，比如--ignore-existing。

A few of you may be asking why I don't just use Dropbox, an external hard drive, or a USB stick (for smaller files). The answer is quite simple: Dropbox offers a limited amount of space, and the other options require me to remember to do this regularly. If you have SSH configured on your “sender” (in this case, my PC from which I transfer the files), and an SSH client (no server required) on your “receiver” (my laptop, in this case), then you can easily write a small script to run a cron (in other words, regularly, and without any input). If you want to automate this, you will need to configure SSH to use keys instead of passwords, so that you can access your server without having to input anything. This is fairly simple (using ssh-keygen to create the keys, and then copying the public key to the server), and is explained in plenty of places (see the Links section below for a link to a Wiki).

你可能会问我为什么不使用Dropbox、硬盘，或者U盘（针对较小的文件）？答案很简单：Dropbox提供的空间数量有限，而其他两者需要我定期做备份。如果在你的“发送端”（此例中，我的PC是发送端）上已经配置好SSH，而在“接收端”（我的笔记本）上有一个SSH客户端（没有服务器请求），然后你就可以写一个简单的脚本去运行cron例程了（也就是说，通常不需要任何输入了）。如果想自动化这些东西，你就需要用密钥代替密码来配置你的SSH，如此一来就不需要任何的输入即可访问你的服务器。这个非常简单（用ssh-keygen去创建这个密钥，然后将公共密钥复制到服务器上），更多详情见本文后的链接。

Once you have SSH configured, it's time to think about how the script should appear. I won't supply an example script, simply because I haven't implemented a decent one yet. There are some things you should take into consideration when designing your script, such as:
The script should only do something if you're on your home network (this can be done by checking the ESSID of your wireless, or, if you connect your laptop to the LAN by cable when at home, checking if eth0 is active, or simply deciding on a specific time the script should run). The reason for this is because otherwise you'll have lots of failed SSH connections when doing this in a location besides your home network. I recommend thinking about your habits, and finding a solution that works best for you. Then write it into an if-statement in the script.

一旦你配置了SSH，就该考虑一下这个脚本应如何显示了。我没办法提供一个示例脚本，因为我还没有执行过一个像样点的脚本。在设计脚本的时候，你应该考虑一些东西，比如：
这个脚本应该只用于你使用家庭网络的时猴（通过检查无线网络的ESSID，如果在家里你通过连接线将你的本本链接到局域网，请检查eth0是否被处于激活状态，或者仅仅考虑在某个特定时间运行此脚本）。这样做的原因是，除了你的家庭网络，在某一位置时可能会有很多失败的SSH链接。不过还是按照你自己的喜好，寻找一种适合自己的解决方案吧。最后把它写进这个脚本的if语句中。

How many files/directories do you want to sync, and which ones exactly? You can either hard-code each file or directory into the script, or create a text-based list of locations on your machines, and then use a while statement and readline to handle each line separately. A few files I would recommend: .bashrc (or your rc file for the shell you use), .Xdefaults (for terminal colors), Music, Pictures, any configuration files for window managers (XMonad, DWM, etc.)

你想同步多少文件/目录，哪一个才是你想要的呢？你要么硬编码每个文件或目录到这个脚本中，要么在你机器上创建一个基于文本列表的位置存储信息，然后用一个while语句和readline去处理文本行。我推荐几个文件：.bashrc（或者用shell的rc文件）、.Xdefaults（可配置终端颜色）、音乐、图片，以及窗口管理的各种配置文件（XMonad、DWM等等。）。

Do you want to update (meaning newest copies of the files are the ones to keep), or ignore files if they already exist on the receiver (useful for music and pictures), do you need to be recursive (that means following a directory tree). There are some other useful options to consider that rsync offers (see the second section of this article).

你需要更新（即需要保留最新的文件备份），或者忽略在接收端已经存在的文件（对于音乐文件和图片来说很有用）吗？你需要递归查找文件（在一颗目录树下）吗？rsync就提供了一些其他有用的选项（见本文第二部分）。

Is the destination folder and the source folder in the same location? If not, you'll need to keep track of where each file is supposed to go (similar to #2).

目标文件夹和资源文件夹在同一个地方吗？如果没有，你就应该记录每个文件的去向（同第二部分）。

Space – do you have enough space on your receiver for all the files from your sender, and, if not, what are you going to do about it? You can either reduce your list of sync files, or build a check into the script using df -h to set a limit (i.e. if there are only 9GB left, stop syncing entirely, and email you/prompt you).

空间——在接收端上有足够的空间放置你所有来自发送端的文件吗？如果没有，你要怎么办？要么减少你所同步的文件清单，要么在脚本增加一个检查点，用df -h设置一个限制范围（也就是说如果只剩余9GB，则停止同步，同时发邮件或者给与你提示）。

Once you've taken these points into consideration, it's time to write the script. I recommend you have at least 2 checks in the script (if you're connected to the right network, and if the sender is currently online). The rest of the script is entirely up to you, including when and how to run it. Back in issue #24, I wrote an article on cron, and since then have used plenty of examples, so I will only briefly discuss your options. When configuring the cron job, you can either dump the script in /etc/cron.hourly, or /etc/cron.daily. The other option is to edit your crontab (crontab -e <username>). In the crontab you can then create a line for the script that either runs every set number of hours/days, or set it to run at a specific time (or a specific date), and so on. I think a script that runs once a day is going to be quite enough for this.

如果你已经考虑到了这些点，那么就该写脚本了。我建议在你的脚本中至少要有两项检查（网络连接是否正确，以及发件人当前是否在线）。脚本剩余部分完全由你决定，包括什么时候以及怎样运行它。想想在24期中，我写的那篇关于cron的文章，在那时我已经列举了大量例子，因此在这里我只简单说一下可供你用的选择。配置cron任务时，你可以将脚本转储在/etc/cron.hourly，或者/etc/cron.daily下。另一种选择是编辑你的crontab（crontab -e <username>）。在crontab中你可以创建一行例程，让脚本在设置的小时/日子运行，或者设置它某个特定的时间（也可以使某个特定的日期）运行等等。我觉得到每天运行一次就已经足够了。

##rsync

As you can see from point 3 above, rsync offers a lot of checks to avoid copying more files than necessary. Some useful ones are:
正如你从上述3点所看到的，rsync为避免复制过多的文件而提供了大量检查。以下是一些有用的命令参数：

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

    -u (--update): 跳过接收端上较新的文件
    --inplace: 原位更新文件 
    --append: 在较短的文件末添加数据
    -x: 避免越过文件系统界限（即坚持一个分区）
    --existing: 不在接收端上创建一个新的文件，仅仅更新已存在的文件
    --ignore-existing: 忽略接收端已存在的文件
    --max-size=SIZE: 不复制任何比此文件大的文件（--min-size 也存在，尽管在这种情况下用处不大）
    --exclude=PATTERN: 排除与此模式匹配的所有文件
    --exclude-from=FILE: 从文件读取模式
    --partial: 保留部分复制的文件

Some other useful switches for rsync:

    --delay-updates: Puts updated files into place at the very end.
    -r (--recursive): Follows directory trees.
    -d: Copy directories without recursing (by default rsync doesn't enter any directory at all)
    -l (--links): Copy symlinks as symlinks
    -E (--executability): Keep files executable (useful for scripts)
    -h: Human-readable sizes and output
    --progress: Display a progress bar for each file

rsync其他一些有用的开关：

    --delay-updates: 将更新的文件放在最后
    -r (--recursive): 依随目录树
    -d: 非递归复制目录（默认情况下rsync根本不进入任何目录）
    -l (--links): 复制符号连接作为符号连接
    -E (--executability): 保持文件的可执行性（对脚本有用）
    -h: 大小和输出的可读性
    --progress: 每个文件都显示进度条


For the full list, check rsync's manpage.

欲得完整的列表，请查看rsync的帮助手册。

The basic format for rsync commands is:

rsync命令的基本格式是：

    rsync <switches> <source> <destination>


So, if I wanted to update all files from ~/scripts on my PC with ~/.bin on my laptop, I'd write:

因此，如果我想更新PC机上~/scripts到笔记本上~/.bin里所有文件的话，我会写：

    rsync -ru lswest@127.0.0.1:/home/lswest/scripts ~/.bin

This will then copy it over. Logically, you'll want to use the actual IP of your PC instead of the localhost IP, but this is only an example.

这样就会将它复制过来了。从逻辑上讲，你将需要用PC机的真实IP代替本地主机的IP，但这仅仅是一个例子。

As we round off this article, I'd like to make a few notes on off-site syncing: Syncing over the Internet, while useful, should be kept to a minimum, simply because the traffic, while encrypted, will be rather large, and might cause issues with an admin, or any kind of data limit you might have. Also, ssh keys are (generally) more secure than passwords, so I highly recommend using them wherever possible.

为了圆满结束这篇文章，我想做几点syncing之外的笔记：在互联网上同步，虽然有用，但是应该保持一个最低限度，这仅仅是因为网络流量；虽然加密，但是将会相当庞大，还可能造成管理问题，又或者你可能会碰到一些数据的限制。再者，ssh密钥比密码更安全，所以无论如何我强烈推荐你使用它们。

If there is a large influx of requests for an actual example script, I will happily deliver it next month. I do, however, recommend you try writing your own, or customize any example scripts you find to suit your needs. If you're of the opinion you'd like one, please let me know in an email (address is below). If you have some concrete questions about a script you're writing yourself, you're also welcome to email me about it.

如果大家对真实的样例脚本有大量请求，我会很乐意在下个月递送。然而，我建议你尝试写自己的，或者定制任何适合你需求的例子脚本。如果你确实想要一个示例脚本，请发邮件让我知道（地址在下方）。如果你自己的脚本有具体问题，也可以发邮件给我。

If anyone has questions, concerns, or simply wants to share a script they've implemented, feel free to email me at lswest34@gmail.com. If you do email me, remember to include C&C or FCM in the title, so that I don't overlook it.

任何人有问题、忧虑，或者仅仅想分享已经实现的脚本，我的邮箱全天候等待lswest34@gmail.com。如果你发邮件给我，记得在标题中包含C&C和FCM，以便于我不会忽视它。

Links: https://wiki.archlinux.org/index.php/SSH_Keys#Generating_an_SSH_key_pair>

链接：https://wiki.archlinux.org/index.php/SSH_Keys#Generating_an_SSH_key_pair>
