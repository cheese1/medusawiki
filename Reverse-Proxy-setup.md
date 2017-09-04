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
In medusa config.ini make sure `enable_https = 1` and `handle_reverse_proxy = 1`. 
```
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
<Proxy *>
        AddDefaultCharset Off
        Order deny,allow
        Allow from all
</Proxy>
ProxyPass /medusa/ws wss://127.0.0.1:8081/medusa/ws keepalive=On timeout=600 retry=1 acquire=3000
ProxyPassReverse /medusa/ws wss://127.0.0.1:8081/medusa/ws
ProxyPass /medusa https://127.0.0.1:8081/medusa keepalive=On timeout=600 retry=1 acquire=3000
ProxyPassReverse /medusa https://127.0.0.1:8081/medusa
ProxyPassReverseCookieDomain 127.0.0.1 %{HTTP:Host}
```