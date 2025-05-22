---
title: "Getting user input in Odin CLI apps"
datePublished: Thu May 22 2025 18:03:06 GMT+0000 (Coordinated Universal Time)
cuid: cmazojuej000g09l205jl5nht
slug: getting-user-input-in-odin-cli-apps
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1747936835864/5e08a487-31f5-46df-81d4-24136108d94c.png
tags: odin, odinlang

---

I had been doing some basic interpreter work in Go and wanted to redo it in another language to solidify my understanding. Naturally, I chose Odin, it’s another great language, with a Go-like, easy-to-approach syntax and no unnecessary complexity.

I had previously used Odin while building the Jack compiler for my Nand2Tetris projects last year, and I really enjoyed the experience.

As I began reimplementing my interpreter in Odin, I realized I’d never actually dealt with reading interactive user input from the command line. Since I needed a REPL, this was a must. Surprisingly, just like Go’s bufio pattern, it’s not super obvious how to do this in Odin either.

After digging around in the Odin Discord, I found how to do it.

And here is a REPL that echoes your input:

```rust
package main

import "core:bufio"
import "core:fmt"
import "core:os"

main :: proc() {

	scanner: bufio.Scanner
	stdin := os.stream_from_handle(os.stdin)
	bufio.scanner_init(&scanner, stdin, context.temp_allocator)

	for {
		fmt.printf("> ")
		if !bufio.scanner_scan(&scanner) {
			break
		}
		line := bufio.scanner_text(&scanner)
		if line == "q" {break}
		fmt.println(line)
	}

	if err := bufio.scanner_error(&scanner); err != nil {
		fmt.eprintln("error scanning input: %v", err)
	}

	free_all(context.temp_allocator)
}
```