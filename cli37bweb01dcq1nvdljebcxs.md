---
title: "Release my port!"
datePublished: Thu May 25 2023 14:00:39 GMT+0000 (Coordinated Universal Time)
cuid: cli37bweb01dcq1nvdljebcxs
slug: release-my-port
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/GfES0V79wCc/upload/5541d58ca10de12062ea110450225c91.jpeg
tags: linux, web-development, command-line

---

So you are doing some exciting web dev work. And for some reason, you get a message saying the port you are trying to use is already in use.

Something like this:

```bash
 Error: listen EADDRINUSE: address already in use 0.0.0.0:3022
```

You don't know what to do, so you go to some generative AI chatbot and ask something dumb like:

```xml
how do i find the process using some address in linux? Because i'm getting this 
Error: listen EADDRINUSE: address already in use 0.0.0.0:3022
```

it doesn't have to be perfect, no spellings or grammar issues need to be checked, because it's an AI, it'll figure it out.

And it replies:

You can use the `lsof` command to find the process that's using a specific address in Linux. Here's how:

1. Open a terminal window.
    
2. Type the following command and press Enter:
    

```bash
$ sudo lsof -i :3022
```

1. This will list all processes using the port 3022, along with their Process IDs (PIDs).
    
2. Note the PID of the process that's using the port you're interested in.
    
3. Type the following command to kill the process using the port:
    

```bash
$ sudo kill -9 <PID>
```

Replace `<PID>` with the actual PID of the process you want to kill.

Alternatively, you can try restarting your system or changing the port number for your application to avoid conflicts