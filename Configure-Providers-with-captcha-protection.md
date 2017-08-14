## Why do we need to use cookies?
A number of providers are protected with with a captcha, like google's reCaptcha. Medusa will not be able to login to these, as it cannot solve the presented captcha. When you use a browser login with your credentials and solve the captcha, your session will be stored in the browser through a number of cookies. At that point you will no longer need to login, until the coockies expire.

## The workaround
As a workaround for these providers, you can configure the provider with the cookies which you can read from your browser (like Google chrome). This article will guide you step in 1. finding out which cookies you need for your provider, 2. logging in to your provider in Google chrome and retrieving the cookies and 3. configuring the provider with the required cookies.

## Step by step

1. finding out which cookies you need for your provider
I'm assuming you have already enabled your captcha protected provider, have the Search Providers page in front of you with the provider options tab opened.

[[images/provider_options_get_cookie_names.png]]

You'll notice that in the red square you'll which cookies you need for this provider.
As in the example `Torrentday` we'll need to search for `uid` and `pass`.

2. retrieving the cookies
As for this guide i'm using chrome to retrieve the required cookies.
First let's login to your provider. As an example i'm using Torrentday. This means i'll have to open the home page of the site, fill in my credentials and "solve" the reCaptcha.
As a result you should now be logged in.

Click on the Green lock (followed with the text 'secure'), as shown in the screenshot.
[[images/provider_options_get_cookie_names_2.png]]

For the exmaple torrentday we navigate to the domain www.torrentday.com. For other providers, you'll have to browse through the tree, to locate your required cookie.
Here you'll have to look for the required cookie, and copy the value from `content`. Repeat this for all the required cookies, as retrieved from step 1.
[[images/provider_options_get_cookie_names_3.png]]

3. configuring the provider with the required cookies
The last step is the easiest. You should now have a list of cookies and the corresponding values.
As shown in the last screenshot, we've found the value `3421003` (don't use this value, as this is just an example) for the cookie `uid`. You should also have found a value for the cookie `pass`.

We should store the values in the following format: `uid=value;pass=value`.
[[images/provider_options_get_cookie_names_4.png]]

A good first test would be to run a manual search on a series, for which you know your provider should give results.