# ThingsBoard Windows 11 Docker Setup

This repository contains a complete step-by-step guide to installing and running **ThingsBoard Community Edition (IoT Platform)** on **Windows 11** using **Docker Desktop**.  
Supports MQTT, CoAP, and HTTP protocols for IoT device data collection.

## 📌 Features
- Full Docker Desktop installation instructions
- Ready-to-use `docker-compose.yml` file
- Default login credentials
- Compatible with Docker Compose V2
- Supports MQTT, CoAP, and HTTP protocols

---

## 🛠 Installation Steps

### **1. Install Docker Desktop**
1. Download: [Docker Desktop](https://www.docker.com/products/docker-desktop)  
2. Install like any other Windows app.  
3. Open Docker Desktop → **Settings** → **General** → enable *Use Docker Compose V2*.  
4. Keep Docker Desktop running.  

---

### **2. Create Project Folder**
```bash
mkdir thingsboard
cd thingsboard
````

---

### **3. Create `docker-compose.yml`**

```yaml
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
```

---

### **4. Start ThingsBoard**

```bash
docker compose up -d
docker logs -f thingsboard-tb-1
```

Look for:

```
ThingsBoard is up and running
```

---

### **5. Access Web Interface**

* Open: [http://localhost:8080](http://localhost:8080)
* **Username:** `tenant@thingsboard.org`
* **Password:** `tenant`


---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).

---

⭐ **If you find this helpful, please star the repo to support the project!**

```
