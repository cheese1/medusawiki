## Guidelines
We highly recommend you use an editor plugin to verify you're following our standards before you commit.
If we find too many issues we may opt to close the PR until you've fixed enough of the errors.

We do provide tests via our `package.json` for the CSS and Javascript as well as pytests for the Python so please use them to make sure you commits are error free.

### Python
We try to follow the <https://www.python.org/dev/peps/pep-0008/> and <https://www.python.org/dev/peps/pep-0257/> as much as possible.

### Javascript
We use [loglevel](https://github.com/pimterry/loglevel) for logging. Please do not use `console.log`.
For linting we use [xo](https://github.com/sindresorhus/xo) with all the defaults.

### CSS
For linting we use [stylelint-config-standard](https://github.com/stylelint/stylelint-config-standard).

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