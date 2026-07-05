# Web Server Setup
The server will be set up in the following structure:
```
/opt/web-server-lab/
├── docker-compose.yml
├── nginx/
│   └── default.conf
└── logs/
    ├── access.log
    └── error.log
```

Here, the nginx and logs directories are used for mapping files from the Nginx container.

## Setup
> "Run every command as Root user."

### Directory structure build
```
mkdir /opt/web-server-lab
mkdir /opt/web-server-lab/nginx
mkdir /opt/web-server-lab/logs
```
### Create Compose and Conf file
#### docker-compose.yml
```
nano /opt/web-server-lab/docker-compose.yml
```
Add the following content to the docker-compose.yml file.
```
services:
  juice-shop:
    image: bkimminich/juice-shop:latest
    container_name: juice-shop
    restart: unless-stopped
    expose:
      - "3000"
    networks:
      - web-lab

  nginx:
    image: nginx:latest
    container_name: nginx-proxy
    restart: unless-stopped
    depends_on:
      - juice-shop

    ports:
      - "80:80"

    volumes:
      - ./nginx/default.conf:/etc/nginx/conf.d/default.conf:ro
      - ./logs:/var/log/nginx

    networks:
      - web-lab

networks:
  web-lab:
    driver: bridge
```

#### default.conf
```
nano /opt/web-server-lab/nginx/default.conf
```
Paste the following data into the default.conf file.
```
server {

    listen 80;

    server_name _;

    access_log /var/log/nginx/access.log;
    error_log  /var/log/nginx/error.log;

    location / {

        proxy_pass http://juice-shop:3000;

        proxy_http_version 1.1;

        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

    }

}
```

### Run the containers
```
cd /opt/web-server-lab
sudo docker compose up -d
```
