## Configure download URL
**Introduction**

Available in General -> Interface, the field download url allows you to specify where the episodes can be downloaded. If configured, a column is added in the episode list with a "Download" link. It's simply generated using the URL configured in the download URL field + the name of the show + the name of the episode.
For example, if the download url is set to http://shows.domain.tld/, for the show Firefly the url generated
for the first episode could be http://shows.domain.tld/Firefly/Season%2001/Firefly%20-%201x01%20-%20The%20Train%20Job.mp4
(probably different for you since it depends on your naming convention).

You do need a separate webserver with a vhost configured to make the shows available.

<span class="section">'''Apache'''</span>
Example configuration if you use apache, assuming your shows are stored in /home/user/shows :

  <VirtualHost "shows.domain.tld:80">
    DocumentRoot /home/user/shows
    ServerName shows.domain.tld
    CustomLog /var/log/apache2/shows_access.log combined
  
    <Directory "/home/user/shows">
       Order deny,allow
       Allow from all
    </Directory>
  </VirtualHost>


<span class="section">'''nginx'''</span>
Example configuration for nginx :
  server
  {
        listen                          80;
        server_name                     shows.domain.tld;
  
        access_log                      /var/log/nginx/shows.access_log;
        error_log                       /var/log/nginx/shows.error_log;
  
        root                            /home/user/shows;
        location /
        {
           autoindex                    on;
        }
  }

**TODO**
- Make subtitles available for download too
- Allow to setup a different download URL for each show root directory