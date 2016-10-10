=========================
[ [Quality Settings] ](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#quality-settings) [ [Quality detection/determination] ](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#quality-detectiondetermination) [ [Quality names to recognize the Quality of a file] ](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#quality-names-to-recognize-the-quality-of-a-file) [ [Difference between Preset and Custom Qualities] ](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#difference-between-preset-and-custom-qualities) [ [Preset Qualities] ](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#preset-qualities) [ [Custom Qualities] ](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#custom-qualities) [ [Example Advanced Custom Qualities] ](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#example-advanced-custom-qualities) [ [Media Extensions] ](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#media-extensions)

=========================


## 2016-01-22 Important Update!

There have been some recent changes/modifications to the qualities. For more info check the temporary link below.  

https://github.com/pymedusa/Medusa/wiki/Qualities-Changes


## Quality Settings

One of the most important settings is the quality setting for your shows. This informs Medusa of the quality that it should search for on your favorite NZB/Torrent indexer. Make sure that you understand the processes of how the quality detection works, and how to set it up correctly.   
  

##Quality detection/determination  

To understand the quality setting, you first need to understand how the quality is detected/determent.
When Medusa starts a search for your shows, it will collect all the titles from those results. The next step is checking those titles for quality names. (Examples of those names are x264 or 720p etc.) From those found quality names Medusa determinates the quality of a file. For HDTV quality the title needs to contain `720p` + `HDTV` + `x264` = `HD TV` Quality.
In the list below you will find what a title needs to contain to be marked as a certain quality.
 
##Quality names to recognize the Quality of a file:  

This shows you what a title needs to contain to be recognized as a Quality in Medusa.

* **SD TV**
    * File name contains `PDTV` or `HDTV` or `DSR` or `TVRIP` or `SATRIP`, and is `xvid` or `x264` or `h264`, but not `720p` or `1080p` or;
    * File name contains `web.dl` or `webrip`, or is `xvid` or `x264` or `h264`, but not `720p` or `1080p`
* **SD DVD**
    * File name contains `DVDRip` or `B\[R\D]Rip`, and is `xvid` or `divx` or `x264`or `h264`, but not `720p` or `1080p`
* **HD TV**
    * File name contains `720p` and `HDTV` and `x264` or `h264`, and not `1080p` or;
    * File name contains `hr.ws.pdtv.x264`, and not `1080p`
* **RawHD TV**
    * File name contains `720p` or `1080i` and `HDTV` and `MPEG-2` or;
    * File name contains `1080i.HDTV` and `h264`
* **1080p HD TV**
    * File name contains `1080p` and `HDTV` and `x264`
* **720p WEB-DL**
    * File name contains `720p` and `web.dl` and `h264` or `x264` or;
    * File name contains `720p` and `iTunes` and `h264` or `x264` or;
    * File name contains `720p` and `webrip` and `h264` or `x264`
* **1080p WEB-DL**
    * File name contains `1080p` and `web.dl` and `h264` or;
    * File name contains `1080p` and `iTunes` and `h264` or;
    * File name contains `1080p` and `webrip` and `x264`
* **720p BluRay**
    * File name contains `720p` and `Bluray` or `HDDVD` or `B\[R\D]Rip` and `x264` or `h264`
* **1080p BluRay**
    * File name contains `1080p` and `Bluray` or `HDDVD` or `B\[R\D]Rip` and `x264` or `h264` 

Note: All `RIP` qualities can have either `rip` or `mux` in the filename. ( Example: WEBRip and WEBMux )

(All of these settings will find files with the required [Media Extensions](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#media-extensions).)  

This quality determination also apply's to imported/already downloaded files. So when you rename your files and they dont include the valid quality names, they can be detected as `Unknown` by Medusa.!  

  
##Difference between Preset and Custom Qualities

Now that you are aware of what a title needs to contain, we can proceed with actually choosing and setting a quality. There are two ways to setup your wanted quality's. [Preset Qualities](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#preset-qualities) witch are pre-configured quality options that you can select or [Custom Qualities](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#custom-qualities) if you want to set your own advanced wanted quality's.  


##Preset Qualities  

You can set more than one Present quality per show. But be aware that the first match that Medusa finds on the indexer will be snatched/downloaded. That can be any of the quality's you have set.!  

* **Any**
    * Will match any available Quality
* **SD**
    * SD TV or SD DVD
* **HD720p**
    * HD TV or 720p WEB-DL or 720p BluRay
* **HD1080p**
    * 1080p HD TV or 1080p WEB-DL or 1080p BluRay
* **HD**
    * HD TV or 1080p HD TV or 720p WEB-DL or 1080p WEB-DL or 720p BluRay or 1080p BluRay
* **Custom**
    * Custom Quality gives you the Allowed and Preferred menus, outlined under [Custom Qualities](https://github.com/pymedusa/Medusa/wiki/Quality-Settings#custom-qualities)  
  

Lets give you some real world examples that you need to consider selecting the quality.
For new/popular shows, you can basically set every quality as there are (probably) released in all of those quality's.
However it might get problematic for more "exotic" and older shows. Maybe those shows where never released as HD/Bluray but only as SD/DVDRip. Needles to say if you only set HD quality for those shows then there is a good chance that Medusa wont find any downloads. So the smart thing is to chose more or `Any` as quality. But most efficient is a old fashion manual search on the indexer to see in what quality the releases are uploaded.

##Custom Qualities

The Custom Quality gives you a new menu where you can use two special _categories_ and one special _setting_ to allow for additional customization of your desired Medusa Quality Settings: the **Allowed** Quality and **Preferred** Quality Categories, and the **Archive on First Match** setting.

**Allowed** Quality allows you to select a custom set of Qualities that instructs Medusa to download _only the first_ matched Quality

**Preferred** Quality allows you to select a _second_ set of Qualities that instructs Medusa to download _any successively better_ matched Quality, except where;

**Archive on First Match** Setting allows you to instruct Medusa to download _only the first_ matched **Preferred** Quality, even if multiple Qualities are selected
  

##Example Advanced Custom Qualities

_I Only Want WEB-DLs_  
Use the Custom setting to choose the Allowed Qualities of 720p WEB-DL and 1080p WEB-DL.  Nothing but WEB-DLs for you!

_I'm an Archivist, give me it all!_  
Use the Custom setting to choose the Allowed Quality of SD, and choose every other Quality under the Preferred Qualities.  As a fair warning: This will download **every** release that comes out for that show in order of increasing quality, as they are released.

_I want a version for watching now, and at least one 1080p quality for a long-term collection_  
Say you want something that would normally fall under the Preset Quality of HD 720p, but you also would like to have a 1080p version for your long-term collection.
1) Choose the Preset Quality - HD 720p  
2) Change the Preset Quality to Custom.  You'll see that all of the HD 720p Qualities are chosen under Allowed  
3) Select the Preferred Qualities of HD 1080p, 1080p WEB-DL, and 1080p BluRay  
    * This _will_ download progressively higher quality 1080p releases until Medusa reaches 1080p BluRay, only then will it stop  

_Its a great show, I've got to get **Any** version for watching now, and **only one** 720p quality for a long-term collection_  (For the record, I call this the "Game of Thrones" Setting)  
So you need to watch it now and you'd be happy to watch any version quick! But its so good you'll watch it again and again, and your collection revolves around 720P episodes.  
1) Choose the Preset Quality - Any  
2) Change the Preset Quality to Custom.  You'll see that all of the Any Qualities are chosen under Allowed  
3) Select the Preferred Qualities of HD 720p, 720p WEB-DL, and 720p BluRay  
4) Save the page (this will activate the Archive on First Match feature) and then come back to the same Edit page  
5) Check off the **Archive on First Match** Setting  

This will allow you to get your grubby little hands on the first release that hits the interwebz, and as soon as **any one** of the 720p qualities is released, Medusa will download the **first only** and then stop!  No multiple Preferred downloads for you, just viewing pleasure :)  
  
  
##Media Extensions
`avi`, `mkv`, `mpg`, `mpeg`, `wmv`, `ogm`, `mp4`, `iso`, `img`, `divx`, `m2ts`, `m4v`, `ts`, `flv`, `f4v`, `mov`, `rmvb`, `vob`, `dvr-ms`, `wtv`, `ogv`, `3gp`
