# thingsboard-windows11-docker-setup
Step-by-step guide to installing and running ThingsBoard CE on Windows 11 using Docker Desktop. Includes docker-compose.yml configuration, login credentials, and troubleshooting tips.
# ThingsBoard Windows 11 Docker Setup

This repository contains a complete step-by-step guide to installing and running **ThingsBoard Community Edition** on **Windows 11** using **Docker Desktop**.

## 📌 Features
- Full Docker Desktop installation instructions
- `docker-compose.yml` ready to use
- Default login credentials
- Works on Windows 11 with Docker Compose V2

## 🛠 Installation Steps

### 1. Install Docker Desktop
1. Download: [Docker Desktop](https://www.docker.com/products/docker-desktop)
2. Install like any other Windows app.
3. Open Docker Desktop → **Settings** → **General** → enable *Use Docker Compose V2*.
4. Keep Docker Desktop running.

### 2. Create Project Folder
```bash
mkdir thingsboard
cd thingsboard

### 3 . Create docker-compose.yml
version: '3.3'
services:
  tb:
    image: thingsboard/tb-postgres
    ports:
      - "8080:9090"
      - "1883:1883"
      - "5683-5688:5683-5688/udp"
    environment:
      TB_QUEUE_TYPE: in-memory
      INSTALL_TB: "false"
      LOAD_DEMO: "true"
    volumes:
      - tb-data:/data
      - tb-logs:/var/log/thingsboard
volumes:
  tb-data:
  tb-logs:

### 4. Start ThingsBoard
docker compose up -d
docker logs -f thingsboard-tb-1
ThingsBoard is up and running


5. Access Web Interface

Open http://localhost:8080

Username: tenant@thingsboard.org

Password: tenant



If you want, I can also make a **SEO-optimized README** with keywords like “IoT platform installation,” “Docker ThingsBoard tutorial,” and “Windows 11 IoT setup” so your repo ranks higher in GitHub and Google searches. That would push more traffic to your GitHub.  

Do you want me to create that optimized README for you?

