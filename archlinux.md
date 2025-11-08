# **archlinux setup guide**
UNLV\
the new version is available on [GitHub](https://github.com/hanc4-git?tab=repositories).

## installation
[CacvhyOS Post Install](https://wiki.cachyos.org/configuration/post_install_setup/)\
[CachyOS Gaming](https://wiki.fascinated.cc/category/cachyos-gaming)\
[Arch Linux Installation guide](https://wiki.archlinux.org/title/Installation_guide)
[Installing Arch Linux with BTRFS and Disk Encryption](https://itsfoss.com/arch-linux-install-encrypted-btrfs/)
>not for virtualbox

[How To Install Arch Linux in VirtualBox (2025) | Arch Linux Installation ](https://youtu.be/DbeL7ehxpZ0?si=sBVLycxjBaTJ-9fB)\
[7 Things After Installing EndeavourOS (MUST DO!)](https://youtu.be/StHVU-Zvacs)

## cachyos
*[CachyOS - August 24, 2025](https://cachyos.org/download/)*

### cachyos installation
1. `liveuser\Desktop Session: Plasma`
2. switch to **Wayland**
3. login without password
4. `CachyOS Installer\Partitions\Erase disk`
5. select **ext4**
6. `CachyOS Installer\All done`
7. deselect **Restart now**
8. click **Done**
9. restart

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
    `sudo pacman -S cachyos-gaming-meta`\
    `sudo pacman -S cachyos-gaming-applications`

### [flatpak](https://flatpak.org/setup/)
1. open **Konsole** *(Ctrl+Alt+T)*
2. `sudo pacman -S flatpak`
3. `flatpak --version`
4. `shutdown -r now`

	- option to add flathub\
		`flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo`

### multimedia codecs
[built-in](https://itsfoss.gitlab.io/post/how-to-install-ffmpeg-in-linux/)\
`ffmpeg -version`

### ppd
[built-in](https://gitlab.freedesktop.org/upower/power-profiles-daemon#power-profiles-daemon/)\
`pwerprofilesctl list`
	
###fastfetch
[built-in](https://github.com/fastfetch-cli/fastfetch)\
`fastfetch`

## archlinux												//archlinux - November 01, 2025
//
$ pacman -Syu												//system update
$ pacman-key --populate										//update database
$ sudo pacman -S archlinux-keyring
	y

$ pacman -S archinstall
	y

$ archinstall
	Disk configuration\Partitioning
		Use a best-effort default partition layout
		space bar											//space bar or tab
		btrfs												//Filesystem
			No
			Use compression

	Swap
		Yes													//zram

		// option to Bootloader
		//
		systemd-boot										//asus

	Authentication
		Root password
		User account
			Add a user
				Should "username" be a superuser (sudo)?
					Yes

			Confirm and exit

	Profile
		Type
			Desktop											//choose desktop environment

		Graphics Driver
			All open-source

			// option to setup audio
			Audio
				pipeuire									//audio server

	Network configuration
		Use NetworkManager

	Additional Packages
		firefox flatpak fastfetch

	Timezone
	Install
		Yes

	chroot into installation for post-installation configurations
		No

	$ shutdown -h now

	//
	// run
	//
	virtualbox manager\Storage\Controller: IDE
		click "IDE Primary Device 0:"
		select "Remove Disk From Virtual Drive"

	click "Start"

	//
	// system update
	//
	open konsole											//Ctrl+Alt+T
		$ sudo pacman -Syyu

	//
	// flatpak
	//
	https://flatpak.org/setup/
	$ sudo pacman -Syu
	$ sudo pacman -S flatpak
	$ flatpak --version
	$ shutdown -r now

		//option to add flathub
		//
		$ flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

	//
	// multimedia codecs
	//
	https://itsfoss.gitlab.io/post/how-to-install-ffmpeg-in-linux/
	$ ffmpeg -version										//built-in
		
	//
	// ppd													//power-profiles-daemon
	//
	https://linuxconfig.org/how-to-manage-power-profiles-over-d-bus-with-power-profiles-daemon-on-linux
	https://gitlab.freedesktop.org/upower/power-profiles-daemon#power-profiles-daemon
	open konsole											//Ctrl+Alt+T
		$ sudo pacman -S power-profiles-daemon
		$ sudo systemctl enable --now power-profiles-daemon.service
		$ powerprofilesctl list
		$ shutdown -r now

	//
	// fastfetch
	//
	https://github.com/fastfetch-cli/fastfetch
	$ pacman -S fastfetch
	$ fastfetch

//
// eos														//EndeavourOS
//
  Select "Start the Installer"
  Select "Online"
  
  	// installer settings with 1) Plasma KDE 2) Xfce4
  		/Erase disk
  		Select "Swap to file"		//for lower RAM usage

  // virtualbox settings
	$ VBoxService --version		//check guest additions version
  	$ sudo gpasswd -a user{$username} vboxsf
	$ shutdown -r now
	
	// shared folder directory in Plasma
		/Devices/endeavouros/media/sf_vboxsf
		
  // endeavouros update
  // https://endeavouros.com		//endeavouros
  // artemis - June 25, 2022
  //
    	// disable sleep in Plasma
		/System Settings/Workspace/Workspace Behavior/Screen Locking
		/System Settings/Hardware/Power Management/Energy Saving
		
	// welcome
	Select "Update Mirrors"				//After Install
	Select "Update System"				//After Install
	Select "Package cleanup configuration"		//After Install
	
	// konsole		//terminal
		$ sudo pacman -Syu
						
	// pamac configuration
	// https://wiki.manjaro.org/index.php/Pamac
	//
		// configuration
			$ yay
			$ yay -S pamac-aur
				n		//remove
				n		//diffs to show
				y		//remove dependencies
				y		//proceed
				
		// update
			$ pamac checkupdates -a
			$ pamac upgrade -a
			$ pamac clean
					--keep 3	//cleaning the cache except for the latest 3	
	
	// third party codecs
 	// https://linuxconfig.org/how-to-install-third-party-codecs-extras-on-manjaro-linux
 	//
  		$ sudo pacman -S a52dec faac faad2 flac jasper lame libdca libdv libmad libmpeg2 \
  		libtheora libvorbis libxv opus wavpack x264 xvidcore


https://youtu.be/QItrmchEQWE								//CERN ROOT Tutorial 2: Installing ROOT
https://youtu.be/Lxb4WZyKeCE								//Geant4 Tutorial 1: Installation and Testing of Geant4
  // root installation
  // https://root.cern		//ROOT: analyzing petabytes of data, scientifically.
  //
  	// root dependencies
	// https://root.cern/install/dependencies/	//Dependencies
	//
		$ sudo pacman -S --needed base-devel
		$ sudo pacman -S git vim
		$ sudo pacman -S git make cmake gcc binutils libx11 libxpm libxft libxext python openssl
		$ sudo pacman -S gcc-fortran pcre mesa glu glew ftgl mysql fftw cfitsio graphviz \
		  util-linux-libs avahi openldap python3 libxml2 gsl readline qt5-webengine
		  	1		//default
			y		//proceed

	// download and unpack source file
	// https://root.cern/install/all_releases/	//Releases
	// 6.24/06 - September 3, 2021
	//
		$ mv /home/user{$username}/Downloads/root{$root_version}.source.tar.gz ~
		$ tar -xzvf root{$root_version}.source.tar.gz

	// compile and install
		$ cd root{$root_version}
		$ cd build
		$ cmake -Dxrootd=OFF -Dbuiltin_xrootd=OFF -Druntime_cxxmodules=OFF ../
		$ lscpu
			N = the number of central processing unit;
		$ make -jN
		$ sudo make install -jN

	// setup scripts
		$ cd ~
		$ cd /usr/local/bin
		$ source thisroot.sh

	// run
		$ root
			-l	//without logo
		$ new TBrowser
		$ .q

  // geant4 installation
  // https://geant4.web.cern.ch		//GEANT4: A SIMULATION TOOLKIT
  //
	// geant4 prerequisites
	// https://geant4-userdoc.web.cern.ch/UsersGuides/InstallationGuide/html/gettingstarted.html
	// https://doc.qt.io/qt-5/linux.html
	//
		$ sudo pacman -S cmake gcc expat libxmu openmotif mesa qt5-base

	// download and unpack source file
	// https://geant4.web.cern.ch/support/download
	// 10.7/patch-04 - September 9, 2022
	//
		$ mv /home/user{$username}/Downloads/geant{geant4_version}.tar.gz ~
		$ tar -xvf geant{geant4_version}.tar.gz

	// compile and install
		$ cd geant{geant4_version}
		$ mkdir build
		$ cd build
		$ cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_QT=ON ../
		$ make -jN
		$ sudo make install -jN

	// setup scripts
		$ cd ~
		$ cd /usr/local/bin
		$ . geant4.sh

	// run Example B1
		$ cd geant{geant4_version}
		$ cd examples/basic/B1
		$ mkdir build
		$ cd build
		$ cmake ..
		$ make -jN
		$ ./exampleB1
		$ run/beamOn 100
		$ exit

		// batch mode
			$ cd geant{geant4_version}
			$ cd examples/basic/B1/build
			$ vim batch.mac
				i
			  	add
			  		/run/beamOn 1000
			  	esc
			  	:x or :wq
			$ ./exampleB1 batchmac
			$ exit
			
  // creating a permanent environment variables in bash
  // https://devconnected.com/set-environment-variable-bash-how-to	//how to set env in bash
  	$ sudo nano /home/user{$username}/.bashrc
		add in the last line
			source /usr/local/bin/thisroot.sh
			source /usr/local/bin/geant4.sh
		Ctrl+o
		enter
		Ctrl+x

  // vim
  	$ vi .vimrc
		i
	  	add
			set number
	 	esc
	  	:x

//....oooOO0OOooo........oooOO0OOooo........oooOO0OOooo........oooOO0OOooo......

  // option of i3 window manager
  https://youtu.be/j1I63wGcvU4		//i3wm: Jump Start
  
  // option of xset				//xorg
  	$ sudo pacman -S xorg-xset
  	$ xset
		noblank			//disable blank
		s off			//disable sleep
		s 3600 3600		//change blank time to 1 hrs
		-dpms			//turn off dpms
		s off -dpms		//disable dpms
		dpms force off		//turn off screen immediately
		dpms force standby	//standby
		dpms force suspend	//suspend
		q			//query the current settings
  
  // option of disable energy saving		//gnome
  	$ sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
  
  // option of pamac configuration		//outdated
  // https://wiki.manjaro.org/index.php/Pamac
  //
  	$ yay
	$ yay pamac-all
		1		//lst option
		1		//default
		n		//remove
		n		//diffs to show
  		y		//proceed

  // option of pamac from the chaotic-aur
	// https://itsfoss.com/install-pamac-arch-linux
	//
		$ sudo pacman-key --recv-key FBA220DFC880C036 --keyserver keyserver.ubuntu.com
		$ sudo pacman-key --lsign-key FBA220DFC880C036
		$ sudo pacman -U 'https://cdn-mirror.chaotic.cx/chaotic-aur/chaotic-keyring.pkg.tar.zst'\
		  'https://cdn-mirror.chaotic.cx/chaotic-aur/chaotic-mirrorlist.pkg.tar.zst'
		$ sudo nano /etc/pacman.conf
			Ctrl+o
		  	enter
		  	Ctrl+x
			
		$ sudo pacman -Syu pamac-aur
		
  // option of latest releases of root
  	// 6.26/06 - July 29, 2022
	//
  	// compile and install
		$ cmake ..
		
	// run
		$ root
			-l			//without logo
			--web=off		//revert to TBrowser
		$ new TBrowser			//RBrowser 
		      TRootBrowser		//TBrowser
		$ .q
		
  // option of latest releases of geant4
  	// 11.0.p03 - December 10, 202
	//
	// compile and install
		$ cmake ..

//....oooOO0OOooo........oooOO0OOooo........oooOO0OOooo........oooOO0OOooo......
## optional
- option to install virtualbox **Guest Additions**
>cachyos built-in

1. `menu bar\Devices\Insert Guest Additions`
2. copy and paste all files in **VBox_GAs_{VBoxClient_version}.iso** to **Documents**
3. right-click
4. **Open in Konsole**
5. `ls -lh`
6. `chmod 777 VBoxLinuxAdditions.run`
7. `sudo ./VBoxLinuxAdditions.run`

- option to [spotify](https://itsfoss.com/install-spotify-arch/)
	1. open **Konsole** *(Ctrl+Alt+T)*
	2. `sudo pacman -Syu spotify-launcher`

	- option to [flatpak](https://linuxways.net/arch/install-spotify-arch-linux/)
   		1. `flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo`
      	2. `flatpak install spotify`

- option to [steam](https://wiki.cachyos.org/configuration/gaming/)
	`sudo pacman -Syu steam`

- option to [yay](https://itsfoss.com/install-yay-arch-linux/)
	1. `sudo pacman -Syu`
	2. `sudo pacman -S --needed base-devel git`
	3. `git clone https://aur.archlinux.org/yay.git`
	4. `cd yay`
	5. `makepkg -si`
	6. `yay --version`

- option to [multimedia codecs](https://itsfoss.gitlab.io/post/how-to-install-ffmpeg-in-linux/)
	1. open **Konsole** *(Ctrl+Alt+T)*
	2. `sudo pacman -Syu`
	3. `sudo pacman -S ffmpeg`
	4. `ffmpeg -version`

// option to asus
//
https://asus-linux.org/
open konsole												//Ctrl+Alt+T
	$ pacman -S linux-firmware amd-ucode					//intel-ucode for intel
	$ pacman-key --recv-keys 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35	//g14 repo
	$ pacman-key --finger 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
	$ pacman-key --lsign-key 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
	$ pacman-key --finger 8F654886F17D497FEFE3DB448B15A6B0E9A3FA35
	$ pacman -Syu											//system update

		//
		// asusctl
		//
		$ pacman -S asusctl power-profiles-daemon
		$ systemctl enable --now power-profiles-daemon.service

		//
		// supergfxctl
		//
		$ pacman -S supergfxctl
		$ systemctl enable --now supergfxd

		//
		// rog control center
		//
		$ pacman -S rog-control-center

		//
		// custom kernel									//dirvers fixes
		//
		$ pacman -Syu linux-g14 linux-g14-headers

			//option to grub
			$ grub-mkconfig -o /boot/grub/grub.cfg

		//
		// nvidia
		//
		$ cat /proc/driver/nvidia/gpus/bus_address/power	//query status
		$ pacman -S nvidia-utils vulkan-icd-loader

			//option to enable
			//
			$ systemctl enable nvidia-suspend.service nvidia-hibernate.service nvidia-resume.service
			$ systemctl enable --now nvidia-powerd

//option to tuned
//
https://www.youtube.com/watch?v=WTJw21XQjCc
open konsole												//Ctrl+Alt+T
	$ yay -S tuned-git
		n													//cleanBuild
		n													//diffs
		y

	$ sudo systemctl enable --now tuned
	$ tuned-adm active
	$ sudo systemctl status tuned

// option to tlp
//
https://wiki.archlinux.org/title/CPU_frequency_scaling
https://linrunner.de/tlp/installation/index.html
open konsole												//Ctrl+Alt+T
	$ sudo pacman -S tlp tlp-rdw							//installation
	$ systemctl enable tlp.service							//enable service
	$ systemctl enable NetworkManager-dispatcher.service	//radio device wizard (tlp-rdw)
	$ systemctl mask systemd-rfkill.service systemd-rfkill.socket	//mask
	$ sudo tlp start
	$ tlp-stat -s



//....oooOO0OOooo........oooOO0OOooo........oooOO0OOooo........oooOO0OOooo......
