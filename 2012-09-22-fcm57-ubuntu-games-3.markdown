---
layout: post
title: "57期 - Ubuntu 游戏 Installing Minecraft"
date: 2012-09-22 13:33
comments: true
categories: issue57 Ubuntu-Games
---

Written by Peter Liwyj

This article assumes you have Ubuntu installed and ready to go, and you’re sitting looking at a Unity desktop [I’ll add Kubuntu notes where I can - Ed]. 

First, you need a 3D video driver. On your nice new Unity desktop, which is probably confusing you, click on "Dash home" on the top left of the Unity desktop.

At the bottom of the screen you'll see some icons.  Click on the Pencil/Pen/Ruler icon.

Top left of the next screen, you'll see "Additional Drivers." This is for your video card, and perhaps other things. (For Kubuntu, click K > Applications > System > Additional Drivers). Select an appropriate video driver, then click on "Activate." Enter your password in the box that pops up. Let the driver download and install. You’ll probably have to reboot to load the drivers. The little gear shape at the top right of the Unity desktop has the shutdown option in it.

Now it’s time to install Java. If you previously installed the “restricted extras,” you probably have it already. If not, click on the "Ubuntu Software Centre." It starts out as the 5th icon up on the left side of the Unity desktop, looks like a shopping bag. (In Kubuntu, it’s K > Applications > System > Muon Software Centre.)

Search for "Java."

You'll get several options, you want "OpenJDK6 Java runtime" (not seven - you want JDK six). Install it.

Go to Minecraft.net and download the minecraft.jar file by saving it on your desktop, or wherever you like. First, open it in your favorite archive manager, and poke around. You're looking for the favicon.png file. It's a picture of a Minecraft block, save a copy of it somewhere out of the way for later.

Go back to your minecraft.jar file, right click on it, and select ‘properties’ at the bottom of the menu. In the BASIC tab, click on the picture and navigate to the favicon.png you saved earlier. In the PERMISSIONS tab, check the "allow executing this file as a program" (“Is Executable” in Kubuntu) check box, and in the OPEN WITH tab (In Kubuntu you get this by right-clicking the file and selecting “Open With...”), and select OpenJDK Java 6 runtime - and make it default while you're there.

TIP: You can also enter:

    java -jar

as the starting application to the ‘open with’ window in Kubuntu. You can also create a desktop ‘widget’ shortcut to the jar file in Kubuntu.

That's it! Run Minecraft, it'll download what it needs, and go.

I have it running at about 50 to 80 frames per second at 1024 X 768 resolution...on a 32 inch Toshiba TV! The 3D analglaph is mind-blowing, by the way... I was afraid of the depth at first (heights make me nervous), and those holes into the bedrock gave me the willies!

Your system may vary slightly or a great deal, but that's how I got mine going perfectly.
