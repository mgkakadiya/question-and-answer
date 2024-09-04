# Instance Setup steps (Install below tools if not exist)
## install Docker
## install git
## install nvm
## install nginx
## install certbot


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
