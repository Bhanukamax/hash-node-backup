---
title: "Vim Fuzzy file search and navigation without plugins"
seoTitle: "Master Fuzzy File Search and Navigation in Vim Without Plugins"
seoDescription: "Discover how to efficiently perform fuzzy file search and navigation in Vim using built-in commands like :find and :buffer—no plugins required."
datePublished: Sun Aug 25 2024 15:04:01 GMT+0000 (Coordinated Universal Time)
cuid: cm09p9jdr000g09lbhzc594lm
slug: vim-fuzzy-file-search-and-navigation-without-plugins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724598024421/b17ff5cf-14eb-4f05-814e-bf2ec62b6d9d.png
tags: linux, vim, neovim, text-editors, text-editor, minimalism, vimawesome, vimrc, fuzzy-search, fuzzy-file

---

Recently, I got curious about how Vim’s built-in commands handle file finding and navigation. Even though I was using modern fuzzy finding plugins at the time, I decided to explore Vim’s native mechanisms. To my surprise, I started enjoying the simplicity and effectiveness of these built-in tools.

If you prefer to see these tips in action, check out the video linked at the end of this post!

### Using `:find` for Fuzzy Searching

By default, the `:find` command in Vim requires the full path of the file you want to open. For instance, you might type `:find src/parser/parser.odin`.

Here’s a handy trick: if you set the `path` option to `**`, Vim will search through all directories from your current working directory. You can do this by adding the following line to your `.vimrc`:

```bash
set path=**
```

With this setting, `:find` becomes much more flexible. For example, if you type `:find par` and hit Tab, Vim will suggest files that match “par” anywhere in your directory. It’s a simple way to perform fuzzy searches without extra plugins.

### Navigating Buffers with `:buffer`

To switch between open files, you can use the `:buffer` command (or just `:b`). Suppose you have these files open:

* `src/parser/parser.odin`
    
* `src/main.odin`
    
* `src/tokenizer/tokenizer.odin`
    

Typing `:b to` and pressing Enter will take you to the buffer that matches the input. In this case it’ll open the ‘src/tokenizer/tokenizer.odin’ file. It’s a straightforward method for navigating between your open files.

### Enjoying the Simplicity

As I started using these built-in commands more, I found them to be quite effective. They offer a simple and efficient way to search and navigate files and buffers without relying on additional plugins.

### Vertical Completion Menu

If you prefer a vertical completion menu, similar to what you might see in Neovim, you can enable it in Vim by setting `wildoptions` to `pum`. Unlike Neovim, this isn’t the default in Vim. Add this to your `.vimrc`:

```bash
set wildoptions=pum
```

### Conclusion

Exploring Vim’s built-in file finding and navigation features has been a rewarding experience. By adjusting `:find` and using `:buffer`, you can navigate and manage your files effectively with just the default tools.

You can see these techniques in action in the video below.

%[https://youtu.be/xxSLNxPK4ew?si=QZ1-6YuNOMT0UUBk] 

Happy Vimming!