# **arch on macOS setup guide**
UNLV\
the new version is available on [GitHub](https://github.com/hanc4-git?tab=repositories).

## installation video
[FINALLY! Linux on the Macbook M1 (bare-metal)](https://youtu.be/voMvctJ4GZ0)

## asahi linux installation
download [asahi linux with a Plasma KDE](https://asahilinux.org/)

## installation
1. open **Terminal**\
`curl https://alx.sh | sh`
	**n**: expert mode\
	**r**: resize\
	**80 gb**: new size\
	**y**: continue\
	**f**: install\
	**1**: asahi linux desktop\
	**max**: new OS size
3. hold down **Power** button to restart
4. select **Asahi Linux**\
	**y**: custom boot object

## optional
- option to install utm\
[Ubuntu Install on M1 MacBook Air - Virtualization and Benchmarking!](https://youtu.be/hnwK-nkXolc)

- option to [UTM Virtual Machines](https://apps.apple.com/us/app/utm-virtual-machines/id1538878817?mt=12) setup
1. select **Create a New Virtual Machine** settings
2. `Information\Style`
3. set **Operating System**
4. `System\Architecture`
5. set **ARM64 (aarch64)**
6. set **Base Memory**
7. `Drivers\Interface\New Drive`
8. select **NVMe**
9. select **USB**
>Removable
