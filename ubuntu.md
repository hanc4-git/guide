# **ubuntu setup guide
UNLV\
the new version is available on [GitHub](https://github.com/hanc4-git?tab=repositories).

## linuxmint
*Linux Mint 22.2 - September 04, 2025*

### flatpak
[built-in](https://flatpak.org/setup/)\
`flatpak --version`

### multimedia codecs
1. `Install\Multimedia codecs`
2. select **Install multimedia codecs**

### ppd
[built-in](https://gitlab.freedesktop.org/upower/power-profiles-daemon#power-profiles-daemon/)\
`pwerprofilesctl list`

### [ppd applet](https://forums.linuxmint.com/viewtopic.php?t=423612)
1. `Applications\Preferences\Applets`
2. switch to **Download**
3. install **[Power Profiles by rcalixte](https://cinnamon-spices.linuxmint.com/applets/view/369)**
4. switch to **Manage**
5. click **+**
>add power profiles to panel
6. `System Settings\Preferences\General`
7. enable **Disable composition for full-screen windows**
>to prevent display tearing

### fastfetch
1. download **[fastfetch-linux-amd64.deb](https://github.com/fastfetch-cli/fastfetch)**
2. run
3. click **Install Package**
4. open **Terminal** *(Ctrl+Alt+T)*\
`fastfetch`

  - option to use **Terminal**\
	open **Terminal** *(Ctrl+Alt+T)*\
    `sudo apt install fastfetch-linux-amd64.deb` 

## ubuntu
*Ubuntu 22.04.3 LTS - August 10, 2023*

### ubuntu update
1. open **Ubuntu Software**
2. **System Update**

	- option to use terminal
		open **Terminal** *(Ctrl+Alt+T)*\
		`sudo apt -y update && sudo apt -y upgrade`\
		`sudo apt autoremove`

### [flatpak](https://flatpak.org/setup/)
open **Terminal** *(Ctrl+Alt+T)*\
`sudo apt install flatpak`\
`sudo apt install gnome-software-plugin-flatpak`\
`flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo`\
`flatpak --version`\
`sudo shutdown -r now`

### [multimedia codecs](https://www.linuxfordevices.com/tutorials/linux/installing-multimedia-codecs-linux)
open **Terminal** *(Ctrl+Alt+T)*\
`sudo add-apt-repository multiverse`\
`sudo apt update`\
`sudo apt install ubuntu-restricted-extras`

### [ppd](https://gitlab.freedesktop.org/upower/power-profiles-daemon#power-profiles-daemon)
1. open **Software Manager**
2. install **power-profiles-daemon**

	- option to use **[Terminal](https://linuxconfig.org/how-to-manage-power-profiles-over-d-bus-with-power-profiles-daemon-on-linux)**
		open **Terminal** *(Ctrl+Alt+T)*\
		`sudo apt install power-profiles-daemon`\
		`sudo systemctl enable power-profiles-daemon.service`
		>enable service

		`powerprofilesctl list`\
		`sudo shutdown -r now`

### [ppd applet](https://forums.linuxmint.com/viewtopic.php?t=423612)
1. `Applications\Preferences\Applets`
2. switch to **Download**
3. install **[Power Profiles by rcalixte](https://cinnamon-spices.linuxmint.com/applets/view/369)**
4. switch to **Manage**
5. click **+**
>add power profiles to panel
6. `System Settings\Preferences\General`
7. enable **Disable composition for full-screen windows**
>to prevent display tearing

### fastfetch
1. download **[fastfetch-linux-amd64.deb](https://github.com/fastfetch-cli/fastfetch)**
2. run
3. click **Install Package**
4. open **Terminal** *(Ctrl+Alt+T)*\
`fastfetch`

  - option to use **Terminal**
    1. open **Terminal** *(Ctrl+Alt+T)*\
    `sudo apt install fastfetch-linux-amd64.deb` 

## installation video
[Geant4 Tutorial 1: Installation and Testing of Geant4](https://www.youtube.com/watch?v=Lxb4WZyKeCE) ([kor](https://youtu.be/gVcbeLQEHNw))\
[CERN ROOT Tutorial 2: Installing ROOT](https://youtu.be/QItrmchEQWE) ([kor](https://youtu.be/J8iQVm0DLzY))

## [geant4](https://geant4.web.cern.ch)

### [geant4 prerequisites](https://geant4-userdoc.web.cern.ch/UsersGuides/InstallationGuide/html/gettingstarted.html)
`sudo apt-get install cmake gcc g++ libexpat1-dev libxmu-dev libmotif-dev libgl1-mesa-dev qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools`

### geant 4 installation
*[Geant4 10.7/patch-04 - September 9, 2022](https://geant4.web.cern.ch/support/download)*\
`mv /home/user($username}/Downloads/geant{geant4_version}.tar.gz ~`\
`tar -xvf geant{geant4_version}.tar.gz`\
`cd geant{geant4_version}`\
`mkdir build`\
`cd build`\
`cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DGEANT4_INSTALL_DATA=ON -DGEANT4_USE_QT=ON ../`\
`lscpu`\
`make -jN`
>N = Number of CPUs

`sudo make install -jN`

### environment variables settings
`cd ~`\
`cd /usr/local/bin`\
`. geant4.sh`

- option to [permanent environment variables settings](https://devconnected.com/set-environment-variable-bash-how-to)\
	`sudo nano /home/user{$username}/.bashrc`
	1. at the last line\
	*`source /usr/local/bin/thisroot.sh`*\
	*`source /usr/local/bin/geant4.sh`*
	2. *Ctrl+o*
	3. *enter*
	4. *Ctrl+x*

### run Example B1
`cd geant{geant4_version}`\
`cd examples/basic/B1`\
`mkdir build`\
`cd build`\
`cmake ..`\
`make`\
`./exampleB1`\
`run/beamOn 100`\
`exit`\

- option to batch mode\
	`cd geant{geant4_version}`\
	`cd examples/basic/B1/build`\
	`vim batch.mac`\
	*`i`*
  	>insert mode

	`/run/beamOn 100`\
  	*`ESC`*
  	>exit insert mode
     
   	*`:wq or :x or :ZZ`*
  	>write (save) and quit
   
	`./exampleB1 batchmac`\
	`exit`
	
## [root](https://root.cern)

### [root dependencies](https://root.cern/install/dependencies/)
`sudo apt install build-essential git vim`\
`sudo apt-get install dpkg-dev cmake g++ gcc binutils libx11-dev libxpm-dev libxft-dev libxext-dev 2to3 dh-python python-is-python3 libssl-dev`\
`sudo apt-get install gfortran libpcre3-dev libglu1-mesa-dev libglew-dev libftgl-dev libmysqlclient-dev libfftw3-dev libcfitsio-dev libgraphviz-dev libavahi-compat-libdnssd-dev libldap2-dev python2-dev:i386 python2:i386 python2-dev python2 python-dev-is-python3 libxml2-dev libkrb5-dev libgsl-dev qtwebengine5-dev`

### root installation
[ROOT 6.28/04 - May 7, 2023](https://root.cern/install/all_releases/)\
`mv /home/user{$username}/Downloads/root{$root_version}.source.tar.gz ~`\
`tar -xzvf root{$root_version}.source.tar.gz`\
`cd root{$root_version}`\
`cd build`\
`cmake -Dbuiltin_llvm=ON ../`\
`make -jN`\
`sudo make install -jN`

### environment variables settings
`cd ~`\
`cd /usr/local/bin`\
`source thisroot.sh`

### run
`root`\
	**-l**: without logo\
	**--web=off**: revert to TBrowser\
	**new TBrowser**: RBrowser\
	**TRootBrowser**: TBrowser\
`.q`

## optional
- option of old releases of root
[ROOT 6.18/04 - September 11, 2019
	//
  	// compile and install
		$ cmake -Dxrootd=OFF -Dbuiltin_xrootd=OFF -Druntime_cxxmodules=OFF ../
			-Dxrootd=OFF -Dmysql=OFF -Dkrb5=OFF -Dodbc=OFF -Doracle=OFF \
			-Dpgsql=OFF -Dqt=OFF \
			-Dpython=ON -Dpython3=ON -Dpcre=ON -Dzlib=ON \
			-Dunuran=ON -Dexplicitlink=ON -Dminuit2=ON -Droofit=ON \
			-Dfftw3=ON -Dgsl=ON -DOpenGL_GL_PREFERENCE=GLVND		//cmake flags
		
	// run
		$ root
			-l	//without logo
		$ new TBrowser
		$ .q
		
  // option of latest releases of geant4
  	// 11.0.p03 - December 10, 202
	//
	// compile and install
		$ cmake ..

  // option of OpenGL		//geant4
  	// geant4 prerequisites
		$ sudo apt-get install libx11-dev libxpm-dev libxft-dev libxext-dev libglu1-mesa-dev

	// compile
		$ cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DGEANT4_INSTALL_DATA=ON \
		  -DGEANT4_USE_OPENGL_X11=ON ../

//....oooOO0OOooo........oooOO0OOooo........oooOO0OOooo........oooOO0OOooo......

// option to install "Virtualbox Guest Additions"
//
menu bar\Devices\Insert Guest Additions
	click "Run"

		//option to run
		//
		home\VBox_GAs_{VBoxClient_version}
		double-click VBoxLinuxAdditions.run

		//option to terminal
		//
		right-click VBoxLinuxAdditions.run
		"Run as a Program"
			$ VBoxService --version							//check guest additions version
			$ sudo gpasswd -a user{$username} vboxsf
			$ sudo shutdown -r now
			
disable sleep
	\Settings\Privacy\Screen\Blank Screen Delay
	\Settings\Privacy\Screen\Automatic Screen Lock
	
### multimedia codecs
https://www.linuxfordevices.com/tutorials/linux/installing-multimedia-codecs-linux
	install\multimedia codecs
		select "Install multimedia codecs"

		//
		// option to media codecs
		//
		$ sudo apt install ubuntu-restricted-extras
			tab												//move
			enter											//ok
			yes												//accept
    
// option to asus
//
https://asus-linux.org/

//option to tuned
//
https://www.funkyspacemonkey.com/tuned-allows-you-to-optimize-linux-system-performance
open terminal												//Ctrl+Alt+T
	$ sudo apt install tuned tuned-utils tuned-utils-systemtap
	$ sudo systemctl enable --now tuned
	$ tuned-adm active
	$ tuned-adm profiles

// option to tlp
//
https://linrunner.de/tlp/installation/index.html
open terminal												//Ctrl+Alt+T
	$ sudo add-apt-repository ppa:linrunner/tlp				//add tlp ppa
	$ sudo apt update
	$ sudo apt install tlp tlp-rdw							//isntallation
	$ sudo tlp start
	$ tlp-stat -s

		// option to remove
		$ apt remove power-profiles-daemon

		// option to version 1.5 only
		$ sudo systemctl enable tlp.service					//enable the service manually

// option to spotify
//
https://www.spotify.com/us/download/linux/

//....oooOO0OOooo........oooOO0OOooo........oooOO0OOooo........oooOO0OOooo......
