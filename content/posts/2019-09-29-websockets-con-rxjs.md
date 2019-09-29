---
draft: false
date: 2019-09-29T09:52:39-05:00
title: "Websockets con RxJS"
slug: "2019/09/27/websockets-con-rxjs" 
tags: ["rxjs", "websocket", "socketio", "reactive programming"]
categories: []
description: "Manipulando un stream de eventos."
---

La programación reactiva es una herramienta muy poderosa si tienes la paciencia para configurar correctamente los observables. 

Ya hacía falta un vídeo de código en el canal, pero por fin lo tenemos acá. En esta ocasión se coló mi escoba en la toma xD

En este vídeo muestro el cómo manipular un stream de eventos emitidos por un Websocket y graficarlos en D3.
Traté de que el código fuera lo más cercano a uno de producción y, es por ello que se manipulan los errores de conexión y se hacen reintentos de conexión.

## Código fuente:
Si ustedes son como yo, lo que les importará más es el código así que aquí está, listo para ser darcargado e instalado:
- Code: https://github.com/tonirilix/webartisan-yt-channel/tree/master/rxjs-websockets-d3

## Fuentes: 
- Gráfica en tiempo real en D3 
http://bl.ocks.org/KevinGutowski/131809cc7bcd1d37e10ca37b89da9630
- Gráfica en tiempo real en D3 
http://bl.ocks.org/Sohalt/9715be30ba57e00f2275d49247fa7118/43a24a4dfa44738a58788d05230407294ab7a348
- Gráfica en tiempo real múltiple en D3
https://bl.ocks.org/dooglz/049ca4a9d2eb4d9e6e4f81c489ee8d55
- Operador RxJS retryWhen
https://www.learnrxjs.io/operators/error_handling/retrywhen.html?q=
- Operador RxJS webSocket 
https://rxjs-dev.firebaseapp.com/api/webSocket/webSocket