# Nginx

* 部署浏览共享目录功能

```text
vim /etc/nginx/nginx.conf

http {
    # other things ...

    server {
        listen 80;
        server_name localhost;
        index index.html index.htm index.php

        location / {
            root /opt/data/; #自定义根目录
            autoindex on;
            autoindex_localtime on;
        }
    }

}

```

* 中文文档 http://www.nginx.cn/doc/index.html


