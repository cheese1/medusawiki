## Ubuntu 15.*
The following instructions are for installing Medusa on Ubuntu 15.*.
 
The installation should also be applicable to the upcoming 16.04 LTS as it is just a systemd setup.
 
The installation assumes that you're not using the root user to install/run medusa - the entries for **user:group** throughout the document will be set as medusa:medusa and you will have to modify if if you want it to match your user configuration.
 
If you trust us and would like us to just do it for you just paste this:
 
    curl https://raw.githubusercontent.com/Medusa/medusa-issues/master/INSTALLSCRIPTS/ubuntusystemd.sh | sudo bash

Otherwise:
 
1. Update repositories and install Medusa dependencies
    This will give you unrar-free (guess), and git to pull the repo
 
   ```bash
   sudo apt-get update && sudo apt-get install unrar-free git-core openssl libssl-dev python2.7
   ```
 
2. Create medusa user and group
    This makes sure that medusa is isolated and is best practice for security
   
    ```bash
    sudo addgroup --system medusa
    sudo adduser --disabled-password --system --home /var/lib/medusa --gecos "Medusa" --ingroup medusa medusa
    ```
   
3. Clone Medusa git repo
 
    ```bash
    sudo mkdir /opt/medusa && sudo chown medusa:medusa /opt/medusa
    sudo -u medusa git clone https://github.com/Medusa/Medusa.git /opt/medusa
    ```
 
 
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
 
All done, verify that Medusa is accessible at: http://localhost:8081
