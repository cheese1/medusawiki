

## CentOS 6
The following instructions are for installing Medusa on CentOS.

The installation should also be applicable to RHEL 6 and Fedora (12, 13, or 14) with minimal changes.

The installation assumes that you're not using the root user to install/run medusa - the entries for **user:group** throughout the document will have to be modified to match your user configuration.

1. Install IUS Community Project repository
    The repository is needed for recent Python versions
   
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

3. Clone medusa git repo

    ```bash
    sudo git clone https://github.com/pymedusa/Medusa.git /usr/share/medusa
    ```

4. Set correct ownership

    ```bash
    chown -R user:group /usr/share/medusa
    ```

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

All done, verify that Medusa is accessible at gui address, eg: http://mymachine:8081/medusa