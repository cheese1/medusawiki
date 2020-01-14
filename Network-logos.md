## What are network logos?  

Network logos show a picture instead of a plain text name in the show overview page of Medusa. 

## How does Medusa receive those names?  

The names are automatically provided by the indexers [theTVDB](http://thetvdb.com/) and [TVRage](http://www.tvrage.com/).
In case there are errors in the name please change/report them to one of the above indexers.

## Where are the logos located in Medusa?  

They are located under :  `*/sickbeard/gui/slick/images/network`

## How to add network logos for Medusa?  

First you need to get your hands on a logo for that particular network. Google is your best friend here.
Once that is done use Paint.net or similar program to edit the image.

Some guidelines for the network logos are :

* Make the background transparent.
* Resize the image to 64x32 pixels.
* Save it as a .png.
* Use colored logos.
* Try not to use black or white.

The last is because Medusa has two color themes, Dark and Light. If the logo contains too much of either color it will not show properly/correctly on one of those themes. Make sure you test/check this.

Last step is to rename the image. It needs to have the exact name of the network in the show overview list.
Also use only lower case characters as upper case characters are not recognized.

Example : `Sky Atlantic`   this needs to be renamed to `sky atlantic` So the logo filename will be sky atlantic.png

Note : Special characters are not supported!

When you have the logo ready it needs to be added to Medusa. This is done with a Pull request on GitHub. You can use a program like [Sourcetree](https://www.sourcetreeapp.com/) for submitting.
If you are not able to do this, then you can alternatively post the logo and exact filename on our Medusa [issue tracker](https://github.com/pymedusa/sickrage-issues/issues ), and one of the contributors/developers will then add it for you.
