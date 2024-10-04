---
title: "Portable emacs config without crazy load time"
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

## Step 3: Create a shell file to run the elisp script without launching Emacs

* Create an empty file with the following contents for example in ~/.emacs.d/sync
    

```bash
#!/bin/bash
emacs -q --script ~/.emacs.d/sync.el
```

* And make it executable
    

```bash
$ sudo chmod +x ~/.emacs.d/sync
```

That's all, now running this `~/.emacs.d/sync` command will install any packages listed on your `custom-set-variables` block.

# Conclusion

This technique is actually inspired by doomemacs. Also alternatively you can just make sure you use `use-package` with `:ensure t` to make sure your packages get installed without any of these steps.

But I like to not add a bunch of `use-package` block for every single Emacs package I want to use. And this works perfectly for me!