As of februari 2018 Medusa utilizes a new frontend build architecture. This enables us to utilize multiple atomic themes. As long as each theme follows a specific structure, it can be used in medusa and users could add their own.
In this document we'll explain how to:
* make changes to existing themes;
* describe the theme's build architecture.

# Make changes to existing themes
If your starting with a fresh checkout of Medusa. You'll end up with the following directory structure:
**distributable**:
```.
themes/[theme name]
├── assets
│  ├── css
│  │ └── main.css
│  ├── img
│  │ └── logo.png
│  └── js
│     └── index.js
|── package.json
|── templates
│  └─ index.mako 
|── vue
│   ├── build.js
│   ├── build.js.map
│   ├── build.min.js
│   └── build.min.map
└─ index.html (SPA)
```
**source**:
```
themes_default/[theme name]
├── static
│   ├── css
│   │   └── main.css
│   ├── img
│   │   └── logo.png
│   └── fonts
│   └── js
│       └── index.js
├── package.json
└── views
│   └─ index.mako
└── vue
    ├── src
    ├── test
    ├── locales
    ├── .babelrc
    ├── index.html
    └── package.json
```

At time of writing Medusa ships with two main themes. `slim` and `legacy`. `slim` is the theme that has been made es6 ready. And this theme should be used with modern browsers like Chrome, Firefox and webkit compatible browsers.
`legacy` is an IE11 compatible browser, which should not be touched anymore. For the rest of this document we'll assume your going to work on `slim`.

You should navigate to the following directory: `./themes-default/slim/`.
By running the following command, you will make sure you have installed all the npm modules, required for building and testing theme.
```
npm install -g yarn // If you have not yet installed yarn.
yarn // To install all dependencies and start the lint.
```

At this time you'll have to choose a theme which your are going to export to. The source is the same except for the dark.css or light.css stylesheets. Using the theme `dark` will build all files into: `themes/dark/*` and `light` into `themes/light/*`.

Run the following command:
```
gulp watch --csstheme dark
```
This will start the following:
* Copy all css files from ./static/css -> themes/dark/assets/css
* Copy all js files from ./static/js -> themes/dark/assets/js
* Copy all fonts from ./static/fonts -> themes/dark/assets/fonts
* Copy all images from ./static/images -> themes/dark/img
* Copy all mako templates from ./views -> themes/templates
* Copy all vue files from ./vue -> themes/vue
* Copy package.json and index.html from ./ -> themes/

With these actions other actions are also performed, like minimizing js, adding source maps, and compress images.

After all tasks have been finished, you'll end up with a build theme, and a watcher has been started. This will watch all source files and compare them to it's source. Whenever it detects a change, it will only build the changed files.
For changes to mako templates you'll need to restart medusa. Others should become directly visible.

## package.json
At Medusa startup medusa reads the ./themes/ folder for all available themes, by moving through the folders and reading the package.json. This is the configuration file for each theme.
As a minimum it will require the following attributes:
* name
* version

## Dark and light sub-theme
Currently we're utilizing one 'mako' templated frontend, with a css for a light and dark theme.
I'd like to add a feature where it's possible to select a complete different frontend (html/mako, css and js) but reuse the existing endpoints. As discussed with @OmgImAlexis this could be realized by changing the webroot data folder to the theme's path. The routes will always stay the same.

### Solution
