Gunicorn is a Python WSGI HTTP Server for Linux. It is best to use Gunicorn behindf an HTTP proxy server like [[Nginx]].

#DevOps #Gunicorn 

# Sample Python Application
```python
def app(environ, start_response):
        data = b"Hello, World!\n"
        start_response("200 OK", [
            ("Content-Type", "text/plain"),
            ("Content-Length", str(len(data)))
        ])
        return iter([data])
```
myapp.py

cmd to run application: `gunicorn -w 4 myapp:app`

# Installation
```bash
pip install gunicorn
```

# Deployment
```nginx
  server {
    listen 80;
    server_name example.org;
    access_log  /var/log/nginx/example.log;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
  }
```
In this sample configuration, Nginx is setup as reverse proxy to a Gunicorn server running on localhost port 8000.