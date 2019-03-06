## Ubuntu 14.x - 18.x | Debian 7.0 - 9
The following instructions are for installing Medusa on Ubuntu 14.x - 18.x and Debian 7.0 - 9.

The installation assumes that you're not using the root user to install/run Medusa. The entries for **user:group** throughout the document will be set as **medusa:medusa** and you will have to modify it if you want it to match your user configuration.

1. Update repositories and install dependencies.
    This will give you unrar-free and git to pull the repo
 
   ```
   sudo apt-get update && sudo apt-get install unrar-free git-core openssl libssl-dev python2.7 ffmpeg mediainfo
   ```

2. Create medusa user and group medusa.
    This makes sure that Medusa is isolated and is best practice for security
   
    ```
    sudo addgroup --system medusa
    sudo adduser --disabled-password --system --home /var/lib/medusa --gecos "Medusa" --ingroup medusa medusa
    ```
   
3. Clone Medusa git repo
 
    ```
    sudo mkdir /opt/medusa && sudo chown medusa:medusa /opt/medusa
    sudo git clone https://github.com/pymedusa/Medusa.git /opt/medusa
    sudo chown -R medusa:medusa /opt/medusa
    ```

**For Init Systems**
	
4. Copy init.d service
 
    ```
    sudo cp -v /opt/medusa/runscripts/init.ubuntu /etc/init.d/medusa
    ```
 
5. Make sure your new service has correct permissions
 
    ```
    sudo chown root:root /etc/init.d/medusa
    sudo chmod 644 /etc/init.d/medusa
    ```
 
6. Update and start your new service
   
    ```
    sudo update-rc.d medusa defaults
    sudo service medusa start
    ```
	
**For Upstart Systems**

4. Copy init.d service
    ```bash
    sudo cp -v /opt/medusa/runscripts/init.upstart /etc/init/medusa.conf
    ```

5. Make sure your new service has correct permissions
    ```bash
    sudo chown root:root /etc/init/medusa.conf
    sudo chmod 644 /etc/init/medusa.conf
    ```

6. Update and start your new service
    ```bash
    sudo service medusa start
    ```

**For Systemd Systems**

4. Copy systemd service
    ```bash
    sudo cp -v /opt/medusa/runscripts/init.systemd /etc/systemd/system/medusa.service
    ```
 
5. Make sure your new service has correct permissions
    ```bash
    sudo chown root:root /etc/systemd/system/medusa.service
    sudo chmod 644 /etc/systemd/system/medusa.service
    ```
 
6. Enable, start, and then check the status of your new service
    ```bash
    sudo systemctl enable medusa
    sudo systemctl start medusa
    sudo systemctl status medusa
    ```

7. Add Medusa to startup (optional)
    ```
    sudo systemctl enable medusa.service
    ```

All done, verify that Medusa is accessible at: http://your_ip:8081