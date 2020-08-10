---
draft: false
date: 2020-08-09T13:09:20-05:00
title: "Mi configuración para programación web"
slug: "2020/08/09/setup-para-desarrollo-web" 
tags: ["hugo", "golang", "blog"]
categories: []
description: "¿Qué configuro como programador web?"
---
# Welcome to StackEdit!

Dependiendo de cuáles son las tecnologías con las que estaré programando en un proyecto es lo que decido instalar en mi máquina, pero hay un conjunto de herramientas que sin importar qué es lo que estaré usando siempre necesito instalar. 

A continuación una lista de las tecnologías más básicas que necesito instalar en mi máquina para programación web.

## Homebrew - [https://brew.sh/](https://brew.sh/)
El Package Manager que necesitas

## iTerm - [https://iterm2.com/](https://iterm2.com/)
La terminal mas bella

## Oh My Zsh - [https://ohmyz.sh/](https://ohmyz.sh/)
Un poco de vida a tu terminal

## Addons for zsh
```bash
brew install zsh-syntax-highlighting zsh-autosuggestions 
```

## Theme for iTerm
Spaceship

## New Profile for iTerm
Bottom Bar with transparency

## Development Fonts
### JetBrains Mono
[https://github.com/JetBrains/JetBrainsMono](https://github.com/JetBrains/JetBrainsMono)
[https://www.jetbrains.com/lp/mono/](https://www.jetbrains.com/lp/mono/)

### Cascadia Code
[https://github.com/microsoft/cascadia-code](https://github.com/microsoft/cascadia-code)

### Fira Code
[https://github.com/tonsky/FiraCode](https://github.com/tonsky/FiraCode)
```bash
brew tap homebrew/cask-fonts
brew cask install font-fira-code
```

## A couple of other tools
```bash
brew install git
brew install lazygit
brew install nvm
brew install tree
brew install cmatrix 😅
```

## Server
### Vagrant y Vagrant Manager
- Vagrant Box
  - https://laravel.com/docs/7.x/homestead
  - https://laravel.com/docs/7.x/homestead#installing-optional-features

### Docker y Plugin Docker para VSCode
https://www.docker.com/get-started

https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker

