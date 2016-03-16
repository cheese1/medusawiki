####Information regarding a normalized development environment setup and project standards for code Should go here.

###### Adding js libraries

Make sure you have `node.js`, `bower` and `grunt` installed then run the command below, it'll install all of the needed dependencies for grunt along with all of the uncompressed library files and then build a new version of `_bower.js` and `_bower.min.js` in the `gui/slick/js/` directory.

If you don't have `bower` or `grunt` installed use `npm install -g bower` and/or `npm install -g grunt-cli` to install them.

````
npm install && bower install && grunt
````

Now that you have everything installed and up to date you'll want to install the new library, to do this we install it via bower and then run grunt to minify it with all of the other libraries.

````
bower install <package> --save && grunt
````