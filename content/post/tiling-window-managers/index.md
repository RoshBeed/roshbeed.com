---
title: Tiling Window Managers
date: 2019-08-18
image:
  placement: 1
---
Today we will delve into the realms of window management and discover new ways to organise windows. Today we will learn new things. Today we will learn about tiling window managers. 

## Contents
* [Desktop Environments](#desktop-environments)
* [Window Managers](#window-managers)
* [List vs. Tree](#list-vs-tree)
* [Stacking Window Managers](#stacking-window-managers)
* [Tiling Window Managers](#tiling-window-managers)
* [Conclusion](#conclusion)

## Desktop Environments
How do window managers work alongside other pieces of software?

You have likely used a window manager as part of a group of applications known as a desktop environment.
Before we look in-depth at window managers, let us have a brief overview of Desktop Environments

* Package of applications to create a complete graphical environment
	* Windows Manager
	* Taskbar
	* Applications
		* Terminal emulator
		* File manager
		* Text editor
* May also include
	* Application launcher
	* Clipboard manager
	* Desktop compositor
	* Desktop wallpaper setter and desktop icon
	* Display manager
	* Display power saving settings
	* Logout dialogue
	* Mount tool
	* Notification daemon
	* Polkit authentication agent
	* Screen locker
	* Sound volume manager
	* Default applications 

## Window Managers

Window Managers control the placement and appearance of windows in a graphical user interface.

* Draws graphical applications
* Controls aspects of windows
	* Appearance
	* Placement
	* Border
	* Titlebar
	* Size

## List vs. Tree
Stacking window managers utilise lists to draw windows in order. List-based tiling window managers use them to populate a predefined grid layout.

Tree-based tiling window managers can have different layouts at each parent node. You can define horizontal or vertical splits and place windows wherever you wish.

## Stacking Window Managers
The windows act like pieces of paper on a desk. They can be drawn anywhere on the screen. They can overlap.

![][6]


## Tiling Window Managers
Tiling window managers place windows in a grid where none of the windows can overlap.

Here we have two windows horizontally split.

![][1]

The parent node has another window added to it.

![][2]

Two horizontal splits can achieve the same layout.

![][3]

Setting the parent node of windows 2 and 3 to a vertical split.

![][4]

## Conclusion
Tiling window managers offer us a fast and efficient way to organise windows. Tree-based tiling window managers enable us to create custom layouts on-the-fly.

Learning to master a tiling window manager is daunting. It requires a paradigm shift in your window management mindset. Your optimal keybindings may take countless iterations to perfect.

Tiling window managers allow us to manage windows solely through the keyboard. Slowing down our workflow to use the mouse to organise windows is a thing of the past. Start using a tiling window manager today!

[1]: /img/tiling-window-managers/H(2,1).png
[2]: /img/tiling-window-managers/H(3,2,1).png
[3]: /img/tiling-window-managers/H(3,H(2,1)).png
[4]: /img/tiling-window-managers/H(3,V(2,1)).png
[5]: /img/tiling-window-managers/H(6,V(5,H(V(H(2,1),3),4))).png
[6]: /img/tiling-window-managers/S6.png

## Did you find this page helpful? Consider sharing it 🙌
