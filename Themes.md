As of February 2018 Medusa utilizes a new frontend build architecture. This enables us to utilize multiple atomic themes. As long as each theme follows a specific structure, it can be used in Medusa and users could add their own.  
In this document we'll explain:
* How to [make changes to existing themes](#make-changes-to-existing-themes)
* A [theme's build architecture](#themes-build-architecture)

# Make changes to existing themes
If you're starting with a fresh checkout of Medusa, you will see that there is a `default-themes` directory and `themes` directory.  
`themes-default` is the source and `themes` is the distributable.

At time of writing Medusa ships with a single main theme: `slim`.  
`slim` is the theme that has been made ES6 ready. And this theme should be used with modern browsers like Chrome, Firefox and other webkit compatible browsers.

You should navigate to the following directory: `./themes-default/slim/`.
By running the following command, you will make sure you have installed all the npm modules, required for building and testing the theme.
Install yarn, if you haven't done so already:
```
npm install -g yarn
```
Install all dependencies and start the lint.
```
yarn
```

Webpack is used to bundle the web application.  
You may use the following command to bundle the application for **development** mode:
```
yarn dev
```

When you are done, please use the following command the bundle the application for **production** mode:

Both commands will automatically copy the relevant files to the each theme's directory (`./themes/dark` and `./themes/light`).  

Gulp is currently still used for most of the theme build.
In order to build the rest of the theme, run the following command:
```
yarn gulp sync
```
This will start the following:
* Copy all css files from ./static/css -> themes/{theme}/assets/css
* Copy all js files from ./static/js -> themes/{theme}/assets/js
* Copy all fonts from ./static/fonts -> themes/{theme}/assets/fonts
* Copy all images from ./static/images -> themes/{theme}/assets/img
* Copy all mako templates from ./views -> themes/{theme}/templates
* Copy index.html from ./ -> themes/{theme}/

With these actions other actions are also performed, like minimizing js, adding source maps, and compress images.

After all tasks have been finished, you'll end up with a built theme.

## Build the dark or light theme
You may build a specific theme using:
**from ./themes-default/slim**
* dark: `yarn gulp build --csstheme dark`
* light: `yarn gulp build --csstheme light`

# Theme's build architecture

## Directory structure
**distributable**:
```
themes/[theme name]
├── assets
│  ├── css
│  │ └── main.css
│  ├── img
│  │ └── logo.png
│  └── js
│     └── app.js
│     └── index.js
|── package.json
|── templates
│  └─ index.mako 
└─ index.html
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
│       └── app.js
│       └── index.js
├── package.json
└── views
│   └─ index.mako
```

## package.json
At Medusa starts up, it reads the `./themes/` folder for all available themes, by moving through the folders and reading the `package.json` file. This is the configuration file for each theme.
As a minimum it will require the following attributes:
* name
* version