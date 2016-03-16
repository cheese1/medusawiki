## Ubuntu 14.x 15.x 16.x
The following instructions are for installing Medusa on Ubuntu 14.x 15.x 16.x
 
The installation is applicable to the upcoming 16.04 LTS as it is the same systemd setup as 15.x. The provided script can distinguish the difference between systemd/init/upstart for you. 
 
The installation assumes that you're not using the root user to install/run sickrage - the entries for **user:group** throughout the document will be set as sickrage:sickrage and you will have to modify if if you want it to match your user configuration.
 
If you trust us and would like us to just do it for you just paste this:

	curl https://raw.githubusercontent.com/SickRage/sickrage-issues/master/INSTALLSCRIPTS/debian-ubuntu-init.sh | sudo bash
	
Otherwise:
 
1. Update repositories and install Medusa dependencies
    This will give you unrar-free (guess), and git to pull the repo
 
   ```bash
   sudo apt-get update && sudo apt-get install unrar-free git-core openssl libssl-dev python2.7
   ```
 
2. Create sickrage user and group
    This makes sure that sickrage is isolated and is best practice for security
   
    ```bash
    sudo addgroup --system sickrage
    sudo adduser --disabled-password --system --home /var/lib/sickrage --gecos "SickRage" --ingroup sickrage sickrage
    ```
   
3. Clone Medusa git repo
 
    ```bash
    sudo mkdir /opt/sickrage && sudo chown sickrage:sickrage /opt/sickrage
    sudo -u sickrage git clone https://github.com/pyMedusa/SickRage.git /opt/sickrage
    ```

For Init Systems
	
4. Copy init.d service
 
    ```bash
    sudo cp -v /opt/sickrage/runscripts/init.ubuntu /etc/init.d/sickrage
    ```
 
5. Make sure your new service has correct permissions
 
    ```bash
    sudo chown root:root /etc/init.d/sickrage
    sudo chmod 644 /etc/init.d/sickrage
    ```
 
6. Update and start your new service
   
    ```bash
    sudo update-rc.d sickrage defaults
	sudo service sickrage start
    ```
	
For Upstart Systems

4. Copy init.d service
 
    ```bash
    sudo cp -v /opt/sickrage/runscripts/init.upstart /etc/init/sickrage.conf
    ```

5. Make sure your new service has correct permissions
 
    ```bash
    sudo chown root:root /etc/init/sickrage.conf
    sudo chmod 644 /etc/init/sickrage.conf
    ```

6. Update and start your new service
   
    ```bash
    sudo service sickrage start
    ```

For Systemd Systems

4. Copy systemd service
 
    ```bash
    sudo cp -v /opt/sickrage/runscripts/init.systemd /etc/systemd/system/sickrage.service
    ```
 
5. Make sure your new service has correct permissions
 
    ```bash
    sudo chown root:root /etc/systemd/system/sickrage.service
    sudo chmod 644 /etc/systemd/system/sickrage.service
    ```
 
6. Enable, start, and then check the status of your new service
   
    ```bash
    sudo systemctl enable sickrage
    sudo systemctl start sickrage
    sudo systemctl status sickrage

All done, verify that Medusa is accessible at: http://localhost:8081
