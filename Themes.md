As of February 2018 Medusa utilizes a new frontend build architecture. This enables us to utilize multiple atomic themes. As long as each theme follows a specific structure, it can be used in Medusa and users could add their own.  
In this document we'll explain:
* How to [make changes to existing themes](#make-changes-to-existing-themes)
* A [theme's build architecture](#themes-build-architecture)

# Make changes to existing themes
If you're starting with a fresh checkout of Medusa, you will see that there is a `default-themes` directory and `themes` directory.  
`themes-default` is the source and `themes` is the distributable.

At time of writing Medusa ships with a single main theme: `slim`.  
`slim` is the theme that has been made ES6 ready, and this theme should be used with modern browsers like Chrome, Firefox and other webkit compatible browsers.

Install yarn globally, if you haven't done so already: [Installation | Yarn](https://yarnpkg.com/lang/en/docs/install)  

You should navigate to the following directory: `./themes-default/slim/`.  
By running the following command, you will make sure you have installed all the node modules, required for building and testing the theme.  

Install all dependencies and start the lint:
```
yarn
```

**Webpack** is used to bundle the web application.  
You may use the following command to bundle the application for **development** mode:
```
yarn dev
```

When building for the `master` branch, please use the following command to bundle the application for **production** mode:
```
yarn build
```

Both commands will automatically copy the relevant files to the each theme's directory.  
* Copy all css files from `./static/css` -> `themes/{theme}/assets/css`
* Copy all js files from `./static/js` -> `themes/{theme}/assets/js`
* Copy all fonts from `./static/fonts` -> `themes/{theme}/assets/fonts`
* ~~Copy all images from `./static/images` -> `themes/{theme}/assets/img`~~  
  [See **Gulp** section below]
* Copy all Mako templates from `./views` -> `themes/{theme}/templates`
* Copy `index.html` from `./` -> `themes/{theme}/`
* Update theme metadata in `themes/{theme}/package.json`

Where `{theme}` is the theme name (`dark` or `light`).

Please note that at the time of writing, when renaming/removing files in any of the folders above,  
it is required to manually remove the old files from the target folders in `./themes`.

**Gulp** is temporarily used for copying and compressing images.  
If you're adding a new image to `./static/images` or modifying an existing image, run the following command:
```
yarn gulp sync
```
This will copy all images from `./static/images` -> `themes/{theme}/assets/img` and compress the new and changed images.

After all tasks have been finished, you'll end up with a built theme.

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
themes-default/[theme name]
├── src
│   └── app.js
│   └── index.js
├── static
│   ├── css
│   │   └── main.css
│   ├── images
│   │   └── logo.png
│   └── js
├── package.json
└── views
│   └─ index.mako
```

## package.json
At Medusa starts up, it reads the `./themes/` folder for all available themes, by moving through the folders and reading the `package.json` file. This is the configuration file for each theme.
As a minimum it will require the following attributes:
* name
* version