# Installation & Setup

This section will go step by step setting up a new Griptape-vue app from scratch. You can skip this by using the starter project from the [Setup your app Page](https://docs.griptapejs.com/introduction/getting-started), however we recommend you follow along at least once so you can see the differences between a plain vue.js app setup and griptape-vue.

# Install

First create a new vite app
```bash
yarn create @vitejs/app griptape-auctions
```
Select "vue" for both options

<video style="width: 100%" autoplay>
  <source src="/.vitepress/assets/vite-cli.mp4" type="video/mp4">
</video>

First things first, add the griptape module

```bash
yarn add @stakeordie/griptape-vue.js
```

Next lets make some small but important changes to some core application files:

vite.config.js
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
index.html
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
App.vue (Strip out everything leaving a blank Vue component)
```javascript
<template>

</template>

<script>

</script>

<style>

</style>

```
And finally /src/main.js
```javascript {5,8,10-12,15}
// Root app component
import App from './App.vue'

// Default styling
import '~/@stakeordie/griptape-vue.js/dist/style.css';

// Import `gripVueJsApp`
import { gripVueJsApp } from '@stakeordie/griptape-vue.js'

const conf = {
  restUrl: 'https://api.holodeck.stakeordie.com'
}

// Grip your app, you are now ready to develop your application
gripVueJsApp(conf, App)
```
With these changes made you can run the app with `yarn dev` and right away, keplr should popup and ask you to authorized.

**Congratulations** you are connected to the network and ready to start **building!**