# **archlinux setup guide**
UNLV\
the new version is available on [GitHub](https://github.com/hanc4-git?tab=repositories).

## installation
[CachyOS Post Install](https://wiki.cachyos.org/configuration/post_install_setup/)\
[CachyOS Gaming](https://wiki.fascinated.cc/category/cachyos-gaming)\
[Arch Linux Installation guide](https://wiki.archlinux.org/title/Installation_guide)
[Installing Arch Linux with BTRFS and Disk Encryption](https://itsfoss.com/arch-linux-install-encrypted-btrfs/)
> not for virtualbox

[How To Install Arch Linux in VirtualBox (2025) | Arch Linux Installation ](https://youtu.be/DbeL7ehxpZ0?si=sBVLycxjBaTJ-9fB)\
[7 Things After Installing EndeavourOS (MUST DO!)](https://youtu.be/StHVU-Zvacs)

## cachyos
*[CachyOS - August 24, 2025](https://cachyos.org/download/)*

### cachyos installation
1. `liveuser\Desktop Session: Plasma (X11)`
2. switch to **Wayland**
3. login without *password*
4. **Launch installer**
5. `CachyOS Installer\Partitions\Erase disk`
6. select **ext4**
7. `CachyOS Installer\All done`
8. deselect **Restart now**
9. click **Done**
10. restart

### run
1. `Details\Storage\Controller: IDE`
2. click **IDE Secondary Device 0:**
3. select **Remove Disk From Virtual Drive**
4. click **Start**

### system update
1. `CachyOS Hello\Apps\Tweaks`
2. click **System Update**

  - option to use **Konsole**\
		open **Konsole** *(Ctrl+Alt+T)*\
    	`sudo pacman -Syyu`\
      		**-s**: option for sync\
      		**-y**: refreshes package database\
      		**-u-**: upgrade packages

### [steam](https://wiki.cachyos.org/configuration/gaming/)
>not for virtualbox
1. `CachyOS Hello\Apps\Tweaks`
2. click **Install Gaming packages**
3. restart

  - option to use **Konsole**\
    	open **Konsole** *(Ctrl+Alt+T)*\
		```
    	sudo pacman -S cachyos-gaming-meta
    	sudo pacman -S cachyos-gaming-applications
    	```

### [flatpak](https://flatpak.org/setup/)
open **Konsole** *(Ctrl+Alt+T)*
```
sudo pacman -S flatpak
flatpak --version
shutdown -r now
```

- option to add flathub\
	`flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo`

### multimedia codecs
[built-in](https://itsfoss.gitlab.io/post/how-to-install-ffmpeg-in-linux/)\
`ffmpeg -version`

### ppd
[built-in](https://gitlab.freedesktop.org/upower/power-profiles-daemon#power-profiles-daemon/)\
`pwerprofilesctl list`
	
### fastfetch
[built-in](https://github.com/fastfetch-cli/fastfetch)\
`fastfetch`

## archlinux
*[archlinux - November 01, 2025](https://archlinux.org/download/)*

### archlinux installation
`pacman -Syu`
> system update

`pacman-key --populate`
> update database

`sudo pacman -S archlinux-keyring`\
	**y**

`pacman -S archinstall`\
	**y**

`archinstall`

### installation setup
1. Disk configuration
   	1. Partitioning
	2. **Use a best-effort default partition layout**
	3. *space bar*: *space bar* or *tab* to select
	4. **ext4**: Filesystem

   	- option to btrfs
   	  > not for virtualbox
   	  
   		**btrfs**: Filesystem\
		**No**\
		**Use compression**

2. Swap\
	**Yes**: zram

	- option to Bootloader for asus\
   		**systemd-boot**

3. Authentication
	1. Root password
	2. User account
	3. **Add a user**
	4. Should "username" be a superuser (sudo)?\
		**Yes**
	5. **Confirm and exit**

4. Profile
	1. Type
	2. **Desktop**
 	3. choose desktop environment
	4. Graphics Driver
	5. **All open-source**

	- option to setup audio
		1. Audio
		2. **pipeuire**
  		> audio server

5. Network configuration
	**Use NetworkManager**

6. Additional Packages\
   *firefox flatpak fastfetch*

7. Timezone
8. Install
	**Yes**
9. chroot into installation for post-installation configurations\
	**No**

### run
1. `Details\Storage\Controller: IDE`
2. click **IDE Secondary Device 0:**
3. select **Remove Disk From Virtual Drive**
4. click **Start**

### system update
open **Konsole** *(Ctrl+Alt+T)*\
`sudo pacman -Syyu`\
	**-s**: option for sync\
    **-y**: refreshes package database\
    **-u-**: upgrade packages

### [flatpak](https://flatpak.org/setup/)
open **Konsole** *(Ctrl+Alt+T)*
```
sudo pacman -S flatpak
flatpak --version
shutdown -r now
```

- option to add flathub\
	`flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo`

### multimedia codecs
[built-in](https://itsfoss.gitlab.io/post/how-to-install-ffmpeg-in-linux/)\
`ffmpeg -version`
		
### [ppd](https://gitlab.freedesktop.org/upower/power-profiles-daemon#power-profiles-daemon/)
open **Konsole** *(Ctrl+Alt+T)*
```
sudo pacman -S power-profiles-daemon
sudo systemctl enable --now power-profiles-daemon.service
powerprofilesctl list
shutdown -r now
```

### [fastfetch](https://github.com/fastfetch-cli/fastfetch)
```
pacman -S fastfetch
fastfetch
```

## eos
*[EndeavourOS_artemis - June 25, 2022](https://endeavouros.com)*

### eos installation
1. select **Start the Installer**
2. select **Online**
3. Erase disk
4. select **Swap to file**
> for lower RAM usage

### system update
1. select **Update Mirrors**
2. select **Update System**
3. select **Package cleanup configuration**

	- option to use **Konsole**\
		open **Konsole** *(Ctrl+Alt+T)*\
    	`sudo pacman -Syyu`\
      		**-s**: option for sync\
      		**-y**: refreshes package database\
      		**-u-**: upgrade packages

### [flatpak](https://flatpak.org/setup/)
open **Konsole** *(Ctrl+Alt+T)*
```
sudo pacman -Syu
sudo pacman -S flatpak
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak --version
shutdown -r now
```

### [multimedia codecs](https://itsfoss.gitlab.io/post/how-to-install-ffmpeg-in-linux/)
```
sudo pacman -Syu
sudo pacman -S ffmpeg
ffmpeg -version
```

### [ppd](https://gitlab.freedesktop.org/upower/power-profiles-daemon#power-profiles-daemon/)
open **Konsole** *(Ctrl+Alt+T)*
```
sudo pacman -S power-profiles-daemon
sudo systemctl enable --now power-profiles-daemon.service
powerprofilesctl list
shutdown -r now
```

### [fastfetch](https://github.com/fastfetch-cli/fastfetch)
```
pacman -S fastfetch
fastfetch
```

## installation video
[Geant4 Tutorial 1: Installation and Testing of Geant4](https://youtu.be/Lxb4WZyKeCE) ([kor](https://youtu.be/gVcbeLQEHNw))\
[CERN ROOT Tutorial 2: Installing ROOT](https://youtu.be/QItrmchEQWE) ([kor](https://youtu.be/J8iQVm0DLzY))

### [geant4 prerequisites](https://geant4-userdoc.web.cern.ch/UsersGuides/InstallationGuide/html/gettingstarted.html)
`sudo pacman -S cmake gcc expat libxmu openmotif mesa qt5-base`

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
> N = Number of CPUs

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
 	> at the last line

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
  	> insert mode

	```
	/run/beamOn 100
  	ESC
 	```
  	> exit insert mode
     
   	*`:wq or :x or :ZZ`*
  	> write (save) and quit

	```
	./exampleB1 batchmac
	exit
 	```

## [root](https://root.cern)

### [root dependencies](https://root.cern/install/dependencies/)
```
sudo pacman -S --needed base-devel
sudo pacman -S git vim make cmake gcc binutils libx11 libxpm libxft libxext python openssl
sudo pacman -S gcc-fortran pcre mesa glu glew ftgl mysql fftw cfitsio graphviz util-linux-libs avahi openldap python3 libxml2 gsl readline qt5-webengine
```
**1**: default\
**y**: proceed

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
- option to install virtualbox **Guest Additions**
> cachyos has built-in

1. `menu bar\Devices\Insert Guest Additions`
2. copy and paste all files in **VBox_GAs_{VBoxClient_version}.iso** to **Documents**
3. right-click
4. **Open in Konsole**
```
ls -lh
chmod 777 VBoxLinuxAdditions.run
sudo ./VBoxLinuxAdditions.run
```

- option to fix virtualbox **Guest Additions**
  ```
  View\Seamless Mode
  Ctrl+L
  ```
  > back to windowed mode

- option to [spotify](https://itsfoss.com/install-spotify-arch/)\
  	open **Konsole** *(Ctrl+Alt+T)*\
	`sudo pacman -Syu spotify-launcher`

	- option to [flatpak](https://linuxways.net/arch/install-spotify-arch-linux/)
		```
   		flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
      	flatpak install spotify
  		```

- option to [steam](https://wiki.cachyos.org/configuration/gaming/)\
	`sudo pacman -Syu steam`

- option to [yay](https://itsfoss.com/install-yay-arch-linux/)
  	```
	sudo pacman -Syu
	sudo pacman -S --needed base-devel git
	git clone https://aur.archlinux.org/yay.git
	cd yay
	makepkg -si
	yay --version
   	```
   
- option to disable sleep
	```
	System Settings/Workspace/Workspace Behavior/Screen Locking
	System Settings/Hardware/Power Management/Energy Saving
 	```

	- option to gnome\
 		`sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target`
		
- option to [multimedia codecs](https://itsfoss.gitlab.io/post/how-to-install-ffmpeg-in-linux/)
	open **Konsole** *(Ctrl+Alt+T)*
  	```
	sudo pacman -Syu
	sudo pacman -S ffmpeg
	ffmpeg -version
	```

- option to [asus](https://asus-linux.org/)\
	open **Konsole** *(Ctrl+Alt+T)*\
	`pacman -S linux-firmware amd-ucode`
	> `intel-ucode` for intel

	```
 	pacman-key --recv-keys 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
  	pacman-key --finger 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
	pacman-key --lsign-key 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
	pacman-key --finger 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
 	```
	> g14 repo
 
	`pacman -Syu`

	- asusctl
   		```
		pacman -S asusctl power-profiles-daemon
		systemctl enable --now power-profiles-daemon.service
     	```
  
  	- supergfxctl
  	  	```
		pacman -S supergfxctl
		systemctl enable --now supergfxd
		```

  	- rog control center\
		`pacman -S rog-control-center`

  	- custom kernel
 	 > dirvers fixes

	`pacman -Syu linux-g14 linux-g14-headers`

	- option to grub\
		`grub-mkconfig -o /boot/grub/grub.cfg`

	- nvidia
		1. `cat /proc/driver/nvidia/gpus/bus_address/power`
  		> query status

		2. `pacman -S nvidia-utils vulkan-icd-loader`

  			- option to enable
       			```
				systemctl enable nvidia-suspend.service nvidia-hibernate.service nvidia-resume.service
				systemctl enable --now nvidia-powerd
          		```

- option to [tuned](https://youtu.be/WTJw21XQjCc?si=jBvUkGmOBHtfHCq5)
	1. open **Konsole** *(Ctrl+Alt+T)*
 	2. `yay -S tuned-git`\
		**n**: cleanBuild\
		**n**: diffs\
		**y**

  	```
	sudo systemctl enable --now tuned
	tuned-adm active
	sudo systemctl status tuned
   	```

- option to [tlp](https://linrunner.de/tlp/installation/index.html)\
	open **Konsole** *(Ctrl+Alt+T)*
	```
	sudo pacman -S tlp tlp-rdw
	systemctl enable tlp.service
	systemctl enable NetworkManager-dispatcher.service
	systemctl mask systemd-rfkill.service systemd-rfkill.socket
	sudo tlp start
	tlp-stat -s
	```
