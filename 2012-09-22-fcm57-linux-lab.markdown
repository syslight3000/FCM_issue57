---
layout: post
title: "57期 - Linux 实验室"
date: 2012-09-22 13:33
comments: true
categories: issue57 LINUX-LAB
---

Mana World Server On Old Hardware

Written by Charles McColm

Traditionally our family has two periods of the year that we do a big cleanup - spring cleaning and at the start of a new year. This year, instead of tossing out our old Athlon64, I decided to reuse it as a development server for our existing MMORPG server. I first became aware of The Mana World (TMW) in late 2007 when the client software, tmw, appeared in the universe repositories of Ubuntu 7.10, Gutsy Gibbon. At the time, the TMW client was primitive but quite functional. Over the past several years, the game has advanced both on the client and server side.

The great thing about running a TMW server is that it doesn’t require a lot of horsepower if you plan on running a small server for friends and family. We originally set up our server on a Pentium III 1.1 GHz CPU with 256 MB of RAM (mind you the hard drives were lightning fast 15,000 RPM SCSI drives). This setup was enough to host 5 simultaneous players over the Internet on our ADSL connection. Currently, we host the Auldsbel server on a hyperthreaded Pentium 4 2.8 GHz system with 2 GB of RAM, and that also runs the front facing web server. Hosting a web server is helpful for getting the client software to show who else is online, but it’s not necessary to get the server running.

We used a server install of Ubuntu 10.04 LTS as the base for our server, and used a notebook running the client software to test the configuration. You may want to install the server on a desktop version of Ubuntu if you plan on using a single machine for the server and client. The TMW server is based on the eAthena (newer TMW server software exists that’s written from scratch, but the main server still uses modified eAthena code) project.

eAthena was originally developed as an open-source server Ragnarok, but TMW developers have done a great job modifying it for the Mana World client. To begin, you need to install git-core, build-essential, flex, and bison:

    sudo apt-get install git-core build-essential flex bison

Next you create a directory to hold the server software, and download and build the tmw-ea server software:

    mkdir ~/tmw-ea

    cd ~/tmw-ea

    git clone git://gitorious.org/tmw-eathena/mainline.git eathena

    git clone --recursive git://gitorious.org/+tmw-admins/tmw/tmwa-server-test.git eathena-data

    cd eathena

Be patient while git clones the repositories. Depending on which version of Ubuntu you’re running, you may run into problems with Make being older than version 3.82 (the version developers recommend you use to make the project). If you run into problems making the project, run the next step:

    mkdir -p obj/{common,login,char,map,ladmin,tool}

    make

Multiple servers can be run from the same point, but the tmw-ea main server binaries should be copied to a standard folder:

    sudo cp login-server char-server map-server ladmin /usr/local/bin/

The next step is to add git hooks to allow updating of the client data. Without this step, you’ll still be able to run the server software, you just won’t be able to pull updates from the git repositories.

    cd ../eathena-data

    ln -s ../../git/hooks/post-merge .git/hooks/

    ln -s ../../../git/hooks/post-merge client-data/.git/hooks/

The last little bit of setup is to make the config files, and checkout client data and funky music:

    cd client-data

    git checkout master

    cd music

    git checkout master

At this point, our server is set for us to log-in locally. I set up a static IP for the development server in our Tomato-MLPPP Linksys WRT54L router, and assigned it the same hostname I assigned the production system. Before we can test the server, we have to load 3 server processes: the character server, the login server, and the map server (the configuration files for these three servers are what we’ll modify later for an Internet facing server). For now we’ll load the server executables to test the server:

    cd ~/tmw-ea/eathena-data

    ./char-server & ./login-server & ./map-server &

When you log in to the server for the first time, you’ll see the character log-in on the terminal you launch the server from. 

From my notebook I loaded the TMW client:

    sudo apt-get install tmw

There are a number of TMW clients. The one in the Ubuntu 10.04 repository is a bit dated and freezes for GM’s when they entered a room where clients were logged in. Better to use the manaplus client available from http://manaplus.evolonline.org/ if you intend to expose your server to the rest of the world.

When the TMW client is loaded, click the Custom Server button, and enter the hostname you gave your server (or domain-name/dynamic DNS name). At this point, we’re just confirming the server is working locally and setting ourselves up to be GM - before exposing it to the rest of the world.

When the client connects, click the register button. Note: you cannot register through the client if you intend to play on the official Mana World server. On the main server, you have to register through the web site, and wait for approval. On your own server you just register a username.

The next screen is the character management screen where you choose a character. Since this is the first time you’ve logged on, all the character slots will be blank. Create a character and assign statistics on the next screen. You can also change hair color and hair style. As you might have guessed, one user login can have multiple characters.

You want to make sure you create a character before inviting anyone else to the server so you can set the first character to be the game master (GM). The TMW variation of eathena stores character data in ~/tmw-ea/eathena-data/login/save. The file account.txt stores character information. The file gm_accounts.txt is where you set up who will be GM on your server. GM’s and developers normally are assigned special levels. You can find these levels in the file ~/tmw-ea/eathena-data/world/map/conf/atcommand_local.conf. What’s important is that you set yourself up as a level 99 GM. If you assign other GMs set their level to 60 so they have limited GM power. The gm_accounts.txt file is formatted in the following fashion:

    account_number gm_level

The first user account is normally assigned a number of 2000000. Subsequent accounts increment the user account number by 1, so the next user account created would be 2000001. So to make the first user account GM we would give the gm_account.txt the following information:

    20000000 99

The ~/tmw-ea/eathena-data/login/save/gm_accounts.txt file can be modified while you’re logged in to your server. Once you’ve given yourself GM level, you can try some of the GM commands. All GM commands begin with an @ symbol. @help will give you a list of GM commands in the debug tab. The keen-eyed will notice that many of the @gm commands scroll right off the screen. To correct this problem we need to adjust the amount of lines available in the chat window of the client software. In the top right corner of the tmw client software, click the Setup button, then click the chat tab, and adjust Limit max lines in chat to 120.

GM’s have the power to create items, spawn monsters, warp to players, warp players to other places, even launch an all-out player versus player war, so choose your GMs carefully. GM actions are logged in a plain text file tmw-ea/eathena-data/world/map/gm.log.year.month (for example tmw-ea/eathena-data/world/map/gm.log.2012.01). We found that looking at the gm log files from the main server gave us a better understanding of the @gm commands and how they’re used. Luckily the main server is transparent with their log files, and they can be viewed online at http://server.themanaworld.org/gm.


Putting your server online

In order to make your server available to everyone on the Internet, you’ll need to punch some holes in the firewall of your router. In particular, TCP and UDP for ports 5122, 6122, and 6901. You’ll also need to modify the configuration files for the server executables. There are a lot of configuration files, in a few places. The configuration files we want are all suffixed with _local.conf. In particular we want to modify the following files:

    ~/tmw-ea/eathena-data/world/conf/char_local.conf
    ~/tmw-ea/eathena-data/world/map/conf/map_local.conf
    ~/tmw-ea/eathena-data/login/conf/ladmin_local.conf

There are 3 variables we want to set, the IP addresses for the login server, the character server, and the map server. If you’re using a dynamic DNS service, the dynamic DNS name can be used in the place of the character and map server, but you should use your local address for the login server (on our test server we used 127.0.0.1 and it worked fine for the login server). Note that if your DNS changes while the server is online the server may be unavailable. Our ISP offers a very inexpensive static IP address, which is what we use in place of the character and map server variables. Our char_local.conf looks something like this:

    // Comment : Login server IP
    login_ip: 127.0.0.1
    // Comment : Character server IP
    char_ip: auldsbel.dyndns.org

Similarly our map_local.conf looks like this:

    // Character Server IP
    char_ip: auldsbel.dyndns.org
    // Map server IP
    map_ip: auldsbel.dyndns.org

The ladmin_local.conf file is an important configuration file used by the ladmin tool. Using ladmin, the administrator can execute a variety of administrative tasks without using the client to log in to the server.

You can find a number of other configuration files in the ~/tmw-ea/eathena-data/world/map/conf directory. If you want to have magic in your world, you’ll want to look at the magic.conf.template file and the build-magic.sh shell script. The help.txt file in this directory is the same help file that gets displayed to GMs who issue the @help command. You will also likely want to customize the motd.txt (message of the day) file.

Like a lot of Linux software, the Mana World eAthena server is highly customizable. While you can run a server identical to the main server, you’ll probably want to customize your server more extensively. Good sources for information on further customization can be found on the Mana World forums, wiki, and in the How to Develop sections of the Mana World web site.

URLs of Interest:
The Mana World - http://www.themanaworld.org/
TMW Forums - http://forums.themanaworld.org/
TMW Wiki - http://wiki.themanaworld.org/
How to Develop (& server set-up) - http://wiki.themanaworld.org/index.php/How_to_Develop
Auldsbel TMW server: http://auldsbel.org/



Charles is a step-father, husband, and Linux fan who runs a not-for-profit computer refurbishing project. When not breaking hardware/servers he maintains a blog at [http://www.charlesmccolm.com/](http://www.charlesmccolm.com/).
