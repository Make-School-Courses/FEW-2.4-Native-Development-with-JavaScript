# FEW 2.4 Class 3 - Desktop Apps with Electron

## Learning Objectives

1. Define use cases for desktop applications
1. Define Electron 
1. Create an Electron project with React
1. Build a Desktop application with Electron

## Before Starting! 

During this lesson you will be building desktop applications which are large binary files. You should not push this to your GitHub repository. 

Add a .gitignore if you haven't already. Add the following to it: 

```
build/
dist/
node_modules/
```

Commit and push.

## What is Electron?

[Electron](https://electronjs.org) is a platform for building desktop applications with JavaScript, HTML, and CSS. It's [open source](https://github.com/electron/electron).

Electron is built on top of the Chrome engine. All of the things that are possible in Chrome are possible in Electron and more. In soime ways you're making an application that runs a single dedicated website with some special privilleges not available to websites normally.

Looking deeper Electron is built on a minimal Chromium browser. It uses HTML/CSS/JS to create graphical user interfaces.

Electron uses Node.js and uses the same concepts. Code is written in JS and packages are imported with NPM. 

The main process is named in package.json under "main". Usually "electron.js".

Every window you create a separate **render** process. 

- Main process - core application process Node.js
- Render process - The HTML, CSS, and JS that display in a window.

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

- When you want apps to run **Offline**
- When **security** is an issue
- When you need the **file system**

## Getting started with Electron

Getting started with Electron is easy. Follow the quick start guide to make a "hello world" app with Electron. 

- https://electronjs.org/docs/tutorial/quick-start

You can follow this guide to create a barebones electron app. This is good when you want to experiment. 

If you're making an app with React you have to do a little more work. 

## Electron Builder

Electron Builder is a tool that handles a lot of the work of building your electron apps. You'll use it to create a desktop app from the a tutorial project you created in the last assignment. You can follow these steps to create a desktop app from any other React project also. 

Note! React apps have some special requirements, they are a little more than simple web pages. They also require a special build process. The steps below create an electron app using a Create React App (CRA) project.

Below I've sumarized the steps from this [article](https://www.codementor.io/@randyfindley/how-to-build-an-electron-app-using-create-react-app-and-electron-builder-ss1k0sfer) with a few changes. 

Use one of your existing prjects created with creat-react-app. Add the electron dependencies: 

```JSON
yarn add electron electron-builder --dev
yarn add wait-on concurrently --dev
yarn add electron-is-dev
```

**Create a new file**, `public/electron.js`, with the following contents.

```JS
const electron = require('electron');
const app = electron.app;
const BrowserWindow = electron.BrowserWindow;

const path = require('path');
const isDev = require('electron-is-dev');

let mainWindow;

function createWindow() {
  mainWindow = new BrowserWindow({
    width: 900, 
    height: 680,
    webPreferences: {
      nodeIntegration: true
    }
  });
  mainWindow.loadURL(isDev ? 'http://localhost:3000' : `file://${path.join(__dirname, '../build/index.html')}`);
  if (isDev) {
    // Open the DevTools.
    // BrowserWindow.addDevToolsExtension('<location to your react chrome extension>');
    // mainWindow.webContents.openDevTools();
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

Add the following to package.json: 

`"main": "public/electron.js",`

**Add the following** to "`scripts`" in `package.json`: 

`"electron-dev": "concurrently \"BROWSER=none yarn start\" \"wait-on http://localhost:3000 && electron .\""`

### Test your Electron app

Use this command to to test your electron app in development mode: 

`yarn electron-dev`

You'll use development mode while to test, modify, and add new features to your app. 

## Challenges

Follow the instructions above. These should get your Electron app running on the desktop in dev mode. This is what you'll use when you are working locally and making changes. 

**Challenge:** Follow the instructions above and get your app running in dev mode. 

**Challenge:** Look at your app and think about how you want it to run on the desktop. Think about these ideas: 

Think about the window size. A desktop app might want a fixed window size or to open at a size that works best. 

You can adjust the window size in `electron.js:11`

```JS
mainWindow = new BrowserWindow({ width: 400, height: 600 });
```

### Set up a production build 

We need some build scripts. These scripts replace the existing react scripts that come with the CRA boilerplate code.

`yarn add @rescripts/cli @rescripts/rescript-env --dev`

**Edit** `package.json` and replace these keys in scripts with these: 

```JSON
"start": "rescripts start",
"build": "rescripts build",
"test": "rescripts test",
```

Now **add a new file** named `.rescriptsrc.js` with the following contents:

```JS
module.exports = [require.resolve('./.webpack.config.js')]
```

Finally **add another new file** called `.webpack.config.js` with the following contents:

```JS
// define child rescript
module.exports = config => {
  config.target = 'electron-renderer';
  return config;
}
```

Add Electron Builder & Typescript:

`yarn add electron-builder typescript --dev`

**Edit** `package.json` again add:

`"homepage": "./",`

Now **add** these to the `"scripts"` in `package.json`: 

```JSON
"postinstall": "electron-builder install-app-deps",
"preelectron-pack": "yarn build",
"electron-pack": "electron-builder -mw"
```

Now add all of this to package.json

```json
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
},
```


Now, build your app for production: 

`yarn electron-pack`

**NOTE:** Following the instructions from the article I wasn't able to get it to build until I changed: 

`"electron-pack": "build -mw"` 

to:

`"electron-pack": "electron-builder -mw"`

I also added the following to the `electron.js` script. Without these my project wouldn't build.  

```JS
webPreferences: {
  nodeIntegration: true
}
```


## Customizing the App

The `electron.js` file has configuration code that is used to by the process that runs the electron app. The HTML/CSS/JS code that was your original CRA project is displayed by electron and is the user interface for your project.

You can modify the application in a few says. Try changing the size of the app and adding an icon. 

While the icon might not sound important in reality it is. It's the first thing people see when they use your app. So it's a chance to brand your product and set impressions. It's also required to publish your apps to the app store. Without an icon your app will automatically be rejected. 

Icons are actually more complex than you might think. You'll need images for all of the different screen resolutions your app might support. 

- Set window size in `electron.js:11`
	- `mainWindow = new BrowserWindow({width: 400, height: 600});`
- App Icon
	- https://dev.to/onmyway133/changing-electron-app-icon
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

