## Frequently Asked Questions & Answers (FAQ)

**Does Sickbeard TVRage support NAS hardware?**

Yes. There are pre-built NAS versions of Sickbeard:
* [For QNAP](http://bit.ly/1j5WtdN) 
* [For Asustor](http://bit.ly/1pFr1rW)

**Error: Rar Not Supported: No suitable RAR unpacker installed**

Sickbeard has ability to unpack RAR-archived releases but is distributed without OS-specific UNRAR binary. If you get this error, your need to download RAR binary and place it in _SickBeard-TVRage/lib/unrar2/_
* RAR Binary for Windows: [UNRAR for Windows] (http://www.rarlab.com/rar/unrarw32.exe)
* RAR Binary for Mac OS X: [UNRAR for OS X] (http://www.rarlab.com/rar/rarosx-5.1.b3.tar.gz) - then _chmod +x unrar_ in Terminal.
* RAR Binary for Linux x64: [UNRAR for Linux x64] (http://www.rarlab.com/rar/rarlinux-x64-5.1.b3.tar.gz)
* RAR Binary for FreeBSD: [UNRAR for FreeBSD] (http://www.rarlab.com/rar/rarbsd-5.1.b3.tar.gz)

**Error while searching ..., skipping: 'sqlite3.Connection' object has no attribute 'action'**

**Error while searching ..., skipping: local variable 'epObj' referenced before assignment**

**Error while searching ..., skipping: 'NoneType' object is not iterable'''**

Close Sickbeard, then delete _cache.db_ in your SickBeard directory. This may solve the problem. 

If you still have the same issues, search the repository for the error message (without the specific provider name) and if there's an open issue, copy your log (at Debug level). If no such issue exists, open a new one. 