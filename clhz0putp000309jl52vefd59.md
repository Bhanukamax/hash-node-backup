---
title: "Vim to Lisp to Emacs"
datePublished: Mon May 22 2023 15:44:28 GMT+0000 (Coordinated Universal Time)
cuid: clhz0putp000309jl52vefd59
slug: vim-to-lisp-to-emacs
tags: emacs, ides, vim, text-editors, lisp

---

Note: This is a post that I published in my blog on August 23, 2021, I'm re-posting it here since I'm planning to continue blogging here.

Also, I'm now back on Neovim, after using Emacs for a full year, I might write a follow-up post sometime later.

TLDR:

> I was happily using vim (neovim), then one day I discovered Lisp,  
> a week later I switched to Emacs  

I had been using Vim since 2017. At first, I had vscode as a backup for when I had to do some major code refactoring, but around mid-2020, I decided to go fully Vim and never turned back, until one day…

## A Vim Confession

Although I had been using Vim to a religious level, I felt the need for something more rich from time to time. Following are some of the pain points I had with it.

* **No proper GUI**
    

Now don't get me wrong, I don't enjoy clicking around with the mouse all day, I want to keep using the keyboard as my primary input device, but we keyboard lovers mostly end up spending most of our time on the terminal emulators because there isn't much GUI software built with the keyboard in mind. I think that's where things have gone wrong, GUI doesn't mean we have to lose the convenience of doing things with the keyboard. I use a lot of terminal-related utils, but I fancy a nice Gui version of Vim.

* **Viml and Lua**
    

Yes, vim and Neovim have bindings for a lot of languages for plugin development, but to do basic config stuff you need to deal with either vim or Lua. Yes, lua is simple, it's easier to understand and write, but I just don't enjoy Lua much.

### Vim Emulation on other editors

In the past, I have tried a few other editors/IDEs with vim emulation, like vs code, web storm, and sublime. For the most part vim style editing works fine but as soon as I try to work with multiple files, I'll have to go back to using the mouse at some point, which I don't really enjoy while writing code.

The main reason for that is the fact that unlike Vim none of those editors were built to operate with just a keyboard. But I always knew there was this other editor which was keyboard-driven just like Vim, more on that later.

## Trying Emacs

So if other editors don't cut it, it must be Emacs right, emacs was built with the keyboard in mind, it came around the same time as Vim. Also, I have heard all the stories about people switching to Emacs because of how awesome org-mode was or Magit (a popular git client implementation on Emacs), but I also none of that is going to make me use Emacs if it can't give me the same experience while writing code. So I thought I'd give it a try.

I have tried Vanila Emacs and its built-in tutorial before, but I never liked the default keybindings that came with it. I also didn't want to spend a lot of hours in Emacs to learn how to configure. I have heard of these prebuilt distributions of Emacs, I wanted to try one of those to see if Emacs can do what I want. If it works then I can learn how to config it later.

Two major such distributions I've heard of were Spacemacs and Doom. I didn't like the layer system in Spacemacs, so I decided to try Doom Emacs.

Immediately after trying it I had these issues:

* Doom emacs was slow to me compared to Vim.
    
* I still need to configure stuff to get it to a usable state for my taste, Evil mode (vim emulation) was good but it wasn't perfect.
    
* File navigation
    

  On Vim I just use Netrw to go into nearby files, I used "-" to open it and use j, k, h, l to navigate through it (this is not the default behavior, I had my Vim configured that way). But I just didn't know who to make Dired (Emacs's default file browser) to do that.

After a few hours of trying Doom Emacs, I wasn't interested enough in going further with it, because I wasn't that impressed with performance or Elisp (the language used to configure Emacs).

So I decided that Emacs wasn't for me, part of me secretly still wanted to try Emacs, but my weekend was over, and I didn't want to spend any more time on it, then I turned back to Neovim, vim is the best editor in the world.

## The Story

As a programming language enthusiast, I spend a lot of time learning about different languages, maybe more time than I really should. So, I have come across Lisp many times, but it was something I was never interested in because I always thought it was just some set of languages only used at some abstract mathematical theory level.

### Fennel

My first encounter with Lisp in action was watching vim conf 2019, I saw this language called Fennel, a Lisp that compiles to Lua. It can be used to configure Neovim, basically, it can be used in any place where Lua can be used. That was interesting but I didn't try it because it was lisp

### Finally, trying out Fennel

On a one fine Sunday evening, I just thought of finally checking out Fennel, just because I was fed up with Lua, and I wanted to give a refresh to my Neovim config, I thought I'd try this Fennel lisp thing to see how far it goes, (hint: lisp did came very far although fennel didn't ).

So I started to explore a little bit of fennel side-by-side with Lua. I started writing stuff in Fennel and watching the Lua output on a second split of my editor. To this date, I can't articulate the feeling I got as I was watching that process. I was amazed by how I was able to generate so much lua with very little fennel, and very little syntax. If you know Lisp, you know there's not much syntax to it, it's just mostly all lists, but the output on the Lua side was ugly, no blame on the compiler, it's just what Lua is, it's not pretty in my eyes.

### Exploring more about Lisp

After being marveled by watching Fennel, I wanted to find out more about this Lisp thing, so I went on youtube and started watching a lot of videos on Lisp. One of the talks I watched referred me to this other talk called [Simple made easy](https://www.youtube.com/watch?v=oytL881p-nQ) by Rich Hitchkey the creator of the Clojure programming language. I kind of bought into what he said in that video, "Simple constructs make it easy to build better solutions" (this may be not what he exactly said, but something around that, at least that's how I understood it).

So with this new mind said when I look back at lisp, I felt it, I felt that since lisp is so simple, maybe it makes it for crafting better software. And then I also thought about these stories about how Emacs has better packages (the equivalent of plugins in Vim world) compared to the similar counterparts in Vim. And even there have been innovative things like org-mode, which only first came in the Emacs world. And then I saw some more non-Emacs stuff that was built with Lisp.

It was still that same Sunday I rediscovered fennel, and I couldn't sleep well that night, I had a lot of lisp dreams, I was going to try all these new lisp stuff next weekend. There was suddenly a lot I wanted to try and find out more about, things like more fennel, Clojure, Clojure script, Common Lisp, and a big endless list of stuff.

### Trying Doom Emacs again

The next week I kept watching more youtube videos on Lisp in the evenings, and because a lot of Lisp programmers use Emacs, I saw a lot of Emacs stuff too. By around Thursday, I couldn't resist the urge to try Emacs again. And I tried it, this time though, I was fully armed to write some lisp, and I was able to configure Dired to work similarly to how Netrw worked in my Vim configuration.

Dired configuration:

```bash
;; binding for going up a directory with "h" in dired
(map! :map dired-mode-map :n "h" #'dired-up-directory)
(map! :map dired-mode-map :n "l" #'dired-find-file)

(after! dired
  (map! :n "-" 'dired-jump))

;; show simple list without the all the ls -al stuff
(add-hook! dired-mode
    (dired-hide-details-mode))
```

That was it, that's all the Elisp code I had to add to get Dired to behave the way I wanted it to, this was pretty straightforward, I know I'm using the doom emacs macros, but it gets the job done. By this time I was pretty impressed by the fact that I was just able to configure emacs to be more like I needed it to be.

So I decided to spend that evening playing a bit more with Emacs and coding a bit more to see what was missing, after hours and about a few more lines of Elisp, I had Doom emacs working, very similar to my tmux + vim setup.

**But wasn't Doom emacs slow?**

I didn't care anymore, I existed in this new lisp-driven environment, and I didn't want to lose it. Yes, it took like a few more milliseconds to open a file sometimes, but not all the time, but with that and a few lines of configuration I was getting a lot more.

## In Conclusion

In the past, I was running away from emacs because of Lisp and also because I was so in love with Vim. But Lisp got to chase behind Emacs this time around. And now I'm also using all the other good stuff which came with Emacs. I'm using Magit for most of my git work. I'm becoming an org-mode junky. I'm tracking my time on it, taking my notes on it, and even writing this blog post on an org file. And also, I'm working on my own Emacs configuration on the side as I find time so that I don't have to depend on Doom config.

### Is Emacs the best text editor in the world now?

No!!, In my opinion, that place is still for Vim, then why Emacs? because Emacs is overall a better software and an extendable interactive development environment, yes, by design, it's made for extendibility. I'm still using Vim key bindings for almost all the editing I do inside Emacs. I have even mapped Ctrl+u to do page up, but I think that's a big no-no in Emacs world because Ctrl+d has some special meaning in Emacs, I may or may not change that in the future, but that's what I have for now.

### So was Vim a mistake? would it have been better if I had started with Emacs itself?

I don't think so, as I said, figuring out how to get productive with Emacs was a bit hard at first. I don't think I'd have taken this big of a leap if I hadn't started with Vim to begin with. So I'm glad I started there.

**This is it!!**

I can write this post forever and never publish it, so I'm going to end it here, I'll write more about this new experience in the future.