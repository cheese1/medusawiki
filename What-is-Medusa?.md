#### What is Medusa?

Medusa is a program that downloads your favorite TV shows, then processes and stores them in your library.
And that all fully automated! Just set it up and as soon as there is a new episode released it gets downloaded. Medusa is your ultimate PVR.!  


#### How does this all work?
When you add a show to Medusa the data (like air-dates, episode name/number) are pulled from an indexer like [TheTVDb](http://thetvdb.com/). At that point Medusa knows when a new episode is going to air and starts the search on your favorite Torrent and/or NZB site. For this search you can set [quality](https://github.com/pyMedusa/SickRage/wiki/Quality-Settings) settings. For example: HDTV or SD quality. Medusa will go over all the results to find the [quality](https://github.com/pyMedusa/SickRage/wiki/Quality-Settings) YOU want and when found snatches the torrent/nzb and sends it to your download client. (sabnzb, utorrent, transmission etc.) At this point Medusa starts monitoring your clients download folder to see if the file is finished downloading. When this is the case Medusa starts the post-processing. Here you can tell Medusa to move the file to your shows folder, or also rename it, or send notifications to Plex/Kodi or to your smart-phone. The list is long for what you can do with post-processing, simply set the actions you prefer.
And this whole proses is completely automated. So once you set it up no user intervention is required.
This makes Medusa ideal for NAS devices. But can run on almost every other device.

#### Features

Medusa contains a ton of cool features. Some of those are :  

 - Automatic torrent/nzb searching, downloading, and processing at the qualities you want
 - Automatic subtitle downloads for your shows.
 - Supports Anime and Sports shows
 - Largest list of build-in torrent and nzb providers, both public and private
 - Possibility to add (almost) every NZB/Torrent provider with the custom provider option
 - Sends notifications to your media server/software and/or mobile/social devices
 - Can notify Kodi, XBMC, Growl, Trakt, Twitter, and many more when new episodes are available
 - Updates Kodi library, poster/banner/fanart downloads, and NFO/TBN generation
 - Configurable automatic episode renaming, sorting, and other post-processing
 - Easily see what episodes you're missing, are airing soon, and more
 - Searches TheTVDB.com, TVRage.com, and AniDB.net for shows, seasons, episodes, and metadata
 - Episode status management allows for mass failing seasons/episodes to force retrying
 - DVD Order numbering for returning the results in DVD order instead of Air-By-Date order
 - Allows you to choose which indexer to have Medusa search its show info from when importing
 - Medusa can easily tell if info for an existing show comes from TheTVDB or TVRage when importing
 - Automatic XEM Scene Numbering/Naming for seasons/episodes
 - Available for any platform, uses a simple HTTP interface
 - Specials and multi-episode torrent/nzb support
 - Improved failed download handling
 - DupeKey/DupeScore for NZBGet 12+
 - Real SSL certificate validation

#### Screenshots
_(as of December 2014)_<br/>
-[Desktop (Full-HD)](http://imgur.com/a/4fpBk)<br>
-[Mobile](http://imgur.com/a/WPyG6)

#### Dependencies  
To run Medusa we recommend [Python 2.7.10 or 11](https://www.python.org/downloads/release/python-2711/), and a minimum of [OpenSSL v.1.01e](https://www.openssl.org/source/). [GIT](https://git-scm.com/) is required for Medusa's update process. 
The minimum requirements are Python 2.7.x with the latest modules of [PyOpenSSL](https://pypi.python.org/pypi/pyOpenSSL), and [cryptography](https://pypi.python.org/pypi/cryptography). (Cheetah isn't required anymore.)  

#### Support
In case the [Wiki](https://github.com/pyMedusa/SickRage/wiki) doesn't have the answer to your question, you could check us out on irc.
We are on freenode in #pymedusa. [WebIRC kiwiirc.com](https://kiwiirc.com/client/irc.freenode.net/?theme=basic#pymedusa)

#### Bugs/Issues
In case you have found a bug and verified that it indeed is a bug, than please report it to our [issue tracker](https://github.com/pyMedusa/SickRage/issues) so that the Developers can investigate.  
Note, make sure you follow the [guidelines](https://github.com/pyMedusa/SickRage/issues#submitting-a-bugissue-ticket) for posting a bug.  

---

Disclaimer: Medusa should only be used with shows that you already own or are in the public domain.
