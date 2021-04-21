# nginx-fancyindex

## Related Links

NGINX module: [aperezdc/ngx-fancyindex](https://github.com/aperezdc/ngx-fancyindex)

Original Theme: [aleha/nginx-fancyindex-flat-theme](https://github.com/alehaa/nginx-fancyindex-flat-theme)

Demo: [https://files.webiptek.com](https://files.webiptek.com)

## How to Use

1. Download all resources in this repository and put them on spesific folder. For example, I placed them on /var/www/files.webiptek.com/.fancyindex.
```
$ ls /var/www/files.webiptek.com/.fancyindex
footer.html  header.html  js  less  theme.d  theme.less  logo.png
```

2. Example /etc/nginx/sites-available/{yoursite} configuration.
```
server {
        root /var/www/files.webiptek.com;
        server_name files.webiptek.com;
        location / {
                # To customize your fancyindex, please refer to aperezdc/ngx-fancyindex (see related links).
                fancyindex on;
                fancyindex_localtime on;
                fancyindex_name_length 255;
                fancyindex_show_path   off;
                fancyindex_exact_size  off;
                fancyindex_header "/theme/header.html";
                fancyindex_footer "/theme/footer.html";
                fancyindex_ignore ".fancyindex" "favicon.ico";
                fancyindex_time_format "%d-%b-%Y %H:%M";
                try_files $uri $uri/ =404;
        }
        location /theme {
                # cutomize your theme location below
                alias /var/www/files.webiptek.com/.fancyindex;
        }
}
```
## LICENSE

This software is distributed for free, in the hope that it will be useful, but **WITHOUT ANY WARRANTY**. Without even the implied warranty of **MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE**.
