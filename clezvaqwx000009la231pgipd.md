---
title: "Python venv with fish shell"
seoTitle: "notes, python, fish"
seoDescription: "How to work with python virtualenv in fish shell"
datePublished: Wed Mar 08 2023 16:01:24 GMT+0000 (Coordinated Universal Time)
cuid: clezvaqwx000009la231pgipd
slug: python-venv-with-fish-shell
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/mJMrbY-jtls/upload/3c47035339093abb1722a1b48258cb66.jpeg
tags: notes, fishshell

---

These commands can be used to create virtualenv with bash or zsh

```bash
virtualenv -p $(which python3) .env
source .env/bin/activate
pip install -r requirements.txt
```

to do the same in fish you can use these:

```bash
# Create
virtualenv venv
# Activate
. venv/bin/activate.fish
# install requirements
./venv/bin/pip install -r requirements.txt
```