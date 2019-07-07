---
layout: post
title: "Homebrew + AXE"
image: images/homebrew.gif
categories:
  - software
tags:
  - axe
  - electrum
  - homebrew
  - macos
---
# AXE Homebrew Casks

[Homebrew](https://brew.sh) is "the missing package manager for macOS". It provides you with a _one-liner_ solution to compile/install/maintain software on macOS. This post will be touching [Casks](https://github.com/Homebrew/homebrew-cask) - part of **Homebrew** mechanics.

## Install Brew

Open the terminal and enter the following

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## Axe Core

To install Axe Core client

```
brew cask install axe-core
```

## Axe Electrum

To install Axe Electrum client

```
brew cask install axe-electrum
```

### Maintenance

Pull fresh versions with `brew update` or `brew cask upgrade`. To remove desired application use `uninstall` agains the application, like `brew cask uninstall axe-electrum`.
