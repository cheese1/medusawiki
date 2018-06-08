### Install Docker for armhf

**pull docker image:**

`docker pull lsioarmhf/medusa`

**create container:**

```
Usage
docker create \
  --name=medusa \
-v /srv/medusa/config:/config \
-v /srv/medusa/downloads:/downloads \
-v /srv/medusa/tv-shows:/tv \
-e PGID=<gid> -e PUID=<uid>  \
-e TZ=<timezone> \
-p 8081:8081 \
  lsioarmhf/medusa
```

further detail about docker: https://hub.docker.com/r/lsioarmhf/medusa/<BR>
or https://docs.docker.com/get-started/

### Config Nginx

**modify "web_root = "medusa""** in **/srv/medusa/config/config.ini**

```
[General]
...
...
...
web_root = "medusa"
```

**Nginx location**<BR> 
such as in Open Media Vault: `/etc/nginx/sites-available/openmediavault-webgui`
```
server {
       listen         80;
       server_name    example.com;
       return         301 https://$server_name$request_uri;
}
server {
    listen 443;
    server_name example.com;

    ssl on;
    ssl_certificate /usr/local/nginx/conf/server.crt;
    ssl_certificate_key /usr/local/nginx/conf/server.key;
    ssl_session_cache shared:SSL:10m;
    
    location ^~ /medusa {
            proxy_pass http://localhost:8081;

            proxy_set_header Host $host;
            #proxy_set_header X-Forwarded-Proto https;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Host $host:443;
            proxy_set_header X-Forwarded-Server $host;
            proxy_set_header X-Forwarded-Port 443;
            proxy_set_header X-Forwarded-Proto $scheme;

            # Websocket
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection "upgrade";
            proxy_read_timeout 86400;
    }
}
```

**Access Medusa on Web-browser**
```
https://example.com/medusa/
...redirect to https://example.com/medusa/home/
```

References:
https://hub.docker.com/r/lsioarmhf/medusa/

https://github.com/pymedusa/Medusa/issues/3041

https://github.com/pymedusa/Medusa/wiki/Reverse-Proxy-setup
