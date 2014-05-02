###Quality Settings#
A major part of SickBeard's functionality is built around the Quality Settings.  The Quality Settings allow you to instruct SickBeard to Snatch a show's release, or leave it alone.

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

####Custom Qualities#

Custom Qualities use two special _categories_ and one special _setting_ to allow for additional customization of your desired SickBeard Quality Settings: the **Initial** Quality and **Archive** Quality Categories, and the **Archive on First Match** setting.

**Initial** Quality allows you to select a custom set of Qualities that instructs SickBeard to download _only the first_ matched Quality

**Archive** Quality allows you to select a _second_ set of Qualities that instructs SickBeard to download _any successively better_ matched Quality, except where;

**Archive on First Match** Setting allows you to instruct SickBeard to download _only the first_ matched **Archive** Quality, even if multiple Qualities are selected



####Media Extensions#
'avi', 'mkv', 'mpg', 'mpeg', 'wmv', 'ogm', 'mp4', 'iso', 'img', 'divx', 'm2ts', 'm4v', 'ts', 'flv', 'f4v', 'mov', 'rmvb', 'vob', 'dvr-ms', 'wtv', 'ogv', '3gp'
