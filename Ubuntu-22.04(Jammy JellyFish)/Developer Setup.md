# Github Desktop
To install the Github Desktop. Follow this official github link: 
https://github.com/shiftkey/desktop

From the Releases, download the latest .deb package and install it.
```bash
sudo dpkg -i GitHubDesktop-linux-x.x.x-linux1.deb 
```

# Vs Code
Download .deb package from the official site and install it.
```bash
sudo dpkg -i code_x.xx._amd64.deb
```

# Insomnia
To install Insomnia, download .deb package from the link and install it.
https://insomnia.rest/download
```bash
sudo dpkg -i Insomnia.Core-xxx.deb
```

# Draw.io
From flatpak: https://flathub.org/home , get the installation command:
```bash
flatpak install flathub com.jgraph.drawio.desktop
```

---
## Python 
```bash
sudo apt install python3
sudo apt install python3-pip
```

### Virtual Environment
It is recommended to create different virtual environments for your python projects to separate dependencies.
```bash
sudo apt install python3-venv # To install venv
```
 Here is a short snipped on how to create and activate your environments:
 ```bash
 python3 -m venv venvName # To create environment named venvName 
 source venvName/bin/activate # To activate the environment 
 deactivate # To deactivate the environment
```

### MySql Dependency

For issue with pip install mysqlclient:
```bash
sudo apt-get install libmysqlclient-dev
```

## Node.js 
This is essential because the apt repository for ubuntu has only node version of 12. To get the latest stable v18, do the following from the terminal:
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash - 
sudo apt update 
sudo apt install nodejs 
node -v # verify version for node 
npm -v # verify version for npm
```

## Java
I prefer to install OpenJDK java via Ubuntu's package system.
```bash
sudo apt install default-jre
```