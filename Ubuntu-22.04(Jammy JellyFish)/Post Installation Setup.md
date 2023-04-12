# Check For Updates

From the terminal:
```bash
sudo apt update && sudo apt upgrade
```

# Install Missing Drivers
From **Software & Updates** > **Additional Drives** install the missing drivers.

# Install Gnome Tweaks
It lets you manage behaviour of the Gnome Windows Manager, install themes,icons and fonts. 
```bash
sudo apt install gnome-tweaks
sudo apt install gnome-shell-extension-manager
```

To see many gnome tweaks available for your operating system visit: 
https://extensions.gnome.org/
You can browse extensions from the website or from the gnome-shell-extension-manager(Extension Manager) and install it.

For the ability to directly install the extensions from the browser, install:
For Chrome:
```bash
sudo apt install chrome-gnome-shell 
```
For Firefox:
https://addons.mozilla.org/en-US/firefox/addon/gnome-shell-integration/

## Custom Themes and Icons
To install custom themes and icons: 
Install : https://extensions.gnome.org/extension/19/user-themes/
and create two directories `.themes` and `.icons` in your home directory. Extract your downloaded tar.xz files inside these directory.

Themes or Icons that you downloaded needs to be placed inside these directory so that you can change it from the gnome-tweaks.

# Setup Multimedia Codecs
To support video formats install the codecs and VLC Media Player.
```bash
sudo apt install ubuntu-restricted-extras
sudo apt install vlc
```

# Enable Minimize on Click
Wierdly, when you click on the icons on dock, they do nothing. To enable feature for click on minimize run the following command:
```bash
gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'
```

# Enable Firewall
Enable the default ubuntu firewall.
```bash
sudo ufw enable
```
Note: ufw is not enabled by default in Ubuntu.

To install a GUI for ufw(**Firewall**). Install it via command:
```bash
sudo apt install gufw
```

# Enable Backups
deja-dup(**Backups**) is a wonderful tool for creating backups for your system. I recommend creating the cloud backup for your home folder.
If **Backups** is not already available in your system, install it using following bash command:
```bash
sudo apt install deja-dup
```

I find it easier to save backups in the google drive which requires additional package to be installed:
```bash
sudo apt install python3-drive
```

# Install Flatpak
Install flatpak software store using following command:
Note: Since Ubuntu 20.04, graphical installation of Flatpak apps is not supported and Flatpak plugin will also install a deb version of Software and result in two Software apps being installed at the same time. 
Don't : `sudo apt install gnome-software-plugin-flatpak`

So use browser and navigate to flathub to install the Flatpak apps. 
https://flathub.org/home

```bash
sudo apt install flatpak
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

Restart the computer.
## Installing the Flatpak App
```bash
flatpak install flathub io.atom.Atom
```

# Install Preload
It monitors the frequently running application and eventually use this analysis to speed up the application load time.
```bash
sudo apt install preload
```

# Install and Enable TimeShift
```bash
sudo apt install timeshift
```

# Laptop Tweaks
This is for battery optimization for latops.
```bash
sudo apt install tlp tlp-rdw
sudo systemctl enable tlp
sudo systemctl start tlp
```
## Enable Battery Percentage
```bash
gsettings set org.gnome.desktop.interface show-battery-percentage true
```

# Essential Cmd Tools

```bash
sudo apt install curl
```

# Essential Tools

## App Image Launcher
Some applications, in Ubuntu cannot be installed directly from the package manager. In case of that other alternatives are snap store or flatpak. Personally, I prefer App Images to install those application for the sake of simplicity and dependency issues. Note: App Image has a downside that they take up large spaces. Only prefer it if there are no .deb packages available as well. In doubt, use app images.

App Image Launcher makes it easier to manage these app images files by integrating them in central location `$HOME/Applications` and gives them ability to pin on application launcher.

To Install the App Image Launcher, follow this official github link:
https://github.com/TheAssassin/AppImageLauncher

From the Releases, download the latest .deb package and install it.
```bash
sudo dpkg -i appimagelauncher_x.x.x-xxx.bionic_amd64.deb
```

You can now easily manage, app image files using App Image Launcher.


## Obsidian
Obsidian is a fantastic tool for creaing notes using markdown. For instance this, note has been created using Obsidian. Other alternative to Obsidian is Notion (https://www.notion.so/) which is equally powerful and I recommend using Notion first for beginners. Obsidian has its few cons in comparision to Notion, however I like Obsidian for its simplicity to add plugins, and knowledge map that links pages together.

To install the Obsidian, download the AppImage file from the official site:
https://obsidian.md/

Open the terminal in Download folder and execute the following command:
```bash
chmod u+x Obsidian-x.x.x.AppImage
```

Now, open the AppImage file and you will be prompted by App Image Launcher for setting up the Obsidian. Simply select the option `Integrate and run` . This will move the App Image file to Applications inside your home directory. From there you can pin the application to the dock.

## Chrome
First, get a deb file from official site and install issuing the following command:
```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## Microsoft Teams
From flatpak: https://flathub.org/home , get the installation command:
```bash
flatpak install flathub com.github.IsmaelMartinez.teams_for_linux
```

## Draw.io
From flatpak: https://flathub.org/home , get the installation command:
```bash
flatpak install flathub com.jgraph.drawio.desktop
```

## Discord
From flatpak: https://flathub.org/home , get the installation command:
```bash
flatpak install flathub com.discordapp.Discord
```

## Slack
From flatpak: https://flathub.org/home , get the installation command:
```bash
flatpak install flathub com.slack.Slack
```
