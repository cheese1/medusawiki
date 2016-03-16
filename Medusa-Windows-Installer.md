## Introduction ##

---

For many novice users installing Medusa on a Windows machine can be confusing.
Therefore we have created a Windows installer to simplify the process. This installer will download all the necessary files and automatically install them for you.
It also will take care of creating a service, so that Medusa will automatically start with Windows.
Both x32 and x64 bit installations are supported and automatically recognized.    

For more detailed information checkout https://github.com/VinceVal/SickRageInstaller#sickrageinstaller  

## Network drive mappings ##

The installer uses a service (account) to run Medusa automatically on startup. This is a different account than your Windows user account witch you use to login to Windows. Meaning that any network drive mappings are not existing for that (service) account and need to be created.
Or edit the service to run with another [account](https://technet.microsoft.com/en-us/library/cc755249.aspx) that has the network drive mappings setup.
You can manually change the account from the command prompt (administrative rights) with the below commands. :  
```
sc config "SickRage" obj= "username" password= "password"
sc restart Medusa
```  

If you are unable to get those setup correctly, you can always disable the service and start Medusa manually. Medusa will then run as the user that is logged in to Windows. Alternatively you can also install Medusa [manually](https://github.com/pyMedusa/SickRage/wiki/SickRage-Windows-Installer/_edit#manual-installation-guides-for-windows)  

---

## Installing Medusa on Windows ##

Head over to the [Medusa Package Installer](https://github.com/VinceVal/SickRageInstaller/releases) and download the latest release.  
(Special thanks to VinceVal for compiling this installer.)  

Browse to the folder/location where you have placed the installer file and execute/run it.  
(You might get a warning from `users account control` that the program is `Unknown`. Just ignore the warning, and click on `OK`.)  

--
![1](https://cloud.githubusercontent.com/assets/7928052/9738295/15735238-564b-11e5-844e-74551c2e312a.png)  

You will be greeted by the welcome screen.
Click on `Next >` to processed with the installation.  

--

![2](https://cloud.githubusercontent.com/assets/7928052/9738296/1573a828-564b-11e5-9f2e-09a320ad02ee.png)

The next window lets you select the destination folder where you want Medusa to be installed. the default is `C:\SickRage`  
Use `Browse...` if you would like to change that location. Or enter the destination manually in the text-field.  
Click on `Next >` to to proceed with the installation.  

--

![3](https://cloud.githubusercontent.com/assets/7928052/9738298/1576b27a-564b-11e5-94a9-1df9408c0fe7.png)

The next window will ask if you would like a shortcut to be created in your start menu.  
If not than check the check-box `Don't create a Start Menu folder`  
Click on `Next >` to to proceed with the installation.  

--

![4](https://cloud.githubusercontent.com/assets/7928052/9738293/15725f7c-564b-11e5-997b-edf09e8f50bf.png)

The next window will let you set the port on witch Medusa will run. The default is `8081` and its advised not to change this, unless you have a good reason for it.  
Click on `Next >` to to proceed with the installation.  

--

![6](https://cloud.githubusercontent.com/assets/7928052/9738294/1572e820-564b-11e5-83d8-d5066919f89e.png)

The next window will ask if you would like to create a shortcut for Medusa on your desktop.  
For ease its recommended to create an shortcut on the desktop. But you can also decide to save the URL as a bookmark/favorite in your browser later.  
Click on `Next >` to to proceed with the installation.  

--

![7](https://cloud.githubusercontent.com/assets/7928052/9738297/15761806-564b-11e5-83b2-9061f3ddc0db.png)

The next window shows you an overview of the settings you have selected and the dependencies that will be installed together with Medusa.  
(Those dependencies are needed to run and update Medusa on your Windows machine.)  
Click on `Install` to to processed with the installation.  

--

![8](https://cloud.githubusercontent.com/assets/7928052/9738301/158b3088-564b-11e5-881d-029e5a13d73b.png)

The next window will start downloading the necessary files that are going to be used to install Medusa.  

--

![9](https://cloud.githubusercontent.com/assets/7928052/9738302/1590b3e6-564b-11e5-9c26-4eae91708094.png)

The next window will show you the installation of the downloaded files, this can take a moment depending on your machine.  

--

![10](https://cloud.githubusercontent.com/assets/7928052/9738299/158adaca-564b-11e5-8c6c-42e12a756d7b.png)

When the installing is complete you will get the `Finish` screen. Simply click on `Finish` to complete the installation.  
Congratulations, you have successfully installed Medusa.! :+1:

--

![11](https://cloud.githubusercontent.com/assets/7928052/9738300/158b1602-564b-11e5-979c-a1ee277d6a74.png)

Now you can access Medusa by opening your favorite browser and go to http://localhost:8081 to open Medusa's Web-interface.

--

---  

## Manual installation guides for Windows ##

In case you prefer to do the installation manually, than you can have a look at the below guides. Note that Cheetah isn't necessary anymore, so you don't have to install it.  

`Official Windows installer:`  
https://github.com/VinceVal/SickRageInstaller

`Windows:`  
http://www.htpcguides.com/install-sickrage-windows-usenet-torrent-tv/

`System Service on All Windows Versions:`  
http://www.htpcguides.com/create-sickrage-system-service-windows-versions/

`Windows System Service v2:`  
http://www.htpcguides.com/create-sickrage-windows-system-service-v2/

