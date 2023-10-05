---
title: "Building c or c++ projects is not that hard (with cmake)"
seoTitle: "Building c or c++ projects is not that hard"
datePublished: Sun May 21 2023 16:57:11 GMT+0000 (Coordinated Universal Time)
cuid: clhxnviv900000al7183t1itn
slug: building-c-or-c-projects-is-not-that-hard
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/fQxMGkYXqFU/upload/c41df5fbb6011e9910d9e0f58692e6b3.jpeg
tags: cpp, c, cmake

---

One of the main reasons for a lot of people to give up learning c or c++ is it's hard to figure out the build system. This is a problem that both new and experienced developer face alike.

I used to use gnu make by writing my Makefile(s) by hand, and I have tried a little bit of premake which is a build system written in Lua. I knew that cmake should be the easiest solution, but I always found it very intimidating to learn how to use cmake.

So here's the simplest cmake file you can create.

(this content should go into a file called `CMakeLists.txt`)

```cpp
# Specify the minimum version of cmake to use
cmake_minimum_required(VERSION 3.0)

# Specify the name of the executable
project(Game)

# list all the source files next to the executable name
add_executable(Game main.c)

# Add any external dependencies
target_link_libraries(Game raylib)
```

you can build your project in a build folder by issuing the following commands in the terminal.

```bash
$ mkdir build
$ cd ./build
$ cmake ..
$ make
```