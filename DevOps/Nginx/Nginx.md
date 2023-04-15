#DevOps #nginx
# Installation
```bash
sudo apt install nginx
```

# Configuration
Configuration files are located at `/etc/nginx/conf.d/`.

## Sample Configuration
For serving a sample application, create a configuration file for the application. For example: 
`my-angular-app.conf`

```nginx
events {
    worker_connections 4096;
}

http {
    server {
        listen 80;
        server_name localhost;
        root /var/www/angular-pmac;
        index index.html;
        
        location  /api {
            rewrite /api(.*) /$1  break;
            proxy_pass         http://localhost:8000;
            proxy_redirect     off;
            proxy_set_header   Host $host;
        }
    }
}
```

**server_name**: specifies the domain name for your angular application.
**root**: specifies the path to the `dist` directory of your Angular application.
**location**: block tells Nginx to try serving the requested URL as-is and if that fails try serving the URL with a trailing slash or serve the `index.html` file.

# Launch
```bash
nginx -t #checks if configuration is ok
systemctl start nginx
```
