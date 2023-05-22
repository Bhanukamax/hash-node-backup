---
title: "Emacs as a Time Tracker"
datePublished: Mon May 22 2023 16:05:13 GMT+0000 (Coordinated Universal Time)
cuid: clhz1gk1w000109lb36ge5xlv
slug: emacs-as-a-time-tracker
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1684775493254/ebdd0e92-2f0b-4ecc-a6c0-8104d431b827.png
tags: emacs, productivity

---

Note: This is a post that I published in my blog on September 11, 2021, I'm re-posting it here since I'm planning to continue blogging here.

I have tried many tools and techniques to track time. Tracking time helps me organize a bit better and manage my time better. I have tried things like spreadsheets, and different utility Apps, but nothing stuck for more than a couple of days.

The good news is since I switched to Emacs recently, it opened me up to the world of org-mode, which has been pretty useful lately. But before getting to the good stuff I'll list down some of the stuff that I've tried in the past. And as with everything I wanted something keyboard-driven because I like it that way :)

## Tools and techniques I've tried in the past

### Spreadsheets

Spreadsheets was a no-brainer, it was simple enough for the job. I used to just add the list of tasks and added start and end times on two columns and at the end of the day, with the help of a few formulas, I was able to see stuff like time spent on different tasks and the total time, etc.

This was fine but wasn't perfect.

### [Project hamster GTK timetaker](https://github.com/projecthamster/hamster-gtk)

This was a good app, but it only runs on Linux, but I needed something cross-platform.

### Manual text or Mark-down files

This was a perfect solution for my itch for using the keyboard, because this, I can do in my editor. But the downside is that, text files can't really do more than just holding onto what I put in them, thus, no easy way to calculate times. End of the day I had to use a spreadsheet again to do the calculations and there's no way to quickly check the time I've spent on the current task.

## Here comes the Org Mode

So now I'm on Emacs, I've heard all the good stuff about org-mode, but soon I found out that I haven't heard it all :). My plan on capturing times on org-mode was to have an org table and insert times on that and figure out how to do calculations on org tables and you know the drill. But this was a very naive attempt at using org-mode for tracking time and I hated it. After trying that, I knew there were only two ways it was going to end up: either all the buzz about org-mode managing your life stuff is made up, emacs fan-boy stories, or I didn't know enough. Luckily it turned out to be the latter :).

### Time tracking for real in Org Mode

So I watched a few more YouTube videos and figured how it's done. I discovered the Org clock which was the real deal, it allows to clock in and out on org-mode document items.

**Here's how I use it**:

* Add the beginning of the day, I create a list of tasks I'll work on that day on a new org file.
    
* Then as I start each task, I just take the cursor over to the tasks name then call `org-clock-in` ( which is set to `SPC m c i` in Doom emacs )
    
* Every time I clock in, it just adds a new click entry to the current task and adds an end entry to the previously active clock entry.
    
* And I create add a clock report at the top of the org file calling `org-lock-report`. The report shows a summary of time spent on each task.
    

**A sample org file with time tracking and clock report:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1684775279372/c972c5f5-0240-43c2-8f7e-32692709a518.png align="center")

This actually fits really well in my workflow, I'll list down some of the pros below.

* **It's Emacs all the way** Having time tracking inside my editor mean no switching between multiple Apps, and no new key bindings to learn. I can just treat my time tracker as another text file and edit anything on it using the same musle memory I use for any other editing.
    
* **No more manual counting**
    

Although it's just a text file, org-mode give these features like real-time status, at any given time I can see the total time I've spent on the current task on the mini buffer. And there is also `org-update-all-dblock` macro, which updates all the `org-clock-report(s)` that's in the current buffer (yes, the report is not real-time, need to run that macro to update, but hey it's just one macro, no drama!! 😊)

### So is this it? is it the ultimate time tracker?

Well, this is the technique or tool which I stuck for this long. It's been two weeks now since I've started using it and it's been the most satisfying time tracker I've used till now. No big complaints here, as I said, it fits nicely within my workflow, but I wished the report was more autonomous, also I wished if there was a little bit more ease in clocking in and out. I mean, I could set a different key binding for that, but what I'm trying to say is, the overall experience could improve a bit more.

### Do I recommend it to everyone?

Yes and No!!, I mean if you are already using Emacs, I don't have to recommend it, you might already be using it or maybe something better than that, but if not, I highly recommend giving it a shot. But I don't recommend it for non-Emacs users. I think learning Emacs just to use the org-mode time tracking feature is a big undertaking, which may not be worth of your time (well, depends on your own valuation of time :) ), and it won't be satisfying either, because you have no other use of Emacs :). It's perfect for me (at least for now), because I'm using Emacs as my editor.