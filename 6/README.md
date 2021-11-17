# Question 6

> Install LEMP stack (avoid installing mysql) and open info.php on
port 80 and print message  info.php

LEMP stands for Linux, Nginx, MySQL, Php stack. First to process php, nginx need php-fpm which can be installed as

```
~ sudo apt install php-fpm
```

![Install php](screenshots/Screenshot%202021-11-18%20005916.png) 

So now the configuration file needs to be changed as follows:

```
server {
        listen 80;
        root /var/www/localhost;
        index index.php index.html index.htm;
        server_name localhost;

        location / {
                try_files $uri $uri/ =404;
        }

        location ~ \.php$ {
                include snippets/fastcgi-php.conf;
                fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
        }

        location ~ /\.ht {
                deny all;
        }
}
```
![Config](screenshots/Screenshot%202021-11-18%20012019.png)

Create symlink of **/etc/nginx/sites-available/lemp.conf** with **/etc/nginx/sites-enabled/** using the command:

```
~ ln -s /etc/nginx/sites-available/lemp.conf /etc/nginx/sites-enabled/
```

And to test the configuration file is correct use the command:

```
~ nginx -t
```

Now to restart the nginx server after configuration changes,

```
~ sudo systemctl reload nginx
```

Now to edit info.php as:

![info.php](screenshots/Screenshot%202021-11-18%20011852.png)

![output](screenshots/Screenshot%202021-11-18%20011939.png)
