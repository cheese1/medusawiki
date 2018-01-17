Luckily this is very easy and can be performed with a few simple steps.  

Summary:  

1) Go into Medusa and make a backup.  
2) Go to the Synology Package Center and remove Medusa.  
3) Then Reinstall Medusa, but now in the installation screen/wizard add the new URL.  
`git://github.com/pymedusa/Medusa.git`  
4) Restore your backup, and restart Medusa.  

That's it. :+1:  

Note: By default the synocommunity sickbeard-custom package uses port 8083, and Synocommunity's Medusa package uses port 8899. So if you restore your backup between the two the port will also be restored back. Therefore make sure you open the Medusa page with the correct port.


## Explained with illustrations.  

Login to Medusa and go to Backup and Restore in the configuration. Create a backup and store it in a safe location.  

![1](https://cloud.githubusercontent.com/assets/7928052/11318354/73fa0d0e-904f-11e5-9432-581a8e795508.png)  
=


Login to Synology's DSM and go into the Package Center and open the Medusa Package. There Select Remove.  

![2](https://cloud.githubusercontent.com/assets/7928052/11318355/73faad5e-904f-11e5-8a00-36a0ca446070.png)
=


On the confirmation window press `YES`.  

![3](https://cloud.githubusercontent.com/assets/7928052/11318353/73f94810-904f-11e5-845b-71c7bc851f7c.png)
=

###### Install Medusa  

Now that Medusa is removed we need to (re)install it. Go to the community overview of Packages, find Sickbeard-custom and click on `Install`.  

![1](https://cloud.githubusercontent.com/assets/7928052/12465056/88f5befe-bfcc-11e5-9c59-f44ad547c768.png)
=


Now you will get a wizard/installation screen. Fill-in the new URL :  
`Fork URL:`    `git://github.com/pymedusa/Medusa.git`  
`Fork branch:` `master` 

![2](https://cloud.githubusercontent.com/assets/7928052/12465370/f6963596-bfcd-11e5-814f-5c168c512b79.png)
=


Medusa is now (re)installed.  
Open the GUI and go to Backup/Restore under configuration and restore your backup.  

![7](https://cloud.githubusercontent.com/assets/7928052/11318357/741a8c14-904f-11e5-94e8-614dc94ede74.png)  
=


Last thing you need to do is a restart of Medusa so the changes take effect.   

![8](https://cloud.githubusercontent.com/assets/7928052/11318356/740d7dbc-904f-11e5-9e3a-4ebfea556b2e.png)  
=


That's all, you are now running on the new Repository. :)  

In some cases you can get a cache warning after restoring the backup. You can ignore those.  

``` 
MAIN :: Restore: Unable to remove the cache/sessions directory: error 2 : No such file or directory  
MAIN :: Restore: Unable to remove the cache/indexers directory: error 2 : No such file or directory  
```