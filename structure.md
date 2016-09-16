# Project structure

> A project structure tree to allow you to find quickly the folder you need

<br />

``` bash
.
├── build/                      # webpack config files
│   └── ...
├── config/
│   ├── index.js                # main project config
│   └── ...
├── electron/
│   └── main.js                 # electron entry point
├── locales/
│   ├── language                # translations files
│   │   └── index.js    
│   └── index.js                # init translations files wit vue-i18n
├── settings/
│   └── default.json            # default settings
├── releases/                   # destination folder for your electron packaged apps
│   └── ...
├── src/
│   ├── assets/                 # module assets (processed by webpack)
│   │   └── ...
│   ├── components/             # ui components
│   │   └── ...
│   ├── data/                   # app datas (as routes)
│   │   └── ...
│   ├── lib/                    # some files to different librairies
│   │   └── ...
│   ├── transitions/            # vue transitions
│   │   └── ...
│   ├── vuex
│   │   ├── store.js            # exports the store (with initial state and mutations)
│   │   ├── getters.js          # exports all getters
│   │   └── actions.js          # exports all actions
│   ├── main.js                 # app entry file
│   ├── App.vue                 # main app component
├── static/                     # pure static assets (directly copied)
├── .babelrc                    # babel config
├── .editorconfig.js            # editor config
├── .eslintrc.js                # eslint config
├── index.html                  # index.html template
└── package.json                # build scripts and dependencies
```

### `build/`

This directory holds the actual configurations for both the development server and the production webpack build. Normally you don't need to touch these files unless you want to customize Webpack loaders, in which case you should probably look at `build/webpack.base.conf.js`.

### `config/index.js`

This is the main configuration file that exposes some of the most common configuration options for the build setup. See [API Proxying During Development](proxy.md) and [Configure you build](build-config.md) for more details.

### `electron/`

This directory holds all the electron related stuffs. The `main.js` file is the entry point for Electron, as specified in the `main` property of your `package.json`. See [Electron support](electron.md) for more details.

### `settings/`

This is where the settings of your app should be. The default.json file contains all the default settings and will always be loaded first as the base of your settings.

### `releases/`

This is where your packaged app will resides. Naming convention for packaged folders is `{project-name}-{platform}-{arch}` See [Electron support](electron.md) for more details.

### `src/`

This is where most of your application code will live in. How to structure everything inside this directory is largely up to you; if you are using Vuex, you can consult the [recommendations for Vuex applications](http://vuex.vuejs.org/en/structure.html).

### `static/`

This directory is an escape hatch for static assets that you do not want to process with Webpack. They will be directly copied into the same directory where webpack-built assets are generated.

See [Handling Static Assets](static.md) for more details.

### `index.html`

This is the **template** `index.html` for our single page application. During development and builds, Webpack will generate assets, and the URLs for those generated assets will automatically injected into this template to render the final HTML.

### `package.json`

The NPM package meta file that contains all the build dependencies and [build commands](commands.md).
