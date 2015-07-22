####Episode Status#

SickBeard uses a variety of Episode Status settings to manage your TV Shows.

The Status Types reflect a number of different episode and show states within SickRage. It can have an effect on:  

* Wanted State
* Downloaded State
* Individual Episode Count (**\##** / ## episodes downloaded)
* Total Episode Count (\## / **\## episodes downloaded**)

#####Status Types#

The different Status Types reflect what stage and state any particular episode is in:  

* **Skipped**
    * is not wanted for download
    * is not downloaded
    * has a zero count toward Individual Episode Count
    * is included in Total Episode Count  (except for Specials)  
* **Wanted**
    * is wanted
    * is not downloaded
    * has a zero count toward Individual Episode Count
    * is included in Total Episode Count  
* **Snatched**
    * is wanted
    * has been found and started to download
    * has a zero count toward Individual Episode Count
    * is included in Total Episode Count  
* **Downloaded ([Quality])**
    * has been found and completed download
    * has a one count toward Individual Episode Count
    * is included in Total Episode Count
    * this can be "Low" or "Best"
        * "Low" shades the Episode **pink** and exists when there is a higher quality still desired for download when the Custom Preset is used with Initial and Archive qualities
        * "Best" shades the Episode **green** and exists when the download matches a desired Quality in a Preset Quality setting, or when the download matches the _highest_ desired Archive Quality in a Custom setting  
* **Archived**
    * this is a manual setting for keeping track of physical episodes (ie. on a disc you own) when using SickBeard as a collection manager
    * has a one count toward Individual Episode Count
    * is included in Total Episode Count  
* **Ignored**
    * is not wanted
    * has a zero count toward Individual Episode Count
    * is not included in total episode count

