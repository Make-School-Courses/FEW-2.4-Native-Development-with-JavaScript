# FEW 2.4 Class 3 - Desktop Apps with Electron

## Learning Objectives

1. Define use cases for desktop applications
1. Define Electron 
1. Create an Electron project with React
1. Build a Desktop application with Electron

## What is Electron? 

[Electron](https://electronjs.org) is a platform for building desktop applications with JavaScript, HTML, and CSS. It's [open source](https://github.com/electron/electron).

Electron is built on top of the Chrome engine. All of the things that are possible in Chrome are possible in Electron and more. In some ways you can think you're making an application that runs a single dedicated website with some special privilleges not available to websites notmally. 

Looking deeper Electron is built on a minimal Chromium browser. It uses HTML/CSS/JS to create graphical user interfaces.

Electron is built on Node.js and uses the same concepts. Code is written in JS and packages are imported with NPM. 

Electron runs a single main process. This is the process that is named in package.json. 

Every window you create a separate render process. 

### Who is using Electron? 

A lot of common apps are using electron. 

- Github Desktop
- Visual Studio Code
- Atom
- Slack 
- WhatsApp
- GraphiQL
- [...many more](https://electronjs.org/apps)

### Why use a Electron?

If you know how to make a website you can hack together a desktop app with Electron. 

In most use cases you'll want to make a website. But for cases where you really need a desktop app Electron is probably the fastest easiest way to get there. 

### When do you need a desktop app?

- Offline
- Security is an issue
- Needs the file system

## Getting started with Electron

Getting started with Electron is easy. Follow the quick start guide to make a "hello world" app with Electron. 

- https://electronjs.org/docs/tutorial/quick-start

## Electron Builder

Electron Builder is a tool that handles a lot of the work of building your electron apps. We will use it here.

Note! React apps have some special requirements, they are a little more than simple web pages. They also require a special build process. Luckily Electron  Builder supports with Create React App projects out of the box.

Below I've sumarized the steps from this [article](https://www.codementor.io/randyfindley/how-to-build-an-electron-app-using-create-react-app-and-electron-builder-ss1k0sfer)

- Create a new React App. You can skip this step if you already have an app. Just start the next from your app's directory. 
	- `npx create-react-app my-app`
	- `cd my-app`
- Add some dependencies
	- `yarn add electron electron-builder --dev`
	- `yarn add wait-on concurrently --dev`
	- `yarn add electron-is-dev`
- Add public/electron.js to setup electron
	- below...
- Add to scripts in package.json
	- `"electron-dev": "concurrently \"BROWSER=none yarn start\" \"wait-on http://localhost:3000 && electron .\""`
- Add to root of package.json
	- `"main": "public/electron.js",`

Test dev mode

- `yarn electron-dev`

Setup production 

- Add to root of package.json
	- `"homepage": "./",`
- Add to scripts in package.json
	- `"postinstall": "electron-builder install-app-deps",`
	- `"preelectron-pack": "yarn build",`
	- `"electron-pack": "build -mw"`
- Add to root of package.json
```JSON
"author": {
  "name": "Your Name",
  "email": "your.email@domain.com",
  "url": "https://your-website.com"
},
"build": {
  "appId": "com.my-website.my-app",
  "productName": "MyApp",
  "copyright": "Copyright © 2019 ${author}",
  "mac": {
    "category": "public.app-category.utilities"
  },
  "files": [
    "build/**/*",
    "node_modules/**/*"
  ],
  "directories": {
    "buildResources": "assets"
  }
}
```

Build your app for production

- `yarn electron-pack`

---

- electron.js

```JS
const electron = require('electron');
const app = electron.app;
const BrowserWindow = electron.BrowserWindow;

const path = require('path');
const isDev = require('electron-is-dev');

let mainWindow;

function createWindow() {
  mainWindow = new BrowserWindow({width: 900, height: 680});
  mainWindow.loadURL(isDev ? 'http://localhost:3000' : `file://${path.join(__dirname, '../build/index.html')}`);
  if (isDev) {
    // Open the DevTools.
    //BrowserWindow.addDevToolsExtension('<location to your react chrome extension>');
    mainWindow.webContents.openDevTools();
  }
  mainWindow.on('closed', () => mainWindow = null);
}

app.on('ready', createWindow);

app.on('window-all-closed', () => {
  if (process.platform !== 'darwin') {
    app.quit();
  }
});

app.on('activate', () => {
  if (mainWindow === null) {
    createWindow();
  }
});
```
---

## Customizing the App

- Set window size in electron.js:11
	- `mainWindow = new BrowserWindow({width: 400, height: 600});`
- App Icon
	- https://www.christianengvall.se/electron-app-icons/
	- https://www.electron.build/icons
	
## Build an Electron App

Your goal is to build a desktop application from your React project. Follow the guide above. Your deliverable is a functioning native app that runs on Mac or Windows. 

- Native App

## After Class

The goal this week is to build an Electron app. Take the tutorial project or a project that you have created with React and build an Electron app with it. 

You have one week to work on this. Scope conservatively. 

Choose a React App you have created, this can be one of the tutorial projects, and make an Electron with it. 

## Additional Resources

- [Electron](https://electronjs.org)
- [Electron Apps](https://electronjs.org/apps)
- [Create React App + Electron](https://medium.com/@kitze/%EF%B8%8F-from-react-to-an-electron-app-ready-for-production-a0468ecb1da3)

