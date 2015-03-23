## Frequently Asked Questions & Answers (FAQ)

**Where are the LOG files?**

It's inside SickRage folder
/SickRage/Logs/sickrage.log

Note: Synology users can use WinSCP to gain access/browse to the root where the Sickrage log is located.
          /volume1/@appstore/sickbeard-custom/var/Logs/sickrage.log

**Does SickRage support NAS hardware?**

Yes. There are pre-built NAS versions of SickRage:
* [For QNAP](http://bit.ly/1j5WtdN) 
* [For Asustor](http://bit.ly/1pFr1rW)
* [For Thecus] (http://bit.ly/1fAJukV)

**Error: Rar Not Supported: No suitable RAR unpacker installed**

SickRage has the ability to unpack RAR-archived releases but require the external `unrar` command on Linux, Mac, FreeBSD and other Unix OS. In Windows, it use unrar.dll(x86) or unrar64.dll(x86_64) which are included in SickRage.

If you get this error, your need to make sure unrar is installed and available into PATH.

To install `unrar`:
* Fedora:
  * `yum install -y unrar` Need [RPMFusion repo](http://rpmfusion.org/) installed.
* Ubuntu, Mint, Debian(non-free repo):
  * `apt-get install unrar`
* openSUSE:
  * `zypper install unrar`
* Arch:
  * `pacman -S unrar`
* Mac (brew):
  * `brew install unrar`
* Mac (ports):
  * `port install unrar`

**Releases have different show name than the one in SickRage, and are not snatched.**

If you encounter releases that use different show name than the one from TVDb or TVRage that SickRage uses, you can add a Scene Exception to your show [Go to Show, Edit Show] with the name that the releases are using. 

A common case is when TVDb show has a name without a year (i.e. _Revolution_), while releases add year of show premiere (i.e. _Revolution (2012)_)

SickRage will now recognize this show by the official and all scene exception names you provide. 

**Error while searching ..., skipping: 'NoneType' object is not iterable'''**

Close SickRage, then delete _cache.db_ in your SickRage directory. This may solve the problem. 

If you still have the same issues, search the repository for the error message (without the specific provider name) and if there's an open issue, copy your log (at Debug level). If no such issue exists, open a new one. 

**How to enable debug logging for better issue logging**

Shutdown SickRage, and edit the config.ini in your favourite editor. Add debug=1 in the configuration in the very first line and start sickRage. 
Once the error happens again, use the logfile, paste it on [pastebin] (http://pastebin.org) or an equivalent site and create, or update your issue.

Don't forget to remove the debug line once you're done considering debug can be a bit spammy.

**Reverse Proxy is not working.**

Make the following changes to your config.ini file:
* _web_host=0.0.0.0_
* _localhost_ip=[your LAN IP]_

**Cannot update SickRage, Git gives FETCH_HEAD error.**

Some times on your local SickRage distribution have been changed. 

On Windows, OS X: Use the following commands:
* git reset --hard
* git pull

On Synology:
* Stop SB using Syno package tool
* Remove current sourcecode
* _cd /volume1/@appstore/sickbeard-custom/var_
* _rm -Rf SickBeard_
* Fresh clone
** /volume1/@appstore/git/bin/git clone https://github.com/echel0n/SickBeard-TVRage.git SickBeard
* Start SB using Syno package tool
* Enjoy!