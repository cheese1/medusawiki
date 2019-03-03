

## CentOS 6
The following instructions are for installing Medusa on CentOS 6.

The installation should also be applicable to RHEL 6 and Fedora (12, 13, or 14) with minimal changes.

The installation assumes that you're not using the root user to install/run medusa - the entries for **user:group** throughout the document will have to be modified to match your user configuration.

1. Install rpmFusion non-free repository 
    The repository is needed for unrar installation

   ```bash
   sudo rpm -ivh http://download1.rpmfusion.org/nonfree/el/updates/6/i386/rpmfusion-nonfree-release-6-1.noarch.rpm
   ```

2. Install prerequisites

   ```bash
    sudo yum install python-cheetah unrar wget git 
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

All done, verify that Medusa is accessible at gui address, eg: http://mymachine:8080/medusa

Celebrate with some impromptu dancing!!