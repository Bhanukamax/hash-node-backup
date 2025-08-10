---
title: "Why I Actually Settled on JetBrains IDEs (After All That Editor Hopping)"
seoTitle: "Why I Actually Settled on JetBrains IDEs After Years of Editor Hopping"
seoDescription: "My journey from Vim and Emacs to VSCode and finally to JetBrains IDEs. Why GoLand and CLion stuck when other editors didn't, and what makes JetBrains differ"
datePublished: Sat Aug 09 2025 18:48:06 GMT+0000 (Coordinated Universal Time)
cuid: cme4ly0x8000902lhcwpccqxn
slug: why-i-actually-settled-on-jetbrains-ides-after-all-that-editor-hopping
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1754764428700/59e5d39e-2974-4c3a-9d05-3e5d129a7520.png
tags: emacs, golang, vim, webstorm, neovim, text-editors, vs-code, jetbrains

---

Remember my post about switching to VSCode? Well, plot twist: the very next day after publishing it, I switched to WebStorm. And guess what? I've been on JetBrains IDEs ever since.

I know, I know. Another "why I switched editors" post. But hear me out—this time it actually stuck, and I think I've finally figured out why.

## The Reality Check

After years of hopping between Vim, Emacs, and VSCode, I've settled into a workflow that's honestly just... practical. I use GoLand for Go and frontend development, and CLion for exploring raylib and other C/C++ (or Odin with Odin plugin) projects.

The thing is, I had some WebStorm experience before—maybe a month or two here and there between my various editor adventures. But this time, something clicked differently.

## What VSCode Got Wrong (For Me)

Don't get me wrong, VSCode has incredible out-of-the-box support for most technologies. But its UX just never sat right with me. Take project-wide text search, for example. VSCode crams those results into a tiny sidebar that's genuinely painful to navigate. Compare that to Vim's quickfix list or Emacs' xref results—even these supposedly "rudimentary" editors (spoiler: they're not) handle search results way more elegantly.

Build configuration is another pain point. Maybe I'm missing something, but I've never been able to wrap my head around VSCode's build configuration with those JSON files. In Vim, you set `makeprg` and you're done. In Emacs, you configure a compile command or use async shell commands. Simple. Intuitive.

That workflow never clicked for me. Zed gets this right—you can run arbitrary commands and bind keys to re-run them. JetBrains takes a similar approach but excels especially when it comes to running tests, debugging, and build configurations—it's all just straightforward and works without fighting the tool.

## Why JetBrains Just Works

Here's the thing about JetBrains IDEs: they actually live up to that "it just works" promise, but in a more real way than VSCode ever did for me.

Setting up builds, running tests, debugging—it's all straightforward. No hunting through documentation to figure out which JSON schema you need. No wondering why your launch configuration isn't working. You just... do the thing you want to do.

Sure, JetBrains IDEs aren't as keyboard-driven as Vim or Emacs out of the box. But here's where it gets interesting: I found some JetBrains plugins that make the editing experience much closer to Emacs. This gave me the best of both worlds—JetBrains' excellent tooling with more familiar keybindings and editing patterns.

## The Right Tool for the Job

These days, my setup is simple:

* **GoLand** for Go + frontend work
    
* **CLion** for exploring raylib, etc
    

Here's something interesting about JetBrains' licensing: you don't actually need WebStorm if you have GoLand. Any upper-tier IDE like GoLand, IntelliJ IDEA Ultimate, or CLion includes all the WebStorm functionality built right in. So even though I do web development at work, GoLand handles JavaScript, TypeScript, React, and all the web technologies just as well as WebStorm would. It's essentially WebStorm plus Go support, not a separate thing entirely.

This feels more mature than trying to make one editor do everything, while also being more practical than juggling multiple specialized tools when you don't need to.

I still use Cursor occasionally for AI capabilities, but when I'm actually writing code? JetBrains runs the show.

## Looking Back at the Journey

My editor journey—Vim → Emacs → VSCode → JetBrains—wasn't really about finding the "best" editor. It was about finding what works for me, right now, with the kind of work I'm doing and the setup I have.

Will I switch again in the future? Maybe. But for now, I'm not fighting my tools anymore. I'm just getting work done.

And honestly? That feels pretty good.

---

*What's your take on the great editor debate? Have you found your "final" editor, or are you still on the journey? Let me know in the comments below.*