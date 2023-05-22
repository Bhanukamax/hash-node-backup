---
title: "How to create your very own keyboard layout"
datePublished: Sat May 06 2023 17:22:14 GMT+0000 (Coordinated Universal Time)
cuid: clhc95y99000009mj5og8dgmw
slug: how-to-create-your-very-own-keyboard-layout
tags: ubuntu, linux, dvorak, keboard

---

1. Create a new file in the `/usr/share/X11/xkb/symbols/` directory. You can name the file anything you like, but it's recommended to use a name that reflects your new layout.
    
    For example, you can create a file called "mydvorak" by opening a terminal and typing the following command:
    
    ```bash
    sudo gedit /usr/share/X11/xkb/symbols/mydvorak
    ```
    
2. In the new file, define your new layout. You can use the existing `dvorak` layout as a starting point, and make modifications as needed.
    
    Here's an example of a modified `dvorak` layout that makes the symbol positioning easier for people coming from `qwerty`.
    
    ```bash
    // My custom Dvorak layout
    partial alphanumeric_keys
    xkb_symbols "basic" {
    
        include "us(dvorak)"
    
        key <AE11> {	[     minus,	underscore	]	};
        key <AE12> {	[     equal,	plus		]	};
    
        key <AC11> {	[     slash,	question	]	};
    
        key <AD11> {	[ bracketleft,	braceleft	]	};
        key <AD12> {	[ bracketright,	braceright	]	};
    
        key <BKSL> {	[ backslash,         bar	]	};
    };
    ```
    
3. Save the file and exit the editor.
    
4. Edit the `/usr/share/X11/xkb/rules/evdev.xml` file to include a reference to your new layout.
    
    I added the following next to all the `dovrak` entries
    
    ```xml
            <variant>
              <configItem>
                <name>mydvorak</name>
                <description>mydvorak</description>
              </configItem>
            </variant>
    ```
    
5. Restart your computer to apply the changes.
    

**How to switch keyboard layouts**

you can use the `setxkbmap` program to change the keyboard layouts.

I have setup the following aliases to switch back and forth between the `qwerty` vs `mydvorak` layout.

```bash
alias asdf="setxkbmap -v mydvorak"
alias aoeu="setxkbmap -v us"
```