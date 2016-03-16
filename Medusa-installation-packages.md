
For many Devices there are installation packages compiled by community members. We try to collect as many as we can here. If you know about a package that isn't in the list yet, then please let us know.  


---

###### Windows
* https://github.com/pyMedusa/SickRageInstaller/releases/latest

---

###### Synology
* Add the [Synocommunity](https://synocommunity.com/#easy-install) repository, And Follow those [Instructions](https://github.com/pyMedusa/SickRage/wiki/Switching-your-Synology's-Sickrage-to-the-new-repository#install-sickrage)  

---

###### Arch Linux
* https://aur.archlinux.org/packages/sickrage2-git

---

###### Docker
* https://hub.docker.com/r/linuxserver/sickrage/

---

###### Qnap 
* Download the [qpkg](https://www.dropbox.com/s/j1svazqdi9ieq82/SickBeard-TVRage_151227.qpkg) and follow the installation instructions from the [Qnap Forums](http://forum.qnap.com/viewtopic.php?f=223&t=118366#p525730)
Make sure you select Sickrage and NOT SickrageTV<br/>

---

###### Asustor
* https://www.dropbox.com/s/f016hij9ebw28qd/sickbeard-tvrage_20151227_any.apk  
Make sure you select Sickrage and NOT SickrageTV.

---

###### Thecus

* http://forum.thecus.com/viewtopic.php?f=36&t=9720 (x32&x64)  
Make sure to download Sickrage community Edition package, as sickragetv is the old repo

---

###### ReadyNas

* https://github.com/Mhynlo/rn-sickrage/releases/latest  
* https://github.com/miigotu/sickrage-readynas/blob/master/sickrage_5.1.2_readynas_all.deb (UNTESTED)  

---

## Outdated Packages.!  

Those packages are not yet updated to the new URL, or are simply not maintained anymore. But as long as they are working you should be able to make the switch with manual Git commands.  


Go into the Sickrage folder and do :  

```
git remote set-url origin https://github.com/pyMedusa/SickRage.git
git fetch origin
git reset --hard origin/master
```

In case thats not possible, you can try to switch the [dirty](https://github.com/pyMedusa/SickRage/wiki/Sickrage-installation-packages#switching-the-dirty-way) way.

---


###### D-Link NAS
* ~~http://forums.dlink.com/index.php?topic=62238.0~~  
* ~~http://dlink.vtverdohleb.org.ua/Add-On/#SickRage~~  

---

###### amahi  
* ~~https://www.amahi.org/apps/sickrage~~  

---

###### Geexbox

* ~~http://download.openbricks.org/utilite/python-sickrage_4.0.22%2bgit-e6c4cfd65-1_armv7.opk~~  

---



--



##Switching the Dirty way.  

As some installers are outdated or not maintained anymore, switching can be a little frustrating.
In most cases you can use those old packages in combination with manual Git commands to make the switch.
However in some cases this is not possible. For those there is a `Dirty` way to switch.

* 1 Run the outdated installer and install sickrage from the old Repo.
* 2 Shutdown Sickrage.
* 3 Download the latest Sickrage package from the [New Repo](https://github.com/pyMedusa/SickRage/archive/master.zip).
* 4 Unzip and overwrite the old files on your device.
* 5 Start Sickrage again.

Thats it. 
However this method is meant as a last resource, and should only be used if all other methods fail.



