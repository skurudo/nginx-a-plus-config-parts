# Get A+ rating with nginx

A little help with SSLLabs A+ rating.

For nginx.conf: 
```
    ssl_session_cache   shared:SSL:50m;
    ssl_buffer_size 1400;
    ssl_session_timeout 24h;
    ssl_protocols       TLSv1.2;
    ssl_prefer_server_ciphers on;
    ssl_stapling on;
    ssl_stapling_verify on;
    resolver 8.8.8.8 8.8.4.4;
    resolver_timeout 10s;
    ssl_trusted_certificate /etc/nginx/cert/trustchain.crt; #need to create first
    ssl_dhparam /etc/nginx/cert/dhparam.pem; #need to create first
    ssl_ecdh_curve              secp384r1;
ssl_ciphers                 ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-SHA384:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES256-SHA256:ECDHE-RSA-AES256-SHA:DHE-RSA-AES256-SHA:DHE-RSA-CAMELLIA256-SHA:ECDHE-RSA-AES256-SHA:DHE-RSA-AES256-SHA:DHE-RSA-AES256-SHA:DHE-RSA-CAMELLIA256-SHA:ECDH-RSA-AES256-SHA:CAMELLIA256-SHA:AES256-SHA;
    #ssl_ciphers AES256+EECDH:AES256+EDH:!aNULL; # good too
```   
 
For nginx-v-host:
```
    ssl         on;
    ssl_certificate      /home/admin/conf/web/ssl.123.ru.pem;
    ssl_certificate_key  /home/admin/conf/web/ssl.123.ru.key;
    spdy_keepalive_timeout 300;
    spdy_headers_comp 9;
    add_header Strict-Transport-Security 'max-age=31536000; includeSubDomains; preload';
    add_header X-Frame-Options SAMEORIGIN;
    add_header X-Content-Type-Options nosniff;
```