###Quality Settings#
A major part of Medusa's functionality is built around the Quality Settings.  The Quality Settings allow you to instruct Medusa to Snatch a show's release, or leave it alone.
  
  

####Qualities#
To begin, the basic 'unit' of Quality Settings are the individual Qualities.  The Qualities available are:

* SD TV
    * File name contains PDTV or HDTV or DSR or TVRIP, and is xvid or x264 or h264, but not 720\[i/p] or 1080\[i/p]  
or;
    * File name contains web.dl or webrip, or is xvid or x264 or h264, but not 720\[i/p] or 1080\[i/p]
* SD DVD
    * File name contains DVDRip or B\[R\D]Rip, and is xvid or divx or x264, but not 720\[i/p] or 1080[i/p]
* HD TV
    * File name contains 720p and HDTV and x264, and not 1080\[i/p]  
or;
    * File name contains "hr.ws.pdtv.x264", and not 1080\[i/p]
* RawHD TV
    * File name contains 720p or 1080i and HDTV and MPEG-2  
or;
    * File name contains "1080i.HDTV" and h264
* 1080p HD TV
    * File name contains 1080p and HDTV and x264
* 720p WEB-DL
    * File name contains 720p and web.dl and h264  
or;
    * File name contains 720p and iTunes and h264  
or;
    * File name contains 720p and webrip and x264
* 1080p WEB-DL
    * File name contains 1080p and web.dl and h264  
or;
    * File name contains 1080p and iTunes and h264  
or;
    * File name contains 1080p and webrip and x264
* 720p BluRay
    * File name contains 720p and Bluray or HDDVD or B\[R\D]Rip and x264
* 1080p BluRay
    * File name contains 1080p and Bluray or HDDVD or B\[R\D]Rip and x264  

All of these settings will find files with the required Media Extensions

These Settings are broken into two main parts: Preset Qualities and Custom Qualities
  
  

####Preset Qualities#

Preset Qualities are groups of Qualities where the **first** Quality that is found which matches will satisfy the download request.

* Any
    * Will match any available Quality
* SD
    * SD TV or SD DVD
* HD720p
    * HD TV or 720p WEB-DL or 720p BluRay
* HD1080p
    * 1080p HD TV or 1080p WEB-DL or 1080p BluRay
* HD
    * HD TV or 1080p HD TV or 720p WEB-DL or 1080p WEB-DL or 720p BluRay or 1080p BluRay
* Custom
    * Custom Quality gives you the Allowed and Preferred menus, outlined below  
  
  

####Custom Qualities#

The Custom Quality gives you a new menu where you can use two special _categories_ and one special _setting_ to allow for additional customization of your desired Medusa Quality Settings: the **Allowed** Quality and **Preferred** Quality Categories, and the **Archive on First Match** setting.

**Allowed** Quality allows you to select a custom set of Qualities that instructs Medusa to download _only the first_ matched Quality

**Preferred** Quality allows you to select a _second_ set of Qualities that instructs Medusa to download _any successively better_ matched Quality, except where;

**Archive on First Match** Setting allows you to instruct Medusa to download _only the first_ matched **Preferred** Quality, even if multiple Qualities are selected
  
  

####Basic Examples for Using Quality Settings#

Say you have a show which is popular and easily available, and you want something HD, but not too big of a file size.  Your best Quality Setting choice may be the **Preset Quality** - **HD 720p**.  With that Preset Setting, you'll be able to grab a quick 720p release and keep your file size down.

On the flip side of the coin, there are some shows out there that are tough to find, and releases are mixed and unreliable.  Your best Quality Setting choice may be the **Preset Quality** - **Any**.  That way, no matter what, when your show gets released, you'll grab a copy.

Maybe you're a quality freak and you need to get your 1080p fix with your newest and swankiest TV.  If its just got to be the best for you, your best Quality Setting choice may be the **Preset Quality** - **HD 1080p**.
  
  

####Advanced Custom Examples#

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
  
  
  
####Media Extensions#
'avi', 'mkv', 'mpg', 'mpeg', 'wmv', 'ogm', 'mp4', 'iso', 'img', 'divx', 'm2ts', 'm4v', 'ts', 'flv', 'f4v', 'mov', 'rmvb', 'vob', 'dvr-ms', 'wtv', 'ogv', '3gp'
