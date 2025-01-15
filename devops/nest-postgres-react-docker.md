# Instance Setup steps (Install below tools if not exist)
## install Docker

add docker installtion steps here
## Docker Installation and Setup

### Prerequisites
- For Ubuntu:
  - Update package index: `sudo apt-get update`
  - Install prerequisites:
    ```bash
    sudo apt-get install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg \
        lsb-release
    ```
  - Add Docker's official GPG key:
    ```bash 
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    ```
  - Set up stable repository:
    ```bash
    echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```
  - Install Docker Engine:
    ```bash
    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io
    ```
  - Verify installation: `sudo docker run hello-world`
  - (Optional) Add user to docker group to run without sudo:
    ```bash
    sudo groupadd docker
    sudo usermod -aG docker $USER
    newgrp docker
    ```

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
### How to Install NVM (Node Version Manager) for Windows
### Steps to Install NVM on Windows:

1. **Download NVM for Windows**:
   - Go to the official NVM for Windows GitHub repository: [NVM for Windows Releases](https://github.com/coreybutler/nvm-windows/releases).
   - Download the latest **nvm-setup.zip** file.

2. **Install NVM**:
   - Extract the ZIP file and run the `nvm-setup.exe` installer.
   - Follow the installation prompts. The default location is typically `C:\Program Files\nvm`, but you can change it if needed.
   - After installation, NVM will automatically create a folder for node versions at `C:\Program Files\nodejs`.

3. **Configure Environment Variables**:
   - During installation, NVM may modify your `PATH` automatically, but if it doesn't, add the following paths manually:
     - `C:\Program Files\nvm` (for NVM).
     - `C:\Program Files\nodejs` (for Node.js versions).

4. **Verify Installation**:
   - Open a new Command Prompt or PowerShell and run:
     ```bash
     nvm version
     ```
     If installed correctly, this should display the NVM version.

5. **Install a Node.js Version**:
   - To install a specific version of Node.js, use the command:
     ```bash
     nvm install <version>
     ```
     For example, to install Node.js version 16.13.0:
     ```bash
     nvm install 16.13.0
     ```

6. **Use a Specific Node.js Version**:
   - To use the installed Node.js version:
     ```bash
     nvm use 16.13.0
     ```
     Verify by running:
     ```bash
     node -v
     ```

7. **Optional**: Set a Default Node Version:
   - To set a default version globally, use:
     ```bash
     nvm use <version> default
     ```

---

You now have NVM set up on your Windows machine to manage multiple Node.js versions!

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

for permission of all folders, follow steps from here.

#### https://stackoverflow.com/questions/25774999/nginx-stat-failed-13-permission-denied/25776092#25776092

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
