## Guidelines
We highly recommend you use an editor plugin to verify you're following our standards before you commit.  
If we find too many issues we may choose to close the PR until you've fixed enough of the errors.

We provide tests for the CSS and Javascript via our `package.json`.  
For Python, we use `pytest` and `flake8` through a `setup.py` command.  
Please use the tests to make sure you commits are error free. The automated builds will fail if any of the tests fail.

### Python
We try to follow the [PEP 8](https://www.python.org/dev/peps/pep-0008/) and [PEP 257](https://www.python.org/dev/peps/pep-0257/) as much as possible.

### Javascript
We use [loglevel](https://github.com/pimterry/loglevel) for logging. Please do not use `console.log`.  
For linting we use [xo](https://github.com/sindresorhus/xo) with all the defaults.  

### CSS
For linting we use [stylelint-config-standard](https://github.com/stylelint/stylelint-config-standard).

### Vue.js
We use [Vue.js](https://vuejs.org/v2/guide/) for rendering the application frontend.  
Please follow the current code style.  
<!-- ==== @TODO: Write a page for our Vue code style ==== -->

### API
To access the REST API via js we recommend you use the `api` global we have setup to be accessed on all pages.

For example to update the current theme just patch the theme's name.
All errors should be caught and passed to `log.error()`. All info should be passed to `log.info()`.
```
api.patch('config', {
    theme: {
        name: $(this).val()
    }
}).then(function(response) {
    log.info(response);
}).catch(function(err) {
    log.error(err);
});
```

### Themes
More info on building themes [here](https://github.com/pymedusa/Medusa/wiki/Themes)