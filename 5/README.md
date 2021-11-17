# Question 5

> Reverse proxy all http traffic of port 82 to port 85.

Creating reverse proxy with configuration file

```
server {
       listen 85;
       listen [::]:85;

       location / {
        proxy_pass http://localhost:82/test/;
       }
}
```

![config](screenshots/Screenshot%202021-11-18%20005543.png)

 

Create symlink of **/etc/nginx/sites-available/revere_proxy2.conf** with **/etc/nginx/sites-enabled/** using the command:

```
~ ln -s /etc/nginx/sites-available/revere_proxy2.conf /etc/nginx/sites-enabled/
```

And to test the configuration file is correct use the command:

```
~ nginx -t
```

Now to restart the nginx server after configuration changes,

```
~ sudo systemctl reload nginx
```

Now all traffic is proxy to 82

![output](screenshots/Screenshot%202021-11-18%20005604.png)

 
