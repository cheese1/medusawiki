# Nginx

Make sure to replace `example.com` with your domain name and localhost with the ip of your Medusa server.
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

    location / {
        proxy_pass http://localhost:8081;
        proxy_set_header Host $host;
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

# Apache
In medusa config.ini make sure `handle_reverse_proxy = 1`.
Your not forced to configure https in medusa, but if you want to, change: `enable_https = 1`.
If you do, then also make sure you change `http://localhost:8081/medusa` with `https://localhost:8081/medusa` and `ws://127.0.0.1:8081/medusa/ws` with `wss://127.0.0.1:8081/medusa/ws`.
```
<VirtualHost *:443>
    LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
    LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
    LoadModule proxy_wstunnel_module /usr/lib/apache2/modules/mod_proxy_wstunnel.so
    LoadModule ssl_module modules/mod_ssl.so
    SSLProxyEngine on
    SSLProxyVerify none
    SSLProxyCheckPeerCN off
    SSLProxyCheckPeerName off
    SSLProxyCheckPeerExpire off
    ProxyRequests Off

    # make sure we keep communicating over https
    RequestHeader set X-Forwarded-Proto "https" env=HTTPS

    ProxyRequests On
    ProxyPreserveHost Off
    ServerName your_server_name

    SSLEngine on
    SSLCertificateFile /etc/apache2/certs/your_cert.crt
    SSLCertificateKeyFile /etc/apache2/certs/your_cert.key

    # Medusa proxy config
    ProxyPass /medusa/ws ws://127.0.0.1:8081/medusa/ws keepalive=On timeout=600 retry=1 acquire=3000

    # websockets
    ProxyPassReverse /medusa/ws ws://127.0.0.1:8081/medusa/ws
    ProxyPassReverseCookieDomain 127.0.0.1 %{HTTP:Host}

***
    # if you receive an error 400 (seen using at least Server version: Apache/2.4.33), use this rather than the ProxyPass and ProxyPassReverse statements above for the ws: urls

    RewriteEngine On

    # When Upgrade:websocket header is present, redirect to ws
    # Using NC flag (case-insensitive) as some browsers will pass Websocket
    RewriteCond %{HTTP:Upgrade} =websocket [NC]
    RewriteRule ^/ws/(.*)    ws://127.0.0.1:5051/ws/$1 [P,L]
***

    # webserver
    ProxyPass /medusa http://localhost:8081/medusa keepalive=On timeout=600 retry=1 acquire=3000
    ProxyPassReverse /medusa http://localhost:8081/medusa

	# just some logging
    CustomLog /var/log/apache2/proxy-access.log combined
    ErrorLog /var/log/apache2/proxy-error.log
</VirtualHost>
```

# Microsoft IIS Application Request Routing
This explanation assumes that ARR in IIS fully configured and working.

Make sure that WebSocket Protocol is added as a feature to IIS.
![](https://i.imgur.com/h62mXUS.png)

Create the following Server Variables in IIS:
1. HTTP_X_FORWARDED_HOST
2. HTTP_X_FORWARDED_PROTO
3. HTTP_X_FORWARDED_SCHEMA

Edit the web.config of the the Medusa site to contain the following lines and change localhost with the ip of your Medusa server
```
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="Medusa Reverse Proxy" enabled="true" patternSyntax="Wildcard" stopProcessing="true">
                    <match url="*" />
                    <action type="Rewrite" url="http://LOCALHOST:8081/{R:1}" />
                    <serverVariables>
                        <set name="HTTP_X_FORWARDED_HOST" value="{HTTP_HOST}" />
                        <set name="HTTP_X_FORWARDED_SCHEMA" value="https" />
                        <set name="HTTP_X_FORWARDED_PROTO" value="https" />
                    </serverVariables>
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```