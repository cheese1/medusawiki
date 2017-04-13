----------
[ [Help & Info] ](https://github.com/pymedusa/Medusa/wiki/Settings-explained#help--info) [ [General] ](https://github.com/pymedusa/Medusa/wiki/Settings-explained#general) [ [ Backup ] ](https://github.com/pymedusa/Medusa/wiki/Settings-explained#backup) [ [Search settings] ](https://github.com/pymedusa/Medusa/wiki/Settings-explained#search-settings) [ [Search providers] ](https://github.com/pymedusa/Medusa/wiki/Settings-explained#search-providers) 
[ [Subtitles search] ](https://github.com/pymedusa/Medusa/wiki/Settings-explained#subtitles-search) [ [Post processing] ](https://github.com/pymedusa/Medusa/wiki/Settings-explained#post-processing)  [ [ Notifications] ](https://github.com/pymedusa/Medusa/wiki/Settings-explained#notifications) [ [Anime] ](https://github.com/pymedusa/Medusa/wiki/Settings-explained#anime)  

-----------

## The settings (gearwheels) section explained.

* This is the section where you configure Medusa to your likings.  
As you can see below Medusa supports a massive amount of customization settings, and might lead to some confusion. With this wiki we will try to explain the settings in more details. As many of those settings are for advanced user only, make sure you understand what the settings does before setting.

![statusmenu](https://cloud.githubusercontent.com/assets/7928052/13013102/4bb15e2e-d1ae-11e5-8668-2ef7e7429228.png)

## Help & Info

![helpinfo](https://cloud.githubusercontent.com/assets/7928052/13013132/70b0840c-d1ae-11e5-8894-f3dd8b95dfe9.png)

`SR Version:`  
This show the exact version of Medusa you are using. Medusa gets updated with so called Commits (code updates). And by knowing the last Commit your particulair Medusa is running, you can tell if you missed updates and/or helps the Develpors trouble shooting a problem you have.  
`SR User:`  
This shows the user on your system that is running Medusa.  
`SR Locale:`  
This shows your Locale (language) setting that your system uses. Its strongly advised that u use UTF-8 to prevent any problems with special characters.  
`SR Config file:`  
Shows the location of your config.ini file. It includes all your settings for Medusa.  
`SR Database file:`  
Shows the location of your sickbeard.db file. It includes all your shows for Medusa.  
`SR Cache Dir:`  
Shows the location of your cache folder. It includes all your search data, banners and other temporary files for Medusa.  
`SR Log Dir:`  
Shows the location of your application.log file. It includes all the events, warnings and errors. If you ever experience problems or issues, the log will be your best friend.    
`SR Arguments:`  
Shows with what arguments Medusa has been started.  
`Python Version:`  
This shows your Python version. Medusa needs a minimal version of 2.7 but the more recent the better. Also make sure pyopenssl and cryptography modules are included in your Python version.  


## General  

#### Misc  
![misc](https://cloud.githubusercontent.com/assets/7928052/13013194/b6248ed4-d1ae-11e5-9294-47d533575b86.png)

`Default Indexer Language`  
With this setting you set the default language that needs to be used for your shows and metadata. Note: not for subtitles.!  
`Launch browser`  
Automatically opens the Medusa web page on startup.  
`Initial page`  
Select the default page that Medusa needs to open when you access the website.  
`When to update shows`  
You can manually set a time at witch Medusa updates/refreshes the shows information from the indexers.  9airdates etc.) Best to use a time at night when the device is idle.  
`Update shows on startup`  
Feature was removed  
`Update shows on snatch`  
Lers Medusa update the shows data when an episode is snached.  
`Send to trash for actions`  
This option lets Medusa move the files to a recycle bin instead of the normal permanent delete. Note doesn't work on all Operating Systems.  
`Log file folder location`  
Lets you set a custom location for the log file. Also can be handy if you use a NAS to store the log on a usb stick. That allows the disks to go into standby and spin down.  
`Number of Log files saved`  
Lets you set he number of log files that are stored before deleted.  
`Size of Log files saved`  
Lets you set the size of the individual log files. Set the seize to your individual needs.  
`Use initial indexer set to`  
Lets you set the default indexer (thetvdb or tvrage) when adding a new show.  
`Timeout show indexer at`  
Lets you set a custom timeout value. Dont change unless asked or the indexer is very slow to respond to your request.  
`Show root directories`  
Shows an overview of your added root folder(s). Those are the folders where your shows are located.  
You can add, edit, delete and set a default folder.  

#### Updates 
 
`Check software updates`  
Lets Medusa check if there are new updates on startup, and at a specific time interval. It updates are available you will see a notification on top of your Medusa page. There you can update and check what changes where made.  
`Automatically update`  
Automatically approves updates and installs them.  
`Check the server every*`  
Lets you set the time interval for update checks. Once a day is advised to make sure you get the latest bug-fixes.  
`Notify on software update`  
Let Medusa sent a notification for the update to all notifiers that you have configured/enabled.  

#### User Interface (Options for visual appearance.)  

![interface-1](https://cloud.githubusercontent.com/assets/7928052/13013213/d4e0ead4-d1ae-11e5-8848-fbf3429e45fb.png)

`Display theme`  
Currently there are 2 themes to chose from. The Dark and Light theme. Chose the theme of your preference.  
`Show all seasons`  
Allows you to collapse past/aired seasons on a shows page. This can be handy for shows that run for many years and you just need to see the recent season expanded.  
`Sort with "The", "A", "An"`  
When sorting the show list on name, you can chose to remove "The", "A", "An" from the name. Personal preference.  
`Filter Row`  
Lets you set a filter option on the show list. So you can filter shows.  
`Missed episodes range`  
Set the range in days of the missed episodes in the Coming Episode page  
`Display fuzzy dates`  
move absolute dates into tooltips and display e.g. "Last Thu", "On Tue"  
`Date style:`  
Lets you chose the Date style for how a date should be shown.  yyyy-mm-dd thusday-mm-yy etc.  
`Time style:`  
Use AM/PM time or 24hr.  
`Timezone:`  
Lets you set the timezone. Display dates and times in either your timezone or the shows network timezone  
`Download url`  
[See here](https://github.com/pymedusa/Medusa/wiki/How-to-use-Download-url)  


#### Web Interface  

`API key`  
The API key is used by external apps like download clients to communicate with Medusa. Generate a key and add it to your preferred app.  
`HTTP logs`  
This enables logs from the internal Tornado web server. Let this be disabled unless ask to enable.  
`HTTP username`  
You can set a username and pasword when opening the Medusa website.  
`HTTP password`  
You can set a username and pasword when opening the Medusa website.  
`HTTP port`  
The port on witch Medusa accepts http connections. Make sure no other application uses this port.!  
`Listen on IPv6`  
Enable ipv6 support and attempt binding to any available IPv6 address.  
`Enable HTTPS`  
lets you enable HTTPS for secure connections.  
`HTTPS certificate`  
file name or path to HTTPS certificate  
`HTTPS key`  
file name or path to HTTPS key  
`Reverse proxy headers`  
?  

#### Advanced Settings  

![advanced-settings](https://cloud.githubusercontent.com/assets/7928052/13013237/eb2e4bc4-d1ae-11e5-8278-fd321a7844da.png)

`CPU throttling:`  
Lets you control the CPU usage. Can be handy on low powered devices.Note : High is lower and Low is higher CPU use.  
`Anonymous redirect`  
Lets you set backlink protection via anonymizer service when opening a link.  
`Enable debug`  
Lets you enable debug logs. This give you more log information than normal.is A requirement for troubleshooting if you encounter an error/bug.  
`Verify SSL Certs`  
This feature enables the verification of SSL certificates for HTTPS etc.. This should only be disabled in case of SSL errors or for testing. But first check if you have installed pyton correctly with pyopenssl and cryptology.  
`No Restart`  
Only shutdown when restarting SR. Only select this when you have external software restarting SR automatically when it stops (like FireDaemon)  
`Encrypt passwords`  
Lets you encrypt passwords in your config.ini file. Make sure the password only contains ASCII characters.  
`Unprotected calendar`  
By default the calendar is protected. This options disables the protection so that an third party app can access it. (like Google Calendar)  
`Proxy host`  
Let you set a Proxy to use with Medusa.  
`Default deleted episode status:`  
Lets you set the default status of shows that have been deleted or have already been aired and not found in the folder.  

#### GitHub  

`Branch version:`  
This shows the Medusa versions you can select. Master branch is the default and the Develop branch is hidden, and can only be access if a GitHub account is added. However end-users should always use Master and only switch to Develop if asked.  
`GitHub username`  
Here you can add your GitHub username.  
`GitHub password`  
Here you can add your GitHub password.  
`GitHub remote for branch`  
default:origin. Access repo configured remotes (save then refresh browser)  
`Git executable path`  
only needed if OS is unable to locate git from env  
`Git reset`  
Removes untracked files and performs a hard reset on git branch automatically to help resolve update and missing files issues.  

## Backup  

* This sections allows you to create an backup of your Medusa settings. The files include :  
  * `sickbeard.db` That contains all your shows  
  * `config.ini` That contains all your settings  
  * `Cache folder` That contains all your search results  

![backup](https://cloud.githubusercontent.com/assets/7928052/13013263/0ab50460-d1af-11e5-9830-849abfdeee7b.png)

`Backup`  
Lets you set the backup folder where Medusa saves your backup.

![restore](https://cloud.githubusercontent.com/assets/7928052/13013273/13bb6b6c-d1af-11e5-9ec5-c5de4ab44f4c.png)

`Restore`  
Lets you browse and select your backup file to be restored.  

## Search Settings  

* This sections allows you to set all Search related settings.  

#### Episode Search  

![episode-search-1](https://cloud.githubusercontent.com/assets/7928052/13013292/250850c4-d1af-11e5-9a3a-f37b25aed7fb.png)

`Randomize Providers`  
By default Medusa searches the provider list from top to the bottom. If you enable this setting, Medusa will randomize the search order.  
`Download propers`  
Sometimes releases that are uploaded get "nuked" by the scene. This means there is something wrong with the file. Like it has freezes, no audio or other defects. Than a new file is released witch is called a Proper. If you enable this function Medusa will automatically search for propers of episodes you have already downloaded and snatch the proper if it finds one.  
`Check propers every:`  
Lets you set the time/frequency on witch Propers should be searched.  
`Backlog search frequency`  
Lets you set the Backlog search frequency. Backlog is only used if episodes cant be found with the Daily search.  
`Daily search frequency`  
Lets you set the Daily search frequency. This is the main search for finding episodes. The default recommendation is 120 minutes. Dont go below 30 minutes!.  
`Usenet retention`  
If you use NZB's than check what the retention of your Usenet server is and add the value in this field. This prevents Medusa from sending episode NZB's that are not on your Usenet server anymore. Most payed Usenet servers have a retention above 1000 days, but ISP servers generally offer much less like 31 days.  
`Ignore words`  
If Medusa comes across any of those words in the title of a search result, the result will be SKIPPED. Apply's to all shows. USE WITH CAUTION!   
`Require words`  
Medusa SKIPPES/IGNORES all search results that dont have those words in the title. Apply's to all shows. USE WITH CAUTION!  
`Allow high priority`  
This sets downloads of recently aired episodes to high priority. So those get priority over already aired episodes. Some download clients like SABnzb allow sending with high priority to prioritize downloads.  
`Daily search on startup`  
Feature was removed.   
`Run backlog on startup`  
Feature was removed.     
`Use Failed Downloads`  
Lets you enable failed downloads.  This will also allow adding bad/failed torrents/nzb to the failed.db so that they aren't downloaded again.  
`Delete Failed`  
Removes files left behind from a failed download. Needs to have failed downloads enabled.

#### NZB Search  

![nzb-search](https://cloud.githubusercontent.com/assets/7928052/13013322/4139856a-d1af-11e5-9efa-b02058e2f6fb.png)
![nzbget](https://cloud.githubusercontent.com/assets/7928052/13013323/415c9898-d1af-11e5-8003-17b8fc0647af.png)

`Search NZBs`  
Enable this setting if you plan to use NZB's and usenet to snatch your shows.  
`Send .nzb files to:`  
Select you download client. Currently the directly supported NZB clients are SABnzbd and NZBget. However for all other clients you can use the blackhole method. With this method Medusa places the NZB in a folder of your choosing. Simply let your download client monitor that folder for new NZB files. And the download client does the rest. This makes Medusa compatible with almost every download client out there.  
`SABnzbd server URL`  
Add the URL where your SABnzbd client is located.  
`SABnzbd username`  
Add the username of SABnzbd.  
`SABnzbd password`  
Add the password of SABnzbd.  
`SABnzbd API key`  
Add the API key of SABnzbd. This allows Medusa to send the nzb directly to SABnzbd. You can find the key in your SABnzb configuration.  
`Use SABnzbd category`  
Set the category that SABnzbd uses for tv shows. Default is TV.  
`Use SABnzbd category for anime`  
Set the category that SABnzbd uses for anime shows. Default is anime.  
`Use forced priority`  
enable to change priority from HIGH to FORCED. This allows NZBs to even start when SABnzbd is Paused.  

#### Torrent Search  

* This sections allows you to set the torrent download client. 

![torrent-search](https://cloud.githubusercontent.com/assets/7928052/13013338/55be7ed2-d1af-11e5-86c5-0c2a23dad48d.png)

`Search torrents`  
Enable this function to download yous shows with Torrents.  
`Send .torrent files to:`  
This allows you to set the direct torrent download clients. Currently supported are. : uTorrent, Transmission, Deluge, Synology Download Station, rTorrent QBittorrent. Also the blackhole method is supported, so that almost every Torrent download client is supported.  
`Synology DS host:port`  
Add the adress and port of Synology Download Station.  
`Synology DS username`  
The username of the Synology account. (best to use the admin account to prevent permission issues.)  
`Synology DS password`  
The password of the Synology account.  
`Downloaded files location`  
Here you can set a manual download location. If blank the default Download Station folder is used.  

## Search Providers  

* This sections allows you to setup your Search Providers  

#### Provider Priorities  

This sections allows you to enable/disable the providers you want to use and drag&drop them in the order you like them to be searched. Al-trough Medusa has already a large number of build-in providers it can be that your favorite provider is not yet added. Dont worry, Medusa has the possibility to add almost every NZB/Torrent provider that is out there. This can be done by adding a Custom provider. Especially for NZB providers its better to set them up manually, that gives you the most flexibility and efficiency while  searching. For more information see the explanations below.   

#### Build-in NZB (and Custom) Providers

![provider-priorities-nzb](https://cloud.githubusercontent.com/assets/7928052/13013411/acaf6756-d1af-11e5-871a-a7c554eba681.png)

#### Build-in Torrent providers (as of Juli 2015)

![provider-priorities-torrent](https://cloud.githubusercontent.com/assets/7928052/13013410/ac13e8bc-d1af-11e5-9930-5cd590000a8d.png)

#### Provider Options  

* This sections allows you to configure the providers.    

![provider-options](https://cloud.githubusercontent.com/assets/7928052/13013420/ba4ef552-d1af-11e5-914c-8a1c9fe2056d.png)

`Configure provider:`  
Those the provider you want to modify. (only enabled providers are shown in the list.)  
`URL:`  
The url of the provider.  
`API key:`  
Add here the API key that the provider has supplied you with.  
`Enable daily searches`  
Do you want to enable daily searches for this provider.?  
`Enable backlog searches`  
Do you want to enable backlog searches for this provider.?  
`Season search fallback`  
Do you only want to search season packs with this provider.?  
`Season search mode`  
Do you only want to search episodes packs with this provider.?  

#### Configure Custom Newznab Providers  

* Medusa lets you add almost every NZB Indexer out there. The custom Newznab is the preferred way of adding an NZB indexer. You might ask yourself if its not better to build them in? Well its not... Firstly there are so many NZB indexers out there that it is impossible to add them all. But even a better reason is that you can search far more efficient if you add/configure the indexer manually. An indexer uses category's to search. Generally they are divided between SD, HD, Sports, Anime etc. Now lets say you only need HD releases than there is no point in adding/enabling all the others. Same if you only need Sports. This method is far more efficient then building-in a provider and using all the category's by default.  

![configure-custom-newznab-providers](https://cloud.githubusercontent.com/assets/7928052/13013477/f304da42-d1af-11e5-83fe-462702b4f567.png)

`Select provider:`  
Here you can add a new custom newznab provider by selecting --add new provider-- or modify an already added custom provider.  
`Provider name:`  
Here you can add the name of the provider. You can freely name it, but if you like to get an provider icon infront of the provider name than use naming like oznzb or oznzb.com as the icons are named this way.  
`Site URL:`  
The providers URL. Try to use HTTPS for better security if the providers allows it, otherwise HTTP.  
`API key:`  
Fill in your API key that your provider has provided you with.  
`Newznab search categories:`  
Here you can add the categories for your provider. For regular users the categories 5030 (SD) 5040 (HD) and when available 5010 (WEB-DL) are the most important onces. If you only download SD quality shows than only add the category 5030 (SD). No need to add 5040 (HD) & 5010 (WEB-DL) than. This makes searching way more efficient.  There is also a category 5000 (TV) however this contains all TV related shows like anime, foreign, sports, shows, documentary, etc. Lots of witch you probably dont need, and therefor not very efficient to search. In case you are using sports you need to add the category 5060 (Sport) and when you use Anime shows add the category 5070 (Anime).  
Note, some NZB indexers use a different numbering scheme but you should be able to navigate your way through.  

#### Configure Custom Torrent Providers  

* Medusa let you add Torrent providers that are currently not build-in yet. The only requirement is that the Torrent site has an RSS feed. Most of them do, and some let you even customize the feed so only the results you want are added. This makes it very efficient and quick to search.  

![configure-custom-torrent-providers](https://cloud.githubusercontent.com/assets/7928052/13013479/f32ebb46-d1af-11e5-8022-932b2fcc1b96.png)

`Select Provider:`  
Lets you select and add a custom torrent provider.  
`Provider name`  
Lets you set a name for the provider.  
`RSS Url`  
Set here the RSS URL that you have received from the provider.  
`Cookies`  
Here you need to set the settings that are normally included in a cookie. Examples are user-name and password.  
`search element`  
?  

## Subtitles Search  
* This section lets you setup automatic subtitle downloads.  

![subtitles-search](https://cloud.githubusercontent.com/assets/7928052/13013478/f32b5848-d1af-11e5-8dba-3062af8f28d9.png)


`Search Subtitles`  
Enable if you want Medusa to search and download subtitles.  
`Subtitle Languages`  
Add here the subtitle languages you like Medusa to search.  
`Subtitle Directory`  
By default Medusa places the subtitles in your shows folder. With this setting you can store them all in one folder.  
`Subtitle Find Frequency`  
Set how frequent Medusa should search for subtitles in hours.  
`Subtitles History`  
Enable if you like to see an entry on the history page if a subtitle is downloaded.  
`Subtitles Multi-Language`  
Some media players dont support language codes behind the subtitles like Game of Thrones S01E01_EN.srt If that is the case disable this setting and the subtitles will be named without the _EN addition.  
`Embedded Subtitles`  
MKV episodes can have build-in subtitles. If you want to ignore those enable this setting so Medusa can search for subtitles itself.  
`Extra Scripts`  
This allows you to run an script after a subtitle was downloaded.  Can be useful if you want to insert the subtitle into an MKV file etc.  

#### Subtitle Plugins  

* Here you can enable the preferred subtitle providers where Medusa should search for subtitles.  

![subtitles-plugin](https://cloud.githubusercontent.com/assets/7928052/13013550/34339ec2-d1b0-11e5-8d72-3b089ce5b719.png)

#### Plugin Settings

* Some subtitle providers have the ability to use an account for extra functions or removing limitations. Here you can  add your account details.   

![subtitle-accounts](https://cloud.githubusercontent.com/assets/7928052/13013551/34598f6a-d1b0-11e5-9322-cbd1da84e3d0.png)

## Post Processing  
* In this section you can use post process options that Medusa should preform after a episode is downloaded. For example renaming of the file etc. More information can also be found under [Post Processing](https://github.com/pymedusa/Medusa/wiki/Post-Processing)  

![postprocessing-1](https://cloud.githubusercontent.com/assets/7928052/13013585/5c1a412a-d1b0-11e5-8d3c-804ff72ffbdb.png)

`TV Download Dir`  This is the folder that Medusa monitors for newly downloaded files/episodes. Once a new file is found the post-processing starts to move the file to your shows folder and take any other actions that you have configured.   
`Process Episode Method:`  Lets you select what method should be used to move the file to your shows folder. Move is the most used method, but the more advanced [hardlinking](https://en.wikipedia.org/wiki/Hard_link) is recommended in case you want to seed the file with your torrent client.  
`Delete RAR contents`  
?  
`Skip Remove Detection`  
?  
`Extra Scripts`  
Medusa gives you the opportunity to run your own scripts for post-processing. See [post processing](https://github.com/pymedusa/Medusa/wiki/Post-Processing) for more information.  
`Move Associated Files`  
Should Medusa move any files that are downloaded with the episode file like external subtitles etc.?  
`Sync File Extensions`  
Here you can set the extensions of the sync files. Some download clients support sync files. Those files are placed inside the download folder if a file is still downloading. This prevents post processing from starting and prevents errors or incomplete files. However its strongly recommended that you setup your download client to use a separate (temp) folder for files that are still being downloaded. And that only completed files are moved to the TV Download Dir that Medusa monitors.  
`Postpone post processing`  
Enables/disables the above described function of the sync files.  
`Rename .nfo file`  
In case there is already a .nfo file in the show folder Medusa will rename it to .nfo-org to prevent if from being overwritten and causing conflicts.  
`Rename Episodes`  
Enables/disables the function of renaming files as configured under the episode renaming tab.  
`Change File Date`  
?  
`Scan and Process` 
Lets you enable/disable the scanning of the TV Download Dir.  
`Don't delete empty folders `  
Lets you select if Medusa should remove or delete empty folders left after moving the episode file.  
`Auto Post-Processing Frequency`  
This lets you set the time between scans in the TV Download Dir as described above. Dont go below 10 minutes as that can cause detection problem. It can happen that the next scan happens when the previous scan is still moving a file. Than you will receive errors that the file/folder doesn't exist etc.  
`Unpack`  
In case a rar collection is detected in the TV Download Dir, Medusa can unrar them.   
`Use Failed Downloads`  
Lets you enable failed downloads. This gives you the opportunity to mark a nzb/torrent as failed and added to the failed.db, so that the same isn't downloaded again.  
`Delete Failed`  
In case a failed download is detected in the TV Download Dir, Medusa will delete the folder.  

#### Episode Naming  

![episode-naming](https://cloud.githubusercontent.com/assets/7928052/13013589/5f160b2a-d1b0-11e5-9f66-e8fb0b7e0f62.png)

`Name Pattern:`  
Lets you set pre configured renaming schemes or add a custom one.  
`Multi-Episode Style:`  
?  
`Strip Show Year`  
?  
`Custom Air-By-Date`  
Name Air-By-Date shows differently than regular shows    
`Custom Sports`  
Name Sports shows differently than regular shows  
`Custom Anime`  
Name Anime shows differently than regular shows  

#### Metadata  

![metadata](https://cloud.githubusercontent.com/assets/7928052/13013593/621d6d2c-d1b0-11e5-86e1-a6862ec70303.png)

## Notifications

* Medusa lets you send notifications to your favorite home Theater/NAS, Devices or Social media service.


#### Home Theater/NAS  

![home](https://cloud.githubusercontent.com/assets/7928052/13013602/64ae89c2-d1b0-11e5-94fd-168ce77f4c43.png)

`KODI`
A free and open source cross-platform media center and home entertainment system software with a 10-foot user interface designed for the living-room TV.  
`Plex Media Server`  
Experience your media on a visually stunning, easy to use interface on your Mac connected to your TV. Your media library has never looked this good!  
`Plex Media Client`  
`Emby`  
Bringing all of your media together into one place has never been easier. Your Emby Server automatically converts and streams your media on-the-fly to play on any device.  
`NMJ`  
A home media server built using other popular open source technologies.  
The Networked Media Jukebox, or NMJ, is the official media jukebox interface made available for the Popcorn Hour 200-series.  
`NMJv2`  
The Networked Media Jukebox, or NMJv2, is the official media jukebox interface made available for the Popcorn Hour 300 & 400-series.  
`Synology`  
The Synology DiskStation NAS. Synology Indexer is the daemon running on the Synology NAS to build its media database.  
`Synology Notifier`  
Synology Notifier is the notification system of Synology DSM  
`pyTivo`  
pyTivo is both an HMO and GoBack server. This notifier will load the completed downloads to your Tivo.  

#### Devices  

![devices](https://cloud.githubusercontent.com/assets/7928052/13013608/66c22e08-d1b0-11e5-9933-40a62e3ab6ed.png)

`Growl`  
A cross-platform unobtrusive global notification system.  
`Prowl`  
A Growl client for iOS.  
`Libnotify`  
The standard desktop notification API for Linux/*nix systems. This notifier will only function if the pynotify module is installed (Ubuntu/Debian package python-notify).  
`Pushover`  
Pushover makes it easy to send real-time notifications to your Android and iOS devices.  
`Boxcar`  
Universal push notification for iOS. Read your messages where and when you want them! A subscription will be sent if needed.   
`Boxcar2`    
Read your messages where and when you want them!  
`Notify My Android`  
Notify My Android is a Prowl-like Android App and API that offers an easy way to send notifications from your application directly to your Android device.  
`Pushalot`  
Pushalot is a platform for receiving custom push notifications to connected devices running Windows Phone or Windows 8.  
`Pushbullet`  
Pushbullet is a platform for receiving custom push notifications to connected devices running Android and desktop Chrome browsers.  
`Free Mobile`  
Free Mobile is a famous French cellular network provider.
It provides to their customer a free SMS API.  

#### Social  

![social](https://cloud.githubusercontent.com/assets/7928052/13013664/adbad044-d1b0-11e5-9842-cb5d6a2e2c2e.png)

`Twitter`  
A social networking and microblogging service, enabling its users to send and read other users' messages called tweets.  
`Trakt`  
trakt helps keep a record of what TV shows and movies you are watching. Based on your favorites, trakt recommends additional shows and movies you'll enjoy!  
`Email`  
Allows configuration of email notifications on a per show basis.  
Note: If using gmail, and having this error `"ERROR: SMTP AUTH extension not supported by server."` , please enable this https://www.google.com/settings/security/lesssecureapps & try settings : smtp.gmail.com , port 587 , TLS , myemail.email@gmail.com , password
.

## Anime  

#### AnimeDB Settings  

![anidb](https://cloud.githubusercontent.com/assets/7928052/13013665/ade0bf20-d1b0-11e5-847a-5c64544e6496.png)


`Enable`  
Lets you enable the AniDB function/indexer  
`AniDB Username`  
Lets you set the AniDB Username  
`AniDB Password`  
Lets you set the AniDB Password  
`AniDB MyList`  
Do you want to add the Post Processed Episodes to the MyList ?  

#### Look & Feel  

`Split show lists`  
Separate anime and normal shows in groups  

