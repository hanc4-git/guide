# **fedora setup guide**
UNLV\
the new version is available on [GitHub](https://github.com/hanc4-git?tab=repositories).

## installation
[Fedora 43 Post Install Guide](https://github.com/devangshekhawat)
[7 Things You MUST DO After Installing Fedora Linux](https://youtu.be/RrRpXs2pkzg)

## bazzite for gaming
*[bazzite 42 - November 3, 2025](https://bazzite.gg/)*

### bazzite installation
1. `INSTALLATION SUMMARY\SYSTEM\Installation Destination`
2. select **Local Standard Disk**
3. **Done**
4. `INSTALLATION SUMMARY\USER SETTINGS`
5. create *username* and *password*
6. **Done**

### system update
open **System Update**\
	**y**

## fedora
*[fedora_kde_plasma-43.1 - October 28, 2025](https://fedoraproject.org/kde/download)*

### flatpak
[built-in](https://flatpak.org/setup/)\
install **[Flathub](https://flathub.org/en)**

- option to add flathub use **Konsole**\
  	open **Konsole** *(Ctrl+Alt+T)*\
	`flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo`

### [multimedia codecs](https://www.linuxfordevices.com/tutorials/linux/installing-multimedia-codecs-linux)
`sudo dnf install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm`
>free

`sudo dnf install https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm`
>non free

```
sudo dnf update 
sudo dnf install gstreamer1-plugins-{bad-\*,good-\*,base} gstreamer1-plugin-openh264 gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel
sudo dnf install lame\* --exclude=lame-devel
sudo dnf group upgrade --with-optional Multimedia
```

### tuned
[built-in](https://github.com/redhat-performance/tuned)\
`tuned-adm list`

### [fastfetch](https://github.com/fastfetch-cli/fastfetch)
```
dnf install fastfetch
fastfetch
```

### systam update
1. open **Software**
2. `Software\Updates`
3. click **Refresh**
4. **Download**
5. **Restart & Update**

	- option to use terminal
		open **Terminal** *(Ctrl+Alt+T)*
		```
		sudo apt -y update && sudo apt -y upgrade
		sudo apt autoremove
  		```

## installation video
[Geant4 Tutorial 1: Installation and Testing of Geant4](https://youtu.be/Lxb4WZyKeCE) ([kor](https://youtu.be/gVcbeLQEHNw))\
[CERN ROOT Tutorial 2: Installing ROOT](https://youtu.be/QItrmchEQWE) ([kor](https://youtu.be/J8iQVm0DLzY))

## [geant4](https://geant4.web.cern.ch)

### [geant4 prerequisites](https://geant4-userdoc.web.cern.ch/UsersGuides/InstallationGuide/html/gettingstarted.html)
`sudo dnf install cmake gcc g++ expat-devel libXmu-devel motif-devel mesa-libGL-devel qt5-qtbase qt5-qtbase-devel

### geant 4 installation
*[Geant4 10.7/patch-04 - September 9, 2022](https://geant4.web.cern.ch/support/download)*
```
mv /home/user($username}/Downloads/geant{geant4_version}.tar.gz ~
tar -xvf geant{geant4_version}.tar.gz
cd geant{geant4_version}
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_QT=ON ../
lscpu
make -jN
```
>N = Number of CPUs

`sudo make install -jN`

### environment variables settings
```
cd ~
cd /usr/local/bin
. geant4.sh
```

- option to [permanent environment variables settings](https://devconnected.com/set-environment-variable-bash-how-to)\
	`sudo nano /home/user{$username}/.bashrc`
	```
	source /usr/local/bin/thisroot.sh
	source /usr/local/bin/geant4.sh
 	```
 	>at the last line

	```
	Ctrl+o
	enter
	Ctrl+x
 	```

### run Example B1
```
cd geant{geant4_version}
cd examples/basic/B1
mkdir build
cd build
cmake ..
make
./exampleB1
run/beamOn 100
exit
```

- option to batch mode
  	```
	cd geant{geant4_version}
	cd examples/basic/B1/build
	vim batch.mac
	i
	```
  	>insert mode

	```
	/run/beamOn 100
  	ESC
 	```
  	>exit insert mode
     
   	*`:wq or :x or :ZZ`*
  	>write (save) and quit

	```
	./exampleB1 batchmac
	exit
 	```
	
## [root](https://root.cern)

### [root dependencies](https://root.cern/install/dependencies/)
```
sudo dnf groupinstall "Development Tools" "C Development Tools and Libraries"
sudo dnf install git vim make cmake gcc-c++ gcc binutils libX11-devel libXpm-devel libXft-devel libXext-devel python openssl-devel
sudo dnf install redhat-lsb-core gcc-gfortran pcre-devel mesa-libGL-devel mesa-libGLU-devel glew-devel ftgl-devel mysql-devel fftw-devel cfitsio-devel graphviz-devel libuuid-devel avahi-compat-libdns_sd-devel openldap-devel python3-numpy libxml2-devel gsl-devel readline-devel qt5-qtwebengine-devel R-devel R-Rcpp-devel R-RInside-devel
```

### root installation
[ROOT 6.28/04 - May 7, 2023](https://root.cern/install/all_releases/)
```
mv /home/user{$username}/Downloads/root{$root_version}.source.tar.gz ~
tar -xzvf root{$root_version}.source.tar.gz
cd root{$root_version}
cd build
cmake -Dbuiltin_llvm=ON ../
make -jN
sudo make install -jN
```

### environment variables settings
```
cd ~
cd /usr/local/bin
source thisroot.sh
```	

### run
`root`\
	**-l**: without logo\
	**--web=off**: revert to TBrowser\
	**new TBrowser**: RBrowser\
	**TRootBrowser**: TBrowser

`.q`

## optional
- option to adjust the screen size for bazzite
	1. `Settings\Expert\Display\Screen\Graphics Controller`
 	2. select **VBoxSVGA**
  	3. **OK**

- option to install virtualbox **Guest Additions**
	1. `Menu Bar\Devices\Insert Guest Additions`
	2. click **Run**

	- option to run\
		`home\VBox_GAs_{VBoxClient_version}`
		1. double-click **VBoxLinuxAdditions.run**

  	- option to use **Terminal**
  	  	1. right-click **VBoxLinuxAdditions.run**
  	  	2. **Run as Program**
  	  	```
		VBoxService --version
		sudo gpasswd -a user{$username} vboxsf
		sudo shutdown -r now
  	  	```
	
- option to [asus](https://asus-linux.org/)\
1. open **Software**
2. `Software\Updates`
3. click **Refresh**
4. **Download**
5. **Restart & Update**

	- option to use **Konsole**
		open **Konsole** *(Ctrl+Alt+T)*
		```
		sudo dnf update -y
		sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm	//enable rpm fusion
		sudo dnf update -y
		sudo dnf install kernel-devel
		sudo dnf install akmod-nvidia xorg-x11-drv-nvidia-cuda
		sudo systemctl enable nvidia-hibernate.service nvidia-suspend.service nvidia-resume.service nvidia-powerd.service
		shutdown -r now
  		```

		`sudo cat /sys/module/nvidia_drm/parameters/modeset`
		>query external displays

		- asusctl
   		```
		sudo dnf copr enable lukenukem/asus-linux
		sudo dnf update
		```
     
  		- supergfxctl
  	  	```
		sudo dnf install asusctl supergfxctl
		sudo dnf update --refresh
		sudo systemctl enable supergfxd.service
		```

	  	- rog control center\
		`sudo dnf install asusctl-rog-gui`

		$ shutdown -r now

	  	- custom kernel
 	 	>dirvers fixes

 		```
		sudo dnf config-manager setopt fedora.excludepkgs=kernel,kernel-core,kernel-modules,kernel-uki-virt,kernel-devel,kernel-modules-extra,kernel-modules-core,kernel-devel-matched	//disable stock kernel updates
		sudo dnf config-manager setopt updates.excludepkgs=kernel,kernel-core,kernel-modules,kernel-uki-virt,kernel-devel,kernel-modules-extra,kernel-modules-core,kernel-devel-matched	//disable stock kernel updates
		sudo dnf config-manager setopt updates-testing.excludepkgs=kernel,kernel-core,kernel-modules,kernel-uki-virt,kernel-devel,kernel-modules-extra,kernel-modules-core,kernel-devel-matched	//disable stock kernel updates
		sudo dnf copr enable bieszczaders/kernel-cachyos
		sudo dnf install kernel-cachyos kernel-cachyos-devel-matched
		sudo dnf update

//option to tuned
//
https://github.com/redhat-performance/tuned
open konsole												//Ctrl+Alt+T
	$ dnf install tuned
	$ systemctl start tuned
	$ systemctl enable tuned
	$ tuned-adm active
	$ tuned-adm list

### [ppd](https://gitlab.freedesktop.org/upower/power-profiles-daemon#power-profiles-daemon)
1. open **Software Manager**
2. install **power-profiles-daemon**

	- option to use **[Konsole](https://linuxconfig.org/how-to-manage-power-profiles-over-d-bus-with-power-profiles-daemon-on-linux)**
		open **Konsole** *(Ctrl+Alt+T)*
		```
		sudo dnf install power-profiles-daemon
  		sudo dnf remove tuned tuned-ppd
		sudo systemctl enable power-profiles-daemon.service
  		```
		>enable service

		```
		powerprofilesctl list
		sudo shutdown -r now
  		```

  			- option to version 40 below
   				`sudo dnf remove power-profiles-daemon

- option to [tlp](https://linrunner.de/tlp/installation/index.html)\
	open **Konsole** *(Ctrl+Alt+T)*
	```
	sudo dnf install tlp tlp-rdw
	sudo dnf remove tuned tuned-ppd
	sudo systemctl enable tlp.service
	sudo systemctl mask systemd-rfkill.service systemd-rfkill.socket
	sudo tlp start
	tlp-stat -s

 		- option to get tlp repository
			`sudo dnf install https://repo.linrunner.de/fedora/tlp/repos/releases/tlp-release.fc$(rpm -E %fedora).noarch.rpm`

 		- option to version 40 below
 			`sudo dnf remove power-profiles-daemon
