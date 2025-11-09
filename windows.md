# **ubuntu on windows 10 subsystem setup guide**
UNLV\
the new version is available on [GitHub](https://github.com/hanc4-git?tab=repositories).

## installation video
[How to Install Ubuntu on Windows 10 (WSL)](https://youtu.be/X-DHaQLrBi8)\
[Xeyes or Xclock : Error: Can't open display](https://youtu.be/4Z4b1w6YDO4)

## windows 10 settings
1. find *Settings* in search box on task bar
2. `Settings\Update & Security\For developers`
3. turn on **Developer Mode**
4. find *Control Panel* in search box
5. `Control Panel\Programs\Turn Windows features on or off`
6. select **Windows Subsystem for Linux**
7. restart

## ubuntu installation
*Ubuntu 20.04 LTS - April 23, 2020*
1. find *Microsoft Store* in search box
2. search *ubuntu*
3. get and launch **Ubuntu 20.04 LTS**
4. create *username* and *password*

## xming for GUI
1. download [Xming X Server for Windows](https://sourceforge.net/projects/xming	)
2. install and launch **Xming**
3. open **Terminal**
```
sudo systemd-machine-id-setup
sudo dbus-uuidgen — ensure
cat /etc/machine-id
sudo apt -y install x11-apps xfonts-base xfonts-100dpi xfonts-75dpi xfonts-cyrillic
```

## run xeyes
```
nano ~/.bashrc
add
export DISPLAY=localhost:0.0
Ctrl+x
xeyes
```

## optional
- option to convert MBR to GPT
  1. boot with **Windows Installation Media**
  2. open **Command Prompt** *(Shift+F10)*
  ```
  diskpart
  list disk
  select disk 0
  ```
  > select the disk want to convert
  
  `clean`
  > format

  ```
  convert gpt
  exit
  ```
  > exit to leave diskpart

  `exit`
  > close command prompt

- option to partition 1tb\
  *personal setup*\
  `c:\` *411000*\
  `d:\` *463000*

- option to install **Vim**\
  *[gVim 9.1.1825 - October 27, 2025](https://www.vim.org/download.php)*\
  [How to Install VIM on Windows 11 (Non WSL Way)](https://youtu.be/1LdQMhFhaxs)
