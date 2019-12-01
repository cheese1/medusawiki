## Ubuntu 14.04+ | Debian 7.0+
The following instructions are for installing Medusa on Ubuntu 14.04 and newer or Debian 7.0 and newer.

The installation assumes that you're not using the root user to install/run Medusa. The entries for **user:group** throughout the document will be set as **medusa:medusa** and you will have to modify it if you want it to match your user configuration.

1. Update repositories and install dependencies.
    This will give you unrar-free and git to pull the repo
 
   ```
   sudo apt-get update && sudo apt-get install unrar-free git-core openssl mediainfo
   ```
   **Install Python 3:**

   Ubuntu: Follow this well written guide over at [Real Python](https://realpython.com/installing-python/#ubuntu).

   Debian 7.0 - 8.0: Follow this well written guide over at [Real Python](https://realpython.com/installing-python/#debian).

   Debian 9 and newer: `sudo apt-get install python3`


   **Still using Python 2.7?** Switch now! [Follow these instructions](https://github.com/pymedusa/Medusa/wiki/Switch-to-Python-3).

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

**For SysVinit Systems**
	
4. Copy init.d service

    Ubuntu:
    ```
    sudo cp -v /opt/medusa/runscripts/init.ubuntu /etc/init.d/medusa
    ```
    Debian:
    ```
    sudo cp -v /opt/medusa/runscripts/init.debian /etc/init.d/medusa
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