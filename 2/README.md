# Question 2

> What are nginx header security and its uses. And also implement in the test.conf file.

The security HTTP headers are the response HTTP headers, that server can add in order to harden the security of HTTP exchange.

There are a few, and as the web evolves, more are being added. Each security header serves its own purpose.
•	HTTP Strict Transport Security (HSTS)
•	Public Key Pinning Extension for HTTP (HPKP)
•	X-Frame-Options
•	X-XSS-Protection
•	X-Content-Type-Options
•	Content-Security-Policy
•	X-Permitted-Cross-Domain-Policies
•	Referrer-Policy
•	Expect-CT
•	Feature-Policy

HTTP security headers are added to responses, so that the browsers behave in a more secure way.

We can add security headers in nginx responses using add_header directive, example:

```
add_header X-XSS-Protection "1; mode=block";
```

Let us implement it on **test.conf** as given:

![config](screenshots/Screenshot%202021-11-18%20021247.png)
 

Create symlink of **/etc/nginx/sites-available/test.conf** with **/etc/nginx/sites-enabled/** using the command:

```
~ ln -s /etc/nginx/sites-available/test.conf /etc/nginx/sites-enabled/
```

And to test the configuration file is correct use the command:

```
~ nginx -t
```

Now to restart the nginx server after configuration changes,

```
~ sudo systemctl reload nginx
```

We can inspect the security headers in the browser’s debug panel.

![Network Browser](screenshots/Screenshot%202021-11-18%20021151.png)

 

 
