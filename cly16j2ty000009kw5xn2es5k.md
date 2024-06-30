---
title: "How to use Xephyr for Window Manager Development"
datePublished: Sun Jun 30 2024 06:37:59 GMT+0000 (Coordinated Universal Time)
cuid: cly16j2ty000009kw5xn2es5k
slug: how-to-use-xephyr-for-window-manager-development
tags: linux, window-managers, xephyr, xinit, startx

---

To future me:

You don't need to install Arch Linux on your laptop or buy a new laptop or install it on a vm to try window management development. Xephyr is just enough for testing the basics. Just make sure you press Ctrl + Shift to lock focus when trying to do any binding in the window manager been tested.

The most basic command to start the window manager in a nested session is to do something like

```bash
startx i3 -- /usr/bin/Xephyr :1
# with specifying window size
startx i3 -- /usr/bin/Xephyr -screen 800x500 :1
```

just make sure to use the full path to the Xephyr.

Above method works, but most of the times when you are just starting out you may not have a way to launch apps inside the window manager. For that using a keybinding agent like sxhkd will be very useful. To do that we need to be able to run other programs besides the window manager while launching.

To do that we can use a xinitrc to add the programs we need to launch.

so we can create a xinitrc file with the following content.

```bash
sxhkd ~/.config/sxhkd/sxhkdrc &
xterm & # also launching a terminal just in case
# assuming the window manager
# executable is called main and is in the current directory
exec ./main
```

then you can also have another script to call xinit and open Xephyr with the relevant options

```bash
#!/bin/sh

set -e
#!/bin/sh

set -e
make # just calling make to build the project once more,
# so we can just use this one script to just build and run
XEPHYR=$(which Xephyr)
xinit ./xinitrc -- \
    "$XEPHYR" \
    :100 \
    -ac \
    -screen 800x500 \
    -host-cursor
```