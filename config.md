## Required 

Install Ubuntu 16.04 LTS on your virtuel machine and make sure that you can ping it from your local
to verify  :

* Get your Virtuel machine IP :

```
sudo apt-get ifconfig
```

* Ping this IP adresse from your local machine :

```
sudo apt-get ping YOUR_IP
```

# LEMP ENV for DEV ubuntu 16.04

Nginx - Php 7 - Mysql - Test with wordpress

## Update packages: 

```
sudo apt-get update
```


## Install Nginx

```
sudo apt-get install nginx
```

### Allow firewall

```
sudo ufw allow 'Nginx HTTP'
```
### Check status , it should be activated .

```
sudo ufw status
```
### Else 

```
sudo ufw enable
```
## Install Mysql

```
sudo apt-get install mysql-server
```
## Configuration php.ini

You to open php.ini : sudo vi /etc/php/7.0/fpm/php.ini  and sereach that contain : cgi.fix_pathinfo=0

uncomment the ligne and change it to cgi.fix_pathinfo=1

### then restart : 

```
sudo systemctl restart php7.0-fpm
```
## Check the server Configuration :


```
sudo vi /etc/nginx/sites-available/default
```
## File Exemple :

```
server {
    listen 80 default_server;
    listen [::]:80 default_server;

    root /var/www/html;
    index index.php index.html index.htm index.nginx-debian.html;

    server_name server_domain_or_IP;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.0-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }
}

```
## Test the configuration : 

```
sudo nginx -t
```
## Reload Nginx 

```
sudo systemctl reload nginx
```

### Check with a php file in /var/www/html : 

```
<?php 

phpinfo();

```
### Phpmyadmin 

```
sudo apt-get install phpmyadmin
```
```
sudo ln -s /usr/share/phpmyadmin/ /var/www/html/
```
```
sudo systemctl restart nginx
```
```
sudo systemctl restart php7.0-fpm
```

## Test with Wordpress 

```
cd /var/www/html
```
Git Clone 

```
git clone https://github.com/WordPress/WordPress.git
```

Browse http://Ip_adresse/WordPress

## ScreenShot

![Alt text](/img/screen.png?raw=true "screen")