# Termux Desktops
Collection of scripts to launch Desktops with audio in Termux X11. You have also all the information needed to install your prefered Linux Distro and connect to it in the following steps. 

# 📚 Index
* 1️⃣ [First steps](#first-steps)
* ⚙️ [Installing Desktops](#installing-desktops)
* 💻 [Running the Desktops to use them with Termux X11](#running-desktops)
* ⬇️ [Download scripts easily](#easy-download)
* 🎨 [Customizations - Themes](#customizations)
* 🔥 [Hardware acceleration in Termux](https://github.com/LinuxDroidMaster/Termux-Desktops/blob/main/Documentation/HardwareAcceleration.md)

---  
<br>

# 1️⃣ First steps <a name=first-steps></a>
We are going to use Termux and Termux X11 in order to have a full Linux Desktop in our Android devices. 

* [[Video] How to install Termux](https://www.youtube.com/watch?v=OMJAyq5NHp0)

* [[Video] How to install and use Termux X11](https://www.youtube.com/watch?v=mXkXzFqSeYE)

* [[Video] How to install a COMPLETE Linux environtment on ANDROID - Customizing XFCE4 - Neon theme - No Root](https://www.youtube.com/watch?v=rDHyPw_7ETs)

* [[Video] How to install a Linux distro on Android](https://www.youtube.com/watch?v=OMJAyq5NHp0)


<details>
<summary><strong> [Commands] How to install a Linux Distro on Termux with proot-distro (No Root)</strong></summary>

You can check the video described in the First Steps section. The written steps are the following ones: 

1. Open Termux
2. Install proot-distro  
```
pkg update
pkg install proot-distro
```
3. Install Debian (or the distor you prefer)
```
proot-distro install debian
```
4 Log in to the distro 
```
proot-distro login debian
```
</details>

<details>
<summary><strong>[Commands ]Create an user with sudo privileges</summary></strong>

The steps are described in the video linked in the previous point. 

1. Install needed packages
```
apt update -y
apt install sudo nano adduser -y
```
2. Create an user
```
adduser droidmaster
```
3. Give the user sudo privileges
```
nano /etc/sudoers

# Add the following line to the file
droidmaster ALL=(ALL:ALL) ALL
```
4. Check you can execute sudo commands (it should return `root`)
```
sudo whoami 
```  

</details>  

---  
<br>

# ⚙️ Installing Desktops <a name=installing-desktops></a> 

I have installed different desktops, if you want me to test any other just leave a comment in any video and I will check it: 

> [!NOTE]
> In the videos I'm using VNC but with Termux X11 installing the tigervnc server and dbus is no longer required.

* [[Video] How to install XFCE4](https://www.youtube.com/watch?v=LO8LWh5tPg8&list=PL4worxVHtqXo8EPHfLcoy5tPwjVSaqdB5&index=6)

```
# Commands: 
proot-distro login debian --user droidmaster
```
```
sudo apt install xfce4
```

* [[Video] How to install LXDE](https://www.youtube.com/watch?v=9b9_9YNsCXc)
```
# Commands: 
proot-distro login debian --user droidmaster
```
```
sudo apt install lxde
```

* [[Video] How to install Cinnamon](https://youtu.be/_wZO5RZu2R8?feature=shared)
```
# Commands: 
proot-distro login debian --user droidmaster
```
```
sudo apt install cinnamon -y
```

* [[Video] How to install GNOME](https://www.youtube.com/watch?v=XedxyTTHYnI)
```
# Commands: 
proot-distro login debian --user droidmaster
```
```
sudo apt install dbus-x11 nano gnome gnome-shell gnome-terminal gnome-tweaks gnome-software nautilus gnome-shell-extension-manager gedit tigervnc-tools gnupg2 -y
```
```
for file in $(find /usr -type f -iname "*login1*"); do rm -rf $file
done
```

* [[Video] How to install KDE Plasma](https://www.youtube.com/watch?v=fru4SWvUowI&list=PL4worxVHtqXo8EPHfLcoy5tPwjVSaqdB5&index=2)  - Not recommended due to performance issues (KDE Plasma requires more resources)
```
# Commands: 
proot-distro login debian --user droidmaster
```
```
sudo apt install kde-plasma-desktop
```

---  
<br>

# 💻 Running the Desktops for use with Termux X11 <a name=running-desktops></a>
All the scripts in this repository are prepared to run the different Desktops with audio in an easy way. 

First you need to install the following packages in Termux: 
```
pkg update
pkg install x11-repo
pkg install termux-x11-nightly
pkg install pulseaudio
```

Then, you just need to download the script corresponding to the Desktop you have installaded, give it permissions to execute it and run it (in Termux, not in proot-distro): 
```
# Download the script to Termux
chmod +x startxfce4_debian.sh
./startxfce4_debian.sh
```

---  
<br>

# ⬇️ Download scripts easily: <a name=easy-download></a> 

> [!NOTE]  
> By default this script works with the user "droidmaster". If you create a user with a different name in proot-distro, please change where it says "droidmaster" inside the scripts.

* startgnome_debian.sh
```
wget https://raw.githubusercontent.com/LinuxDroidMaster/Termux-Desktops/main/startgnome_debian.sh
```

* startxfce4_debian.sh
```
wget https://raw.githubusercontent.com/LinuxDroidMaster/Termux-Desktops/main/startxfce4_debian.sh
```

* startlxde_debian.sh
```
wget https://raw.githubusercontent.com/LinuxDroidMaster/Termux-Desktops/main/startlxde_debian.sh
```

* startcinnamon_debian.sh
```
wget https://raw.githubusercontent.com/LinuxDroidMaster/Termux-Desktops/main/startcinnamon_debian.sh
```

* startkde_debian.sh
```
wget https://raw.githubusercontent.com/LinuxDroidMaster/Termux-Desktops/main/startkde_debian.sh
```

# 🎨 Customizations <a name=customizations></a>
* How to install nerd fonts (this allows you to have icons in the terminal):
```
bash -c  "$(curl -fsSL https://raw.githubusercontent.com/officialrajdeepsingh/nerd-fonts-installer/main/install.sh)"
```
* [How to customize XFCE4 - Neon Theme](https://www.youtube.com/watch?v=rDHyPw_7ETs)
