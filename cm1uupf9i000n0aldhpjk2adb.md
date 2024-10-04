---
title: "Portable emacs config without crazy load time"
seoTitle: "Portable Emacs Config: Install Packages Without Slowing Startup"
seoDescription: "Set up a portable Emacs config with a script for installing packages on new systems—without increasing startup times or bloating your config."
datePublished: Fri Oct 04 2024 14:59:12 GMT+0000 (Coordinated Universal Time)
cuid: cm1uupf9i000n0aldhpjk2adb
slug: portable-emacs-config-without-crazy-load-time
tags: emacs, linux, automation, lisp

---

Imagine you can just use `package-install` to install any Emacs package and have a painless way to reinstall the same packages when you move to a new system.

usually what happens is when you install some package, Emacs modifies your `custom-set-variables` block to include the newly installed package in the `package-selected-packages` variable. But this does not anything special to install these packages on a new system (as far as I know). So when you are on a new system you still have to manually install all the packages present in this block to get your Emacs running without any issues.

So I wrote a script that I can just run on a new system which would read the `package-selected-packages` variable and install all the relevant packages for me.

Let's go over how to get this set up.

### Step 1: have a separate `custom-file`

Add the following to your Emacs config to make sure the auto-generated `custom-set-variables` block is saved to a separate file.

```lisp
(setq custom-file "~/.emacs.d/custom.el")
(load custom-file)
```

## Step 2: Create the eslip script to do the package installation

Create a file called `sync.el` in your Emacs configuration folder with the following contents.

```lisp
(require 'package)

(load-file "~/.emacs.d/custom.el")
(print package-selected-packages)
;; Add melpa
(add-to-list 'package-archives
             '("melpa-stable" . "https://melpa.org/packages/") t)

(package-initialize)
;; refresh packages
(setq my/package-refreshed-p nil)
(defun my/refresh-contants ()
    (unless my/package-refreshed-p
      (progn
	(package-refresh-contents)
	(setq my/package-refreshed-p t))))

(dolist (pkg package-selected-packages)
  (condition-case err
      (progn
	(let ((pkg-name (symbol-name pkg)))
	  (eval (if (package-installed-p pkg)
		    (print (concat pkg-name " already installed!"))
		  (progn
		    (print  (concat  "Installing: " pkg-name))
		    (my/refresh-contants)
		    (package-install pkg))))))
    (error
     (message "Failed to install package: %s. Error: %s" pkg err))))
```

This script will go through all the packages listed in `package-selected-packages` and install any that aren’t already on the system.

The key thing here: we don’t call this script during regular Emacs startup. That means `package-refresh-contents` is **never** called when Emacs is starting up normally. So no extra load times! You only run this `sync.el` script when setting up a new system or installing your packages. The rest of the time, Emacs stays fast as usual.

## Step 3: Create a shell file to run the elisp script without launching Emacs

* Create an empty file with the following contents for example in ~/.emacs.d/sync
    

```bash
#!/bin/bash
emacs -q --script ~/.emacs.d/sync.el
```

* Make it executable:
    

```bash
$ sudo chmod +x ~/.emacs.d/sync
```

That’s it! Now, running `~/.emacs.d/sync` will install any packages listed in your `custom-set-variables` block.

# Conclusion

This technique is actually inspired by Doom Emacs. Alternatively, you could use `use-package` with `:ensure t` to handle package installation automatically. But honestly, I find that approach makes your config pretty beefy when you have a lot of packages. Adding a `use-package` block for everything feels clunky. And yeah, it might avoid the need for this script, but I like the simplicity of just listing the packages and not having to write a bunch of boilerplate.

This setup works perfectly for me—it's lightweight, avoids the usual slowdowns, and gets my Emacs ready in no time!