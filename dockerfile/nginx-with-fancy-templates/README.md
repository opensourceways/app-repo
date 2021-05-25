# Example
 Nginx configuration snippet:
 ```nginx
         location / {
            root   /repo/openeuler;
            fancyindex on;
            fancyindex_exact_size off;
            fancyindex_header /fancySource/header.html;
            fancyindex_footer /fancySource/footer.html;
            autoindex   on;
        }
        location /fancySource {
            root /etc/nginx/conf/static;
        }
 ```