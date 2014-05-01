## Frequently Asked Questions & Answers (FAQ)

**Does Sickbeard TVRage support NAS hardware?**

Yes. There are pre-built NAS versions of Sickbeard:
* [For QNAP](http://bit.ly/1j5WtdN) 
* [For Asustor](http://bit.ly/1pFr1rW)
* [For Thecus] (http://bit.ly/1fAJukV)

**Error: Rar Not Supported: No suitable RAR unpacker installed**

Sickbeard has ability to unpack RAR-archived releases but is distributed without OS-specific UNRAR binary. If you get this error, your need to download RAR binary and place it in _SickBeard-TVRage/lib/unrar2/_
* RAR Binary for Windows: [UNRAR for Windows] (http://www.rarlab.com/rar/unrarw32.exe)
* RAR Binary for Mac OS X: [UNRAR for OS X] (http://www.rarlab.com/rar/rarosx-5.1.b3.tar.gz) - then _chmod +x unrar_ in Terminal.
* RAR Binary for Linux x64: [UNRAR for Linux x64] (http://www.rarlab.com/rar/rarlinux-x64-5.1.b3.tar.gz)
* RAR Binary for FreeBSD: [UNRAR for FreeBSD] (http://www.rarlab.com/rar/rarbsd-5.1.b3.tar.gz)

**Error while searching ..., skipping: 'NoneType' object is not iterable'''**

Close Sickbeard, then delete _cache.db_ in your SickBeard directory. This may solve the problem. 

If you still have the same issues, search the repository for the error message (without the specific provider name) and if there's an open issue, copy your log (at Debug level). If no such issue exists, open a new one. 

**How to enable debug logging for better issue logging

Shutdown Sickbeard, and edit the config.ini in your favourite editor. Add debug=1 in the configuration in the very first line and start sickbeard. 
Once the error happens again, use the logfile, paste it on [pastebin] (http://pastebin.org) or an equivalent site and create, or update your issue.

Don't forget to remove the debug line once you're done considering debug can be a bit spammy.

**Cannot update Sickbeard-TVRage, Git gives FETCH_HEAD error.**

Some times on your local Sickbeard distribution have been changed. 

On Windows, OS X: Use the following commands:
* git stash
* git stash drop
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