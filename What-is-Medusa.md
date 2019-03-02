#### What is Medusa?

Medusa is a program that downloads your favorite TV shows, then processes and stores them in your library.
And that is all fully automated! Just set it up and as soon as there is a new episode released it gets downloaded. Medusa is your ultimate PVR!


#### How does this all work?
When you add a show to Medusa the data, such as air-dates and episode name/number, are pulled from an indexer like [TheTVDb](http://thetvdb.com/). Afterwards Medusa knows when a new episode is going to air and starts a search on your favorite Torrent and/or NZB sites. For this search you can set [quality](https://github.com/pymedusa/Medusa/wiki/Quality-Settings) settings. For example: HDTV or SD quality. Medusa will go over all the results to find the [quality](https://github.com/pymedusa/Medusa/wiki/Quality-Settings) _you_ want and when found, snatches the torrent/nzb then sends it to your download client (sabnzb, utorrent, transmission, etc.). 

At this point Medusa starts monitoring your client's download folder to see if the file is finished downloading. After it's finished downloading Medusa starts the post-processing. Here you can tell Medusa to move the file to your shows folder, rename it, or send notifications to Plex/Kodi or your smart-phone. The possibilities are endless for what you can do with post-processing; simply set the actions you prefer.

Furthermore this whole process is completely automated; Once you set it up no user intervention is required making Medusa ideal for NAS devices, although Medusa can run on almost any other device.

#### Features

Medusa contains a ton of cool features. Some of those are:  

 - Automatic torrent/nzb searching, downloading, and processing at the qualities you want
 - Automatic subtitle downloads for your shows.
 - Supports Anime and Sports shows
 - Largest list of built-in torrent and nzb providers, both public and private
 - Possibility to add (almost) every NZB/Torrent provider with the custom provider option
 - Sends notifications to your media server/software and/or mobile/social devices
 - Can notify Kodi, XBMC, Growl, Trakt, Twitter, and many more when new episodes are available
 - Updates Kodi library, poster/banner/fanart downloads, and NFO/TBN generation
 - Configurable automatic episode renaming, sorting, and other post-processing
 - Easily see what episodes you're missing, are airing soon, and more
 - Searches TheTVDB.com, TVRage.com, and AniDB.net for shows, seasons, episodes, and metadata
 - Episode status management allows for seasons/episodes that failed to force retrying en masse
 - DVD Order numbering for returning the results in DVD order instead of Air-By-Date order
 - Allows you to choose which indexer to have Medusa search its show info from when importing
 - Medusa can easily tell if info for an existing show comes from TheTVDB or TVRage when importing
 - Automatic XEM Scene Numbering/Naming for seasons/episodes
 - Available for any platform, uses a simple HTTP interface
 - Specials and multi-episode torrent/nzb support
 - Improved failed download handling
 - DupeKey/DupeScore for NZBGet 12+
 - Real SSL certificate validation

#### Dependencies  
To run Medusa we recommend the latest [Python 2.7.x](https://www.python.org/downloads/) release, and a minimum of [OpenSSL v.1.01e](https://www.openssl.org/source/). [git](https://git-scm.com/) is required for Medusa's update process. 

#### Support
In case the [Wiki](https://github.com/pymedusa/Medusa/wiki) doesn't have the answer to your question, you could check us out on irc.

We are on freenode in #pymedusa. [WebIRC kiwiirc.com](https://kiwiirc.com/client/irc.freenode.net/?theme=basic#pymedusa)

#### Bugs/Issues
In case you have found a bug and verified that it indeed is a bug, then please report it to our [issue tracker](https://github.com/pymedusa/Medusa/issues) so that the Developers can investigate.  
Note, make sure you follow the [guidelines](https://github.com/pymedusa/Medusa/issues#submitting-a-bugissue-ticket) for posting a bug.  

---

Disclaimer: Medusa should only be used with shows that you already own or are in the public domain.
