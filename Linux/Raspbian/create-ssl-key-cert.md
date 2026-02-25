# Creating key and cert for nginx on Raspbian:

1. `sudo mkdir /etc/nginx/ssl`
2. `sudo openssl genrsa -out /etc/nginx/ssl/nginx.key 2048`
3. `sudo openssl req -x509 -nodes -days 1095 -key /etc/nginx/ssl/nginx.key -out /etc/nginx/ssl/nginx.crt`
