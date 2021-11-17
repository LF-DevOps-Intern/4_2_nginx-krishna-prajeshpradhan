# Question 4

> Create a **test2.conf** and listen on port 82 and to “ location /test/” with message “ test is successful”.

Create a **test2.conf** configuration file and add the following:

```
server {
       listen 82;
       listen [::]:82;

       server_name localhost;

       root /var/www/localhost;
       index index.html;

       location /test/ {
        index test.html;
       }
}
```

![config](screenshots/Screenshot%202021-11-18%20004237.png)
 

Create symlink of **/etc/nginx/sites-available/test2.conf** with **/etc/nginx/sites-enabled/** using the command:

```
~ ln -s /etc/nginx/sites-available/test2.conf /etc/nginx/sites-enabled/
```

And to test the configuration file is correct use the command:

```
~ nginx -t
```

Now to restart the nginx server after configuration changes,

```
~ sudo systemctl reload nginx
```


The html file is now inside **/var/www/localhost/test/test.html**,

![html](screenshots/Screenshot%202021-11-18%20004147.png)

![output](screenshots/Screenshot%202021-11-18%20004300.png)
 


 
 
