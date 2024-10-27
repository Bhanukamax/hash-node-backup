---
title: "Linking Libraries Locally with CMake: A Follow-Up"
seoTitle: "Linking Local Libraries in CMake: A Simple Guide for C/C++ Projects"
seoDescription: "Learn how to link libraries from local folders in CMake, making your C/C++ project setup flexible and portable."
datePublished: Sun Oct 27 2024 04:44:53 GMT+0000 (Coordinated Universal Time)
cuid: cm2r3w0cn000309js2drqavlf
slug: linking-libraries-locally-with-cmake-a-follow-up
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1730003979822/7d5bd640-2121-4f85-847a-730117e716fd.webp
tags: cpp, c, compiling, cmake, raylib, linking

---

In my [previous post](https://imbmax.com/building-c-or-c-projects-is-not-that-hard) about building C/C++ projects with CMake, I shared a simple CMakeLists.txt setup for compiling a basic project. Today, I’ll dive into a specific need that many developers encounter: linking libraries directly from project folders rather than relying on a system-wide installation. Why Link Libraries Locally?

Sometimes, you might want to keep your dependencies within your project directory, whether for portability, version control, or simply to avoid installing extra packages globally. Here’s how I set this up with CMake. Updated CMakeLists.txt Example for Local Libraries

This is the setup I use to link Raylib (a popular C library for game development) directly from my `libs` folder.

```bash
cmake_minimum_required(VERSION 3.29)
project(Game)

# Set the C++ standard version
set(CMAKE_CXX_STANDARD 20)

# Include and link directories for Raylib (in ./libs folder)
include_directories("./libs/raylib-5.0_linux_amd64/include")
link_directories("./libs/raylib-5.0_linux_amd64/lib")

add_executable(Game main.cpp)

# Link dynamically to Raylib 
# Comment this if you are going with static linking
target_link_libraries(Game PRIVATE raylib) 

# Uncomment the following line if you prefer static linking
# target_link_libraries(cppray PRIVATE raylib.a)
```

### Key Points:

* include\_directories: Adds headers for Raylib.
    
* link\_directories: Adds the path to the Raylib library files.
    
* target\_link\_libraries: Specifies whether you’re linking dynamically or statically (toggle as needed).
    

## Revisiting the Previous Approach

In the first post, I used target\_link\_libraries(Game raylib) without specifying local paths, assuming a system-wide installation. While that approach is simpler, linking libraries from subdirectories can be more portable, especially for sharing projects or working across different environments.