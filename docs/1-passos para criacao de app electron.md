# Passos para criação de uma applicação desctop em electron

O electron é um framawork que permite construir app desktop multiplataforma (Win, Mac, linux) utilizando tecnologias do nojejs e chromium (kernel do google chrome).

O desenvolvimento é semelhante ao de uma aplicação web com utilização de html, css e javascript.

Este documento apresenta os passos necessários para a criação de um app básico.

## Iniciar o projeto em node
```
$ md exemplo-electron
$ cd exemplo-electron
$ npm init
```
O npm cria o arquivo packge.json com as configurações do projeto em nodejs.


Pode-se aceitar todas as perguntas iniciais como default. (depois pode trocar)
```
package name: (exemplo-electron)
version: (1.0.0)
description:
entry point: (index.js) main.js
test command:
git repository: (https://github.com/cnlenzc/exemplo-electron.git)
keywords:
author: Carlos Lenz
license: (ISC) MIT
```

## Instalar dependencias

Instalando a dependencia do electron no nodejs
```
$ npm install electron --save-dev
```

Este comando altera o arquivo packate.json e packate-lock.json.
Também cria a pasta node_modules com várias subpastas contendo as bibliotecas do nodejs.


## Criar arquivo mais.js com o fluxo principal do app

Arquivo: mais.js
```
const { app, BrowserWindow } = require('electron');

let mainWindow = null;

app.on('ready', () => {
    mainWindow = new BrowserWindow({
            width: 800,
            height: 600
        });
    mainWindow.loadURL(`file://${__dirname}/app/index.html`);
});

app.on('window-all-closed', () => {
    app.quit();    
});
```

## Criar html, css e js
Arquivos: app/index.html, app/css/index.css, app/js/renderer.js

Um exemplo de conteúdo destes arquivos esta neste repositório.


## Configurar start do app
Arquivo: packate.json

Incluir script start
```
  "scripts": {
    "start": "electron .",
    ...
  },
```

## rodando a aplicação

```
$ npm start
```
