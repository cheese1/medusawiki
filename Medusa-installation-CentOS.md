

## CentOS 6-7
The following instructions are for installing Medusa on CentOS.
They should also be applicable to RHEL and Fedora with minimal changes.

The installation assumes that you're not using the root user to install/run Medusa. The entries for **user:group** throughout the document will be set as **medusa:media** and you will have to modify it if you want it to match your user configuration.

1. Install [IUS Community Project](https://ius.io/) repository.
    The repository is needed for recent Python versions.
   
   For **CentOS 6**:
   ```
   sudo yum install https://centos6.iuscommunity.org/ius-release.rpm
   ```
   For **Centos 7**:
   ```
   sudo yum install https://centos7.iuscommunity.org/ius-release.rpm
   ```

2. Install prerequisites

   ```
    sudo yum install python36u wget git
    ```
   Install unrar:

   64bit
   ```
   wget https://www.rarlab.com/rar/rarlinux-x64-5.7.0.tar.gz
   tar -zxvf rarlinux-x64-5.7.0.tar.gz
   sudo cp -v rar/rar rar/unrar /usr/local/bin/
   ```
   32bit
   ```
   wget https://www.rarlab.com/rar/rarlinux-5.7.0.tar.gz
   tar -zxvf rarlinux-5.7.0.tar.gz
   sudo cp -v rar/rar rar/unrar /usr/local/bin/
   ```

3. Add new group and user
   ```
   sudo groupadd media
   sudo useradd -g media medusa
   ```

4. Clone medusa git repo

    ```bash
    sudo git clone https://github.com/pymedusa/Medusa.git /usr/share/medusa
    ```

5. Set correct ownership

    ```bash
    chown -R medusa:media /usr/share/medusa
    ```

**For systemd (CentOS 7)**

5. Copy systemd service
   ```
   sudo cp -v /usr/share/medusa/runscripts/init.systemd /etc/systemd/system/medusa.service
   ```
   Make sure your new service has correct permissions
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

**For Init Systems**

5. Copy init file to system init

    ```bash
    sudo cp /usr/share/medusa/runscripts/init.fedora /etc/init.d/medusa
    ```

6. Make init file executable

    ```bash
    sudo chmod +x /etc/init.d/medusa
    ```

7. Modify init file

    ```bash
    sudo sed 's|/etc/sysconfig/sickbeard|/etc/sysconfig/medusa|' -i /etc/init.d/medusa
    ```

8. Create configuration file /etc/sysconfig/medusa with the following content

    ```bash
    # Medusa service configuration
    
    #run Medusa as
    SR_USER=media
    SR_HOME=/usr/share/medusa
    SR_DATA=/usr/share/medusa
    SR_PIDFILE=/usr/share/medusa/medusa.pid
    
    #gui address, eg: \${protocol}://\${host}:\${port}/home/
    protocol=http
    host='<<< hostname or IP >>>' #example host=mymachine
    port='<<<Desired Port>>>'     #example port=8081
    
    #leave blank if no username/password is required to access the gui
    username=
    password=
    
    #use nice, ionice, taskset to start Medusa
    nicecmd=
    #  example: nicecmd="nice -n 19 ionice -c3"
    ```

9. Add the medusa service to system services
    
    ```bash
    sudo chkconfig --add medusa
    ```

10. Configure medusa service to start on system startup
    
    ```bash
    sudo chkconfig medusa on
    ```

11. Start medusa service
    
    ```bash
    sudo service medusa start
    ```

All done, verify that Medusa is accessible at gui address, eg: http://your_ip:8081