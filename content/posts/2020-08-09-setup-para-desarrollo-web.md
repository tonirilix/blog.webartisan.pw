---
draft: false
date: 2020-08-09T13:09:20-05:00
title: "Mi configuración para programación web"
slug: "2020/08/09/setup-para-desarrollo-web" 
tags: ["homebrew", "configuraciones", "vagrant", "iterm", "git", "plugins"]
categories: []
description: "¿Qué configuro como programador web?"
---
> NOTA: Esta es la primera versión draft del artículo. Es posible que aún existan typos.

Dependiendo de cuáles son las tecnologías con las que estaré programando en un proyecto es lo que decido instalar en mi máquina, pero hay un conjunto de herramientas que sin importar qué es lo que estaré usando siempre necesito instalar. 

A continuación una lista de las tecnologías más básicas que necesito instalar en mi máquina para programación web.

## Homebrew - [https://brew.sh/](https://brew.sh/)
El Package Manager que necesitas

## iTerm - [https://iterm2.com/](https://iterm2.com/)
La terminal mas bella  

## Perfil para iTerm
La siguiente configuración te creará una terminal que podrás abrir desde cualquier lugar con un sólo comando:

1. En la configuración de iTerm, entra a Profiles y crea uno nuevo
2. Selecciona el nuevo perfil
3. En la pestaña de Text podrás cambiar la fuente (puedes usar Fira Code para la terminal). Activa la opción de "Use ligatures" y "anti-aliased".
4. En la pestaña de Window, podrás configurar la transparencia y el blur, pero en la sección de estilo usa la opción "Full-Width Bottom of Screen" para que la terminal se abra desde abajo. 
5. Y el paso más importante es en la pestaña de Keys, al pie de esta verás la opción "Hotkey Window". Ahí podrás configurar qué comando abrirá tu nuevo perfil.
6. Como paso opcional, te recomiendo que en la pestaña de Keys selecciones el preset ¨Natural text editing¨, para que puedas navegar en la terminal con los mismos comandos que en un editor de texto.


## Oh My Zsh - [https://ohmyz.sh/](https://ohmyz.sh/)
Un poco de vida a tu terminal

## Tema para iTerm
**Spaceship** es el tema de mi preferencia. 
Tendrás que abrir el archivo ~/.zshrc, dentro del archivo busca la opción ZSH_THEME y configúrala así:
```bash
ZSH_THEME="spaceship"
```
Si no estás seguro si esa es la mejor opción, esta es la liga en donde podrás ver el resto de los temas: https://github.com/ohmyzsh/ohmyzsh/wiki/Themes

También en la opción de ZSH_THEME podrás establecer el valor como ¨random¨ y cada nueva sesión abrirá un tema nuevo. Es una buena opción para ir probando varios.

## Plugins para zsh
Recomiento este par de plugins para zsh. 
```bash
brew install zsh-syntax-highlighting zsh-autosuggestions 
```


## Fuentes para programadores
Para instalarlas, sigue cada una de las instrucciones. 

### JetBrains Mono
[https://github.com/JetBrains/JetBrainsMono](https://github.com/JetBrains/JetBrainsMono)
[https://www.jetbrains.com/lp/mono/](https://www.jetbrains.com/lp/mono/)

### Cascadia Code
[https://github.com/microsoft/cascadia-code](https://github.com/microsoft/cascadia-code)

### Fira Code
[https://github.com/tonsky/FiraCode](https://github.com/tonsky/FiraCode)

Puedes instalar esta fuente con los siguientes comandos también
```bash
brew tap homebrew/cask-fonts
brew cask install font-fira-code
```

## VSCode Themes
Me gusta combinar Night Owl con Material Icon Theme

[night-owl](https://marketplace.visualstudio.com/items?itemName=sdras.night-owl)

[material-icon-theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)

Pero aquí hay otros temas que uso de vez en cuando

[theme-monokai-pro-vscode](https://marketplace.visualstudio.com/items?itemName=monokai.theme-monokai-pro-vscode)

[vsc-material-theme](https://marketplace.visualstudio.com/items?itemName=Equinusocio.vsc-material-theme)

[horizon-theme-vscode](https://marketplace.visualstudio.com/items?itemName=jolaleye.horizon-theme-vscode)

[dark-sea](https://marketplace.visualstudio.com/items?itemName=MoOx.dark-sea)

[github-vscode-theme](https://marketplace.visualstudio.com/items?itemName=GitHub.github-vscode-theme)

[shades-of-purple](https://marketplace.visualstudio.com/items?itemName=ahmadawais.shades-of-purple)



## Otras herramientas que instalo con brew
```bash
brew install git
brew install lazygit
brew install nvm
brew install tree
brew install cmatrix 😅
```

## Server
Por lo regular me gusta aprender los comandos de las tecnologías que dan esa opción, pero particularmente estas dos me gusta instalar un par de interfaces.
### Vagrant
- Vagrant Box
  - https://laravel.com/docs/7.x/homestead
  - https://laravel.com/docs/7.x/homestead#installing-optional-features
- Vagrant Manager
  - https://www.vagrantmanager.com/

### Docker y Plugin Docker para VSCode
- Docker
  - https://www.docker.com/get-started
- Docker Plugin
  - https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker

