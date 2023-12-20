---
title: "Emacs-Inspired Search in Vim"
datePublished: Sat Jul 01 2023 04:51:16 GMT+0000 (Coordinated Universal Time)
cuid: cljjizx1h00010amhbj3x5f42
slug: emacs-inspired-search-in-vim
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703051714603/dbe920eb-2441-4863-b62a-60279619dd43.png
tags: emacs, vim, neovim

---

I wanted to share some in-buffer search techniques that I brought back to my Neovim setup from my year of experience with Emacs.

You know how you can use "/" and "?" to perform forward and backward searches for text in the current buffer. Similarly, in Emacs, you can use Ctrl+s and Ctrl+r to search back and forth. There's a slight difference in how it works in Emacs, though. In Emacs, searching starts immediately as you type Ctrl+s, and the text you type is incrementally added to the current search term. You can achieve the same behavior in Vim with "set `incsearch`," but there's more. In Emacs, you can keep hitting Ctrl+s and Ctrl+r to continue searching back and forth in the buffer while still editing the search term.

Can we do the same in Vim?

Yes, you can, but it works slightly differently in Vim. When you are in `incsearch` mode, i.e., once you hit "/" or "?" and start typing a text, you can still edit the text and search back and forth without having to go back to normal mode. The default keys to do that are Ctrl+g (search forward) and Ctrl+t (search backward).

However, this might be a lot to remember, and you may not end up using it even though you know it because of all the keybindings you have to remember.

I have a simpler way to achieve this in my configuration, where I'm able to use Ctrl+s just like in Emacs. Instead of Ctrl+r, I mapped search backward to Alt+s because Ctrl+r is the default keybinding to redo.

The following is what I have in my Neovim config to make this work:

```bash
vim.keymap.set('n', '<C-s>', '/')
vim.keymap.set('c', '<C-s>', '<C-g>')
vim.keymap.set('n', '<A-s>', '?')
vim.keymap.set('c', '<A-s>', '<C-t>')
```