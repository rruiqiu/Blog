# Linux

## [Systemd](https://systemd.io/)(system demon)

Systemd is a service management tool in linux that can be used to create a new service.

### Create Http Flask service

After configure the reverse proxy successful in nginx, we can deploy the python flask application by using gunicorn(https://gunicorn.org/#quickstart) to deploy. Gunicorn 'Green Unicorn' is a Python WSGI HTTP Server for UNIX. 

[Why should I use gunicorn to deploy instead of using python?](###Why should I use gunicorn to deploy instead of using python?)

Create a [name].service file under `/etc/systemd/system/`

Example service file for my gunicron application

```
[Unit]
Description=Gunicorn instance to serve flask_testing
After=network.target

[Service]
User=ubuntu
Group=ubuntu
WorkingDirectory=/home/ubuntu/flask_testing
Environment="PATH=/home/ubuntu/flask_testing/flasktestvenv/bin"
ExecStart=/home/ubuntu/flask_testing/flasktestvenv/bin/gunicorn --workers 2 --bind 0.0.0.0:5000 app:app

[Install]
WantedBy=multi-user.target

```



Useful cmd:

```c
sudo systemctl daemon-reload	//Reload the systemd manager configuration to make it aware of the new service file:
sudo systemctl enable gunicorn	//Enable the service to start on boot:
sudo systemctl start gunicorn	//Start the service:
sudo systemctl status gunicorn	//Verify that the service is running without errors:

sudo systemctl restart gunicorn
sudo systemctl stop gunicorn
journalctl -u gunicorn
```

[Resources](https://dev.to/tkirwa/create-a-systemd-service-script-for-running-gunicorn-to-serve-your-application-5aea)









## HTTPS & SSL

How to auto generate the SSL certificate and set up the ssl in Nginx to make the website use https

I find it really easy to configure the SSL by using the certbot by following the below link. I am using AWS EC2 ubuntu instance.

https://certbot.eff.org/instructions?ws=nginx&os=ubuntufocal

The only change I need to make is 

## NGINX CMD

`sudo nginx -t` Check the nginx syntax verfication

`sudo systemctl reload nginx` 

`sudo systemctl restart nginx` 



























## Reference

### Why should I use gunicorn to deploy instead of using python?
1. **Production-Ready**: The Flask built-in server is intended for development purposes only. It is not optimized for production use and does not provide the necessary features for handling production traffic efficiently and securely. Gunicorn, on the other hand, is designed for production use and can handle multiple requests concurrently.
2. **Concurrency**: Gunicorn can manage multiple worker processes. This allows it to handle many requests at the same time, improving the responsiveness and performance of your application. The built-in Flask server is single-threaded and can only handle one request at a time, making it unsuitable for high-traffic applications.
3. **Load Balancing**: Gunicorn can spawn multiple worker processes, which can be distributed across multiple CPU cores. This makes better use of the server's resources and improves performance. The built-in Flask server does not support multiple workers or load balancing.
4. **Graceful Handling of Connections**: Gunicorn provides graceful handling of connections and worker processes, ensuring that requests are completed even if a worker process is restarted or shut down. This helps maintain uptime and provides a better experience for users.
5. **Security**: Gunicorn is more secure for production use as it is designed to handle various security concerns such as handling untrusted client data. The built-in Flask server lacks these production-level security features.
6. **Compatibility with WSGI Servers**: Gunicorn is a WSGI (Web Server Gateway Interface) HTTP server for Python web applications. It allows your Flask application to be served by any WSGI-compatible web server, providing flexibility and scalability. The built-in Flask server does not support WSGI, limiting its compatibility with other web servers.
7. **Integration with Reverse Proxies**: Gunicorn works well with reverse proxies like Nginx. Nginx can handle static files, SSL termination, and can act as a load balancer, forwarding requests to Gunicorn. This setup enhances performance and security while providing more robust server management.
8. **Reliability and Robustness**: Gunicorn has been battle-tested in production environments and is known for its reliability and robustness. It handles edge cases and failures gracefully, ensuring your application remains available.

In summary, while the built-in Flask server is great for development and testing, Gunicorn provides the necessary features, performance, and security required for deploying a Flask application in a production environment.
