# Criação de pacote de instalação do app no windows
Para criação do pacote para distribuição do app desktop, vamos utilizar a ferramenta eletron-builder.

Neste exemplo criaremos o pacote apenas para windows, porem, o eletron-builder também gera pacotes para mac e linux.


## Instalar dependencias
Instalando a dependencia do electron-builder
```
$ npm install electron-builder --save-dev
$ npm install cross-env --save-dev
```

## Configurar scripts
Arquivo: packate.json

Alterar script start e incluir script build
```
  "scripts": {
    "start": "cross-env NODE_ENV=development electron .",
    "build": "cross-env NODE_ENV=production electron-builder",
    ...
  },
  ...
  "build": {
    "appId": "br.com.quickgenial.teste_electron",
    "productName": "Appelectron",
    "directories": {
      "output": "dist"
    },
    "win": {
      "icon": "icon.png",
      "target": "nsis"
    },
    "nsis": {
      "perMachine": true, 
      "allowElevation": false,
      "oneClick": false, 
      "allowToChangeInstallationDirectory": true 
    }
  }
```
obs:
 * "perMachine": true, // instalação para todos os usuários da maquina
 * "oneClick": false, // permite perguntas durante a instalação
 * "allowToChangeInstallationDirectory": true // o instalador confirma o direório destino

## criação do build
```
$ npm run build
```
Este passo cria o pacote de instalação para windows na pasta dist.

Para distribuir o app basta passar o arquivo 'dist\Appelectron Setup 1.0.0.exe'


## Rodando o App compilado
```
$ dist\win-unpacked\Appelectron.exe
```

## Instalando o App
```
$ "dist\Appelectron Setup 1.0.0.exe"
```

O app é instalado em "C:\Program Files\Appelectron" e pode agora ser executado pelo menu do windows.

