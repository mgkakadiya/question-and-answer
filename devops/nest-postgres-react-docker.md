# Instance Setup steps (Install below tools if not exist)
## install Docker
## install git
## install nvm
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
source ~/.bashrc
nvm list-remote
nvm install v14.10.0
nvm list
nvm use v14.10.0
nvm current
nvm uninstall node_version
```
## install nginx
ref: https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04
```
sudo apt update
sudo apt install nginx
# checking status
systemctl status nginx
# basic management commands.
sudo systemctl stop nginx
sudo systemctl start nginx
sudo systemctl restart nginx
sudo systemctl reload nginx
sudo systemctl disable nginx
sudo systemctl enable nginx
sudo nginx -t
```

### setting up domain
```
sudo nano /etc/nginx/sites-available/your_domain
```
sample /etc/nginx/sites-available/your_domain file
```
server {
    server_name your_domain www.your_domain;
    
    location / {
        root /opt/apps/<MY_APP>/prod/frontend;
        try_files $uri $uri/ /index.html;
        index  index.html index.htm;
    }
    
    location /api/v1 {
        proxy_pass http://localhost:5050;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "Upgrade";
        proxy_set_header Host $host;

        # Set the maximum allowed size of the client request body
        client_max_body_size 310M; # 300 megabytes
    }

    location /swagger-ui {
        proxy_pass http://localhost:5050;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "Upgrade";
        proxy_set_header Host $host;

        # Set the maximum allowed size of the client request body
        client_max_body_size 10M; # 10 megabytes
    }
}
```
```
sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/
```

## install certbot
Ref: https://letsencrypt.org/docs/
https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-22-04
```
sudo snap install core; sudo snap refresh core
sudo apt remove certbot
sudo snap install --classic certbot
# optional sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo certbot --nginx -d example.com -d www.example.com
```


# setup dockerise envirnment for shared postgres_db, dockerise nest backend and react UI

### setup postgres DB
```
services:
  postgres:
    image: postgres:14-alpine
    container_name: postgres14_db
    restart: always
    #ports:
    #  - "5431:5432"
    volumes:
      - /opt/apps/pgsql-new/db:/var/lib/postgresql/data
      - /opt/apps/pgsql-new/etc/postgresql.conf:/etc/postgresql/postgresql.conf
      - /opt/apps/pgsql-new/etc/pg_hba.conf:/etc/postgresql/pg_hba.conf
    networks:
      - app-network
volumes:
  db:
 
networks:
  app-network:
    external: true
```

### setup UI and Backend Server
```
nvm use 18.18.0
UI_CODE="<UI_REPO_DIR_PATH>"
BACKEND_CODE="<BACK_END_REPO_DIR_PATH>"
ROOT_DIR="/opt/apps/<MY_APP>/(''|'dev'|'prod')"

# step 1: update code from origin for UI
cd "$UI_CODE"
rm -rf build
git checkout develop
git pull
npm ci
npm run build:dev
cd build
cp -r * /<ROOT_DIR>/frontend

# UI deploynment completed
# step 2 Start Backend Deploynment.

# step 2.1 Update code

cd "$BACKEND_CODE"
git checkout develop
git pull

#step 2.2 docker stop, remove
cd "$ROOT_DIR"
docker stop <DOCKER_CONTAINER_NAME> || true
docker rm  <DOCKER_CONTAINER_NAME> 

#step 2.3 docker build
cd "$BACKEND_CODE"
docker build -t  <DOCKER_IMAGE_NAME> :latestdev .
cd "$ROOT_DIR"

#step 2.4 restart server
docker compose up -d
```


docker-compose.yml 
```
version: '3.8'

services:
  backend-dev:
    image: backend:latestdev
    container_name: backend-dev
    ports:
      - "5050:8080"
    volumes:
      - /opt/apps/<MY_APP>/dev/logs:/opt/app/logs
      - /opt/apps/<MY_APP>/dev/certs:/opt/app/certs
    env_file:
      - .env
    networks:
      - app-network
    restart: always

networks:
  app-network:
    external: true
```

## option 2 generate UI Build: Using docker

```
REPO_DIR="<UI_REPO_DIR_PATH>"
APP_DIR="/opt/apps/<MY_APP>/(''|'dev'|'prod')"

# step 1
cd "$REPO_DIR"
git checkout develop
git pull

#step2 docker stop, remove and build
docker build -t <MY-APP-UI>:latestdev .

#step 3 run docker build
docker run -v /home/ubuntu/apps/<MY_APP>/dev/frontend:/app/build -t <MY-APP-UI>:latestdev
```
