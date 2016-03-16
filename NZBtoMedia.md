## What is NZBtoMedia.?

NZBtoMedia is a collection of scripts for [post-processing](https://github.com/pyMedusa/SickRage/wiki/Post-Processing).  
Normally Medusa scans the download folder for new files/downloads every 10 minutes. However that prevents the hard disks from going into sleep/hibernation. Scripts on the other hand let Medusa instantly know if a download was completed. Therefore the scanning of the `tv download folder` isn't necessary anymore.
Another advantage is that other [post-processing](https://github.com/pyMedusa/SickRage/wiki/Post-Processing) options can be done, before the file is sent to Sickrage. But most of those options are already included in Medusa, so you probably wont use them.
Last and probably the MOST important reason, it supports failed downloads. Meaning that when your client fails to download the file a notification gets sent to Medusa and a new search gets started, with hopefully now a valid file.  

## Before you start

* Enable inside Medusa :  `Settings` --> `Search Settings` --> `Use Failed Downloads` !  
* Make sure the permissions and file ownership are correctly set.  
* Windows users will need to install the [pywin32](https://sourceforge.net/projects/pywin32/files/pywin32/) extensions to run NZBtoMedia.   

## With what client can i use NZBtoMedia.?

With every client that allows to run a script after the download. Most famous is probably SABnzbd, but also Synology's Download Station and Transmission support this.
For more info see [NZBtoMedia's Repo](https://github.com/clinton-hall/nzbToMedia/wiki#downloaders)  

### Installation for torrent Clients :  

* [Deluge](https://github.com/clinton-hall/nzbToMedia/wiki/deluge)  
* [µTorrent](https://github.com/clinton-hall/nzbToMedia/wiki/utorrent)  
* [Transmission](https://github.com/clinton-hall/nzbToMedia/wiki/transmission)  
* [rTorrent](https://github.com/clinton-hall/nzbToMedia/wiki/rtorrent)  
* [Download Station (Synology)](https://github.com/clinton-hall/nzbToMedia/wiki/Download-Station)  
* [vuze](https://github.com/clinton-hall/nzbToMedia/wiki/vuze)  

## How to setup NZBtoMedia with NZBget.?  

The good news is that NZBget has NZBtoMedia support build-in to the program. This allows for easy configuration.  
First you need to make sure that NZBget points to the NZBtoMedia files. Sometimes the files are included in the NZBget/Scrips folder. However if they are not you have two options. Manually download the latest NZBtoMedia [package](https://github.com/clinton-hall/nzbToMedia/archive/master.zip) and unpack them there. Or point to the NZBtoMedia folder included within Sickrage. This can be done in NZBGet by going to Settings --> PATHS --> `ScriptDir`.

==

![naamloos](https://cloud.githubusercontent.com/assets/7928052/13014408/f9a0cfb0-d1b3-11e5-915a-bc695e77b4ba.png)

The first step is to do the basic configuration of NZBget. So add your Usenet provider and download path etc.  
Go to `PATHS` and fill-in your download Path that Sickrage monitors under `MainDir` or `DestDir` depending on your preference.   


== 

![4](https://cloud.githubusercontent.com/assets/7928052/13014407/f99d1d34-d1b3-11e5-9fc7-7366fb786ebe.png)

Go to `CATEGORIES` in the Settings. Push on Add another `categorie` at the bottom of the page to add a new categorie. (or re-use an already existing categorie)  

* Under `name` add `tv`  
* Under `Postscript` chose `nzbToSickBeard`  

And save the settings.  

==

![2](https://cloud.githubusercontent.com/assets/7928052/13014403/f995f324-d1b3-11e5-9917-fdcb71d9aabe.png)

Next we need to setup the settings for the nzbToSickBeard script itself.  
Go to `nzbToSickBeard` in the Setting. Now change/add : 

* `sbcategory`        leave set to `tv` (or change if you changed it in Medusa.)  
* `sbhost`            leave to `localhost` (or enter IP if Sickrage runs on different machine)  
* `sbport`            Enter the port on witch Medusa is running.  
* `sbusername`        Enter the username if Medusa requires login.  
* `sbpassword`        Enter the password if Medusa requires login.  
* `sbprocess_method`  Use your preferred process method.  

(more advanced settings can be set, but make sure you understand there functions.!)  

And save the settings.  

==

![3](https://cloud.githubusercontent.com/assets/7928052/13014404/f99896ec-d1b3-11e5-8d84-7bab89f35121.png)

By default NZBget will create a sub-directory with the name of the category. And some users might not like that. To change this go to `INCOMING NZBS` under settings and set `appendedcategorydir` to `NO`  

And save the settings.  

## How to setup NZBtoMedia with SABnzbd.?

If you are lucky you might already be familiar with the SABtoSickbeard script. The setup is almost identical to that.  
But first we need to configure the autoProcessMedia.cfg to include your user-name/passwords/ip/port etc.  

( SABtoSickbeard works but is outdated and doesn't support failed downloads.)

==

## Configure autoProcessMedia.cfg for SABnzbd

First locate your `contrib` folder where NZBtoMedia is located, or download/install it on a location you prefer. Included in the NZBtoMedia folder is a file called `autoProcessMedia.cfg.spec`.  
Copy the `autoProcessMedia.cfg.spec` file and rename it to `autoProcessMedia.cfg` in the same folder. 
Now open the `autoProcessMedia.cfg` with your favorite editor.   

Go to the `[SickBeard]` section and add/change the following settings. :  
  
`[SickBeard]`  
  
* `enabled = 0`            (Change the `0` to `1` to enable Sickrage)  
* `host = localhost`       (Change IP number if Sickrage runs on a different device)  
* `port = 8081`            (Change the port to the one that your Medusa install uses)   
* `username =`             (Add your username if you have enabled login in Sickrage)  
* `password =`             (Add your password if you have enabled login in Sickrage)  
* `fork =`                 (Only replace `auto` with `sickrage`if detection problems)  

Go to the `[Nzb]` section and add/change the following settings. :    

`[Nzb]`  

* `clientAgent = sabnzbd`    (Add sabnzbd)  
* `sabnzbd_host = localhost` (Change/add the IP number if needed)  
* `sabnzbd_port = 8081`      (Change the port if needed)  
* `sabnzbd_apikey` =         (Add the API key of sabnzbd)  
* `default_downloadDirectory = "/downloads"` (add your tv download dir)  

(Note: There are more advanced settings that you can modify, but they are not needed in most cases.)

Thats it. Now save the file.  


## Configure nzbtosickbeard.py with SABnzbd

![02a04048-5bab-11e5-9f25-a14f4fa42566](https://cloud.githubusercontent.com/assets/7928052/13014406/f99c4288-d1b3-11e5-8f68-dde9be0fe691.png)

First step is to let SABnzbd know where the NZBtoMedia scripts are located.  
Do this by going to. : `Config` -> `Folders` -> `User Folders` -> `Post-Processing Scripts Folder`  
Now browse to the location where they are located and save the new path.  

==

![1](https://cloud.githubusercontent.com/assets/7928052/13014405/f99ac868-d1b3-11e5-841f-d566aed5f04c.png)

The second step is to setup the categories. When Medusa sends an nzb to SABnzbd it adds a tag. the defealt is `tv`. The Categories allow to run a script when a certain tag is sent/found by SABnzbd.  
In our case we want to do this with the tag `tv` that Medusa uses.  
Go to : `Config` -> `Categories`  

See if there is already a category called `tv` and if not create one.  
Than select in the `Script` column "nzbToSickBeard.py" as the script needs to be executed after the file was downloaded by SABnzbd. (In case there are no scripts the select, than make sure you have sett the correct scripts folder mentioned in the previous step.)  

The "Folder/Path" doesn't need to be set, but if you are having problems than set to the location where you want your movies extracted to (Usually just set this as tv to move files to a tv sub-directory in the download completed directory)


==

**The next steps are not necessary but recommended.** 


![3](https://cloud.githubusercontent.com/assets/7928052/13014409/f9abfca0-d1b3-11e5-93c8-ad8e47836327.png)

Go to : `Config` -> `Switches` -> `Post-Process Only Verified Jobs (off)`  
And deselect, in order to allow for snatching of the next best release. (mainly used with CouchPotatoServer if a download fails.)  

==

![4](https://cloud.githubusercontent.com/assets/7928052/13014410/f9ae3d94-d1b3-11e5-9713-896c133465c8.png)
With the release of SABnzbd version 0.7.5 a new special parameter named "empty_postproc" was introduced. This allows for better handling of failed downloads.  
Go to : `Config` -> `Special` -> `empty_postproc (on)`  
And change the setting to off.   

==

A successful run of the script should look like this in SABnzbd. :  

![5](https://cloud.githubusercontent.com/assets/7928052/13014411/f9afd71c-d1b3-11e5-89bf-643f2bf13603.png)

