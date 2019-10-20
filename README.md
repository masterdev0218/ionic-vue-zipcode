# Ionic Vue Zipcode

App to display location information from the [zippopotam API](https://api.zippopotam.us/) based on a US zip-code user-input. This is another great tutorial from Traversy Media, [Youtube video: 'Build a PWA With Vue & Ionic 4'](https://www.youtube.com/watch?v=6H1wftPS0oo)

## Table of contents

* [General info](#general-info)
* [Screenshots](#screenshots)
* [Technologies](#technologies)
* [Setup](#setup)
* [Features](#features)
* [Status](#status)
* [Inspiration](#inspiration)
* [Contact](#contact)

## General info

* The user enters a US zipcode and a regex test is used to verify the format is correct. If the format is incorrect an error message is returned. If the format is correct a GET request is made to the [zippopotam API](https://api.zippopotam.us/). If it is a valid code then location data is returned in a JSON response. If the zip code is invalid then an error message is returned.

* Location data is displayed and also stored in cache to be available in the evet of loss of internet (a pwa requirement).

* The app uses firebase web hosting and is deployed to [https://zipfinder-b5b23.firebaseapp.com/](https://zipfinder-b5b23.firebaseapp.com/).

## Screenshots

![screenshot](./img/zipcode-pwa.png)

## Technologies

* [Ionic v4.11.1](https://ionicframework.com/)
* [Ionic/vue v0.0.4](https://ionicframework.com/)
* [Vue v2.6.10](https://vuejs.org/v2/guide/)
* [pwa plugin for vue-cli v4.0.4](https://www.npmjs.com/package/@vue/cli-plugin-pwa)

## Setup

* To start the server on _localhost://3000_ type: 'npm run start'

* To create a build file type: 'npm run build'

* The app is deployed to this web address: [https://zipfinder-b5b23.firebaseapp.com/](https://zipfinder-b5b23.firebaseapp.com/)

## Code Examples

* vue.config.js with pwa configuration.

```javascript
module.exports = {
  pwa: {
    workboxPluginMode: 'GenerateSW',
    workboxOptions: {
      navigateFallback: './index.html',
      runtimeCaching: [
        {
          urlPattern: new RegExp('^https://api.zippopotam.us/us/'),
          handler: 'networkFirst',
          options: {
            networkTimeoutSeconds: 20,
            cacheName: 'api-cache',
            cacheableResponse: {
              statuses: [0, 200]
            }
          }
        }
      ]
    }
  }
};
```

## Features

* **pwa plugin for vue-cli** is configurable: e.g. workbox-webpack-plugin has 2 modes: GenerateSW and InjectManifest. Other options: themeColor, appleMobileWebAppCapable, etc.

## Status & To-do list

* Status: Working.

* To-do: Develop into more advanced app.

## Inspiration

* Traversy Media: [Youtube video: 'Build a PWA With Vue & Ionic 4'](https://www.youtube.com/watch?v=6H1wftPS0oo)

## Contact

Repo created by [ABateman](https://www.andrewbateman.org) - feel free to contact me!
