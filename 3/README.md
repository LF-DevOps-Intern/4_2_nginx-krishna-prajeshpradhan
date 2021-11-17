# Question 3

> Nginx Reverse proxy all http requests to nodes js api.

Reverse Proxy from all http requests (port **80**) is directed towards node js app which is being served at port **6080**:
So the configuration file, **reverse_proxy.conf**, becomes:

```
server {
       listen 80;
       listen [::]:80;

       server_name localhost;

       location / {
                proxy_pass http://localhost:6080;
       }
}
```

![config](screenshots/Screenshot%202021-11-18%20001631.png)
 

Create symlink of **/etc/nginx/sites-available/reverse_proxy.conf** with **/etc/nginx/sites-enabled/** using the command:

```
~ ln -s /etc/nginx/sites-available/reverse_proxy.conf /etc/nginx/sites-enabled/
```

And to test the configuration file is correct use the command:

```
~ nginx -t
```

Now to restart the nginx server after configuration changes,

```
~ sudo systemctl reload nginx
```

So now the the port 80 proxy to port 6080 which is hosting node app

![output](screenshots/Screenshot%202021-11-18%20001729.png)