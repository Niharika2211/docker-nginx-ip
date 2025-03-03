# 🚀 Deploying Docker Machine with Nginx Custom IP

![Docker](https://img.shields.io/badge/Docker-🟦-blue) ![Shell Script](https://img.shields.io/badge/Shell_Script-💻-green) ![Cloud](https://img.shields.io/badge/Cloud-☁️-lightgrey) ![Linux](https://img.shields.io/badge/Linux-🐧-yellow) ![Nginx](https://img.shields.io/badge/Nginx-💚-green)

## 📌 Overview 📝
This repository contains scripts to **create a Docker machine**, install necessary packages, and deploy an **Nginx container with a custom IP**.

## 🛠 Prerequisites ⚡
Ensure you have the following before proceeding:
- 🖥️ Cloud Shell or any Linux-based system
- 🔑 Permissions to create Docker instances
- 🔐 Your **.pem key** for SSH authentication

---
## 📜 **Step-by-Step Guide** 🏗️

### **Step 1: Create a Docker Machine 🏭**
Write a script (`docker-machine.sh`) to create a Docker instance with the following:
- 🐳 Docker container with **Nginx custom IP**
- 🌐 DNS name **docker.nirvanan.online** (or any other configured name)
- 🏷️ **HOST ID** added in the script
- 🔐 Use **your .pem key** for authentication

### **Step 2: Set Up DNS for Docker Machine 🌍**
- 📌 Create a DNS entry in Docker: `docker.nirvanan.online`
- ✍️ Paste the DNS hostname in the script
- 🔑 Add the **HOST ID** and your **.pem key** in `docker-machine.sh`

### **Step 3: Execute `docker-machine.sh` in Cloud Shell ☁️**
```sh
chmod +x docker-machine.sh
./docker-machine.sh
```
- 🎯 Enter necessary details to create the Docker machine

### **Step 4: Deploy Nginx with Custom IP 🚀**
```sh
# 🔗 Connect to the Docker Machine
docker-machine ssh <docker-machine-name>

# 📥 Clone the repository containing Nginx custom IP setup
git clone https://github.com/your-nginx-repo.git
cd your-nginx-repo

# 🏗️ Build the Docker Image
docker build -t nginx-custom .

# 🚢 Run the Container
docker run --rm -d --name nginx-container -p 8080:80 nginx-custom
```

✅ **Verify the running container:**
```sh
docker ps
```

### **Step 5: Check Docker DNS & Container IP 🔍**
Since we have already created the Docker DNS, verify it along with the port ID.

```sh
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' nginx-container
```

✅ If we are able to see the container IP, then **SUCCESS!** 🎉

---

### **Install Docker & Dependencies 🛠️**
Run `docker-installations.sh`, which installs:
- 🐳 Docker & Docker Compose ✅
- 🛠️ Git ✅
- 🔄 tmux ✅
- 🌲 tree ✅

```sh
git clone https://github.com/your-repo.git
cd your-repo
chmod +x docker-installations.sh
./docker-installations.sh
```

---

## 📎 **Resources & References 📚**
- 📜 [Docker Documentation](https://docs.docker.com/)
- 🔗 [Docker Machine](https://docs.docker.com/machine/)

💡 **Happy Dockering! 🚢💙**
