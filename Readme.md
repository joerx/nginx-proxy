# Nginx Proxy

Generic Nginx image to be used as reverse proxy. Backend address can be configured using env vars.

## Usage

Command line:

```bash
docker run -d --name nginx-proxy -e PROXYPASS_PORT=5000 -e PROXYPASS_HOST=172.17.0.10 nginx-proxy
```

Docker Compose:

```yaml
services:
  web:
    image: joerx/nginx-proxy
    ports:
      - 8000:80
    links:
      - backend
    environment:
      # points nginx to the backend host/port
      PROXYPASS_HOST: backend
      PROXYPASS_PORT: 3000

  backend:
    build: ./
    # etc.
```
