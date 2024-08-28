---
title: "Setting up Emacs to have `gql` template literals highlights"
datePublished: Wed Aug 28 2024 15:47:53 GMT+0000 (Coordinated Universal Time)
cuid: cm0e15ird000b09ma3hu2ffui
slug: setting-up-emacs-to-have-gql-template-literals-highlights
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724860016107/813dcc5a-3cbd-4bef-bdc0-e266503b0fb8.png
tags: emacs, graphql, text-editors

---

This code is copied form emacs stack-exchange and adopted to work with web-mode for future reference.

Following is the link to the original stack exchange post:

[https://emacs.stackexchange.com/questions/37918/how-to-highlight-graphql-template-literals-gql-in-jsx-files](https://emacs.stackexchange.com/questions/37918/how-to-highlight-graphql-template-literals-gql-in-jsx-files)

step1: Install the packages

```haskell
M-x package-install RET graphql-mode
M-x package-install RET mmm-mode
```

step2 : Put this in your config

```lisp
;; Graphql
(require 'graphql-mode)
(require 'mmm-mode)

(mmm-add-classes
    '((js-graphql
          :submode graphql-mode
          :face mmm-declaration-submode-face
          :front "[^a-zA-Z]gql`" ;; regex to find the opening tag
          :back "`"))) ;; regex to find the closing tag
;; mode in the next line can be any major mode that you use for the particular file
;; The original answer from stackexchanged had js-mode,
;; I have replaced it with web-mode is that's what I use
(mmm-add-mode-ext-class 'web-mode nil 'js-graphql) 
(setq mmm-global-mode 'maybe)
;; Optional configuration that hides the background color for a highlighted block
;; I find it useful for debugging emacs, but when actually coding I dont want so much emphasis on submodes
(setq mmm-submode-decoration-level 0)
```