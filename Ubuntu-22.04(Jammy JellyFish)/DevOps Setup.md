# Docker 
There are two variations of Docker that can be installed in Linux Based System.
1. Docker Engine
2. Docker Desktop

On, Windows and MacOS system, Docker Desktop is the only way to get docker running in the system, however both Docker Engine and Docker Desktop can be installed and run side by side in Linux. Personally, I prefer the Docker desktop installation for its ease of setup and usage.

To learn more about them follow the following links:
https://docs.docker.com/desktop/faqs/linuxfaqs/#what-is-the-difference-between-docker-desktop-for-linux-and-docker-engine

## Installation of Docker Desktop
These docs have been generated from the site: 
https://docs.docker.com/desktop/install/ubuntu/

### 1. Setup Apt Repository
```bash
sudo apt update
sudo apt install ca-certificates curl gnupg
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### 2. Download DEB Package and Install 
After downloading the .deb package install it via command:
```bash
sudo dpkg -i docker-desktop-x.xx.deb
```
If you run into any issue running the above command like dependency issue, run the following command:
```bash
sudo apt --fix-broken install
```
and proceed with .deb package installation again.

### 3. Confirm Installation
```bash
$ docker compose version
Docker Compose version v2.5.0
$ docker --version
Docker version 20.10.14, build a224086349
$ docker version
Client: Docker Engine - Community
Cloud integration: 1.0.24
Version:           20.10.14
API version:       1.41
...
```
