## Required 

Install Ubuntu 16.04 LTS on your Vm using vagrant:



* Create the vagrant file:

```
vagrant init hashicorp/precise64
```

* Uncomment the ligne that contain "config.vm.network" and insert your Ip adresse in the Browser's adresse bar:

```
vagrant up
```
* Access

```
vagrant ssh
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
### Check status, it should be activated

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

You have to open php.ini : sudo vi /etc/php/7.0/fpm/php.ini  and search for the ligne that contains: "cgi.fix_pathinfo=0"

uncomment the ligne and change it to "cgi.fix_pathinfo=1"

### then restart: 

```
sudo systemctl restart php7.0-fpm
```
## Check the server's configuration:


```
sudo vi /etc/nginx/sites-available/default
```
## File Example :

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
## Test the configuration: 

```
sudo nginx -t
```
## Reload Nginx 

```
sudo systemctl reload nginx
```

### Check with a php file in /var/www/html: 

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
