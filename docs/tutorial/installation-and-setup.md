# Installation & Setup

This section will go step by step setting up a new Griptape-vue app from scratch. You can skip this by using the starter project from the [Getting Started](/introduction/getting-started). After that you can jump right to [Wallet](/tutorial/wallet-support). We do recommend you follow along here at least once so you can see the differences between a plain vue.js app setup and griptape-vue.
## Install

First create a new vite app

@vitejs/app requires node ">=10.16.0 <=14.x.x"

Open a terminal and enter
```bash
yarn create @vitejs/app griptape-tutorial

cd griptape-tutorial
```

When prompted, select `vue` for both options. (you are free to `vue.ts` as it is supported, but doing that will result in code that differs from this tutorial)

🛹 GRIPTAPE 🛹
```bash
yarn add @stakeordie/griptape-vue.js
```

Open the project in your favorite editor and make some some small but important changes to the core application files:

## Vite Config File
**vite.config.js**
```javascript {4,9-14}
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'

const path = require('path')

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [vue()],
  resolve: {
    alias: {
      '~': path.resolve(__dirname, 'node_modules'),
      '@': path.resolve(__dirname, 'src')
    }
  }
})
```

## Index File
**index.html**
```html {11}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" href="/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite App</title>
  </head>
  <body>
    <div id="app"></div>
    <script>window.global = window;</script>
    <script type="module" src="/src/main.js"></script>
  </body>
</html>
```

## App Component
Strip out everything from the App component

**/src/App.vue**
```html
<template>

</template>

<script>
  export default {
    
  }
</script>

<style>

</style>

```
And finally

## Main.js

**/src/main.js**
```javascript {5,8,10-12,15}
// Root app component
import App from './App.vue'

// Import `gripVueJsApp`
import { gripVueJsApp } from '@stakeordie/griptape-vue.js'

const conf = {
  restUrl: 'https://api.holodeck.stakeordie.com'
}

// Grip your app, you are now ready to develop your application
gripVueJsApp(conf, App, (app, pinia) => {})
```
With these changes made you can run the app with `yarn dev` and right away, keplr should popup and ask you to authorized.

**Congratulations** you are connected to the network and ready to start **Building!**