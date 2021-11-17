# Question 1

> Install nginx and host a simple index.html with message “hello nginx”

To Install nginx we will first need to run the Linux command: 

```
~ sudo apt update
~ sudo apt install nginx
``` 

![Nginx Install](screenshots/Screenshot%202021-11-17%20220825.png)
![Nginx Status](screenshots/Screenshot%202021-11-17%20220943.png)

Now to configure the nginx server, we create a configuration file at **/etc/nginx/sites-available/host.conf**:

```
server {
	listen 80;
	listen [::]:80;
	server_name localhost;
	root /var/www/localhost;
	index index.html;
	location / {
		try_files $uri $uri/ =404;
    }
}
```
 
![Configuration](screenshots/Screenshot%202021-11-17%20225139.png)

Create symlink of **/etc/nginx/sites-available/host.conf** with **/etc/nginx/sites-enabled/** using the command:

```
~ ln -s /etc/nginx/sites-available/host.conf /etc/nginx/sites-enabled/
```

And to test the configuration file is correct use the command:

```
~ nginx -t
```

Now to restart the nginx server after configuration changes,

```
~ sudo systemctl reload nginx
```

Now to create **index.html** at **/var/www/localhost/** as

```
<html>
        <head>
                <title>Hello World</title>
        </head>
        <body>
                <h1>Hello Nginx!</h1>
        </body>
</html>
```

![index.html](screenshots/Screenshot%202021-11-17%20235443.png)

So now the nginx server will response with **index.html** as such:

![output](screenshots/Screenshot%202021-11-17%20235331.png)
