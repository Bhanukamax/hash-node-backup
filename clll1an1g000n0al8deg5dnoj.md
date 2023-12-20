---
title: "Build multiple OCaml executables in one Dune Project"
seoTitle: "Dune: Build multiple OCaml executables"
seoDescription: "Build multiple OCaml executables in one Dune project. This is useful for doing things like the advent of code problems in one Dune project."
datePublished: Mon Aug 21 2023 15:30:40 GMT+0000 (Coordinated Universal Time)
cuid: clll1an1g000n0al8deg5dnoj
slug: build-multiple-ocaml-executables-in-one-dune-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703051355216/b861be00-b0ac-4f13-b217-457fc361fc85.png
tags: ocaml, dune

---

### Create a dune project

Follow these steps to create a new dune project if you don't already have one.

* First, initiate the project structure.
    
    ```bash
    dune init project foo
    ```
    
* It will create a project structure like this
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692630925329/e373f499-bbfd-4945-859c-7eba141f1b07.png align="center")
    
    The bin folder contains the source file for the main executable `main.ml`
    
* the `bin/dune` file has the build instruction for the executable, it'll look something like this.
    
    ```lisp
    (executable
     (public_name foo)
     (name main)
     (libraries foo))
    ```
    

### Adding Support to build multiple executables

* Let's see how to add support to build another executable called bar, which we'll write in the file called `bar.ml`.
    
* First, create a file called `bar.ml` in the `bin` directory.
    
* Then you can update the `bin/dune` file support multiple executables like below.
    
    ```lisp
    (executables
     (public_names foo bar)
     (name main bar)
     (libraries foo))
    ```
    

### Build and run the different executable

You can use the following commands to run the different executables.

```bash
dune exec ./bin/main.exe
dune exec ./bin/bar.exe
```

To build you can run following

```bash
dune build ./bin/main.exe
dune build ./bin/bar.exe
```

To run the built executables

```bash
 ./_build/default/bin/main.exe
 ./_build/default/bin/bar.exe
```