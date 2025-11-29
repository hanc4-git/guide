# **dual-boot linux and windows guide**
UNLV\
the new version is available on [GitHub](https://github.com/hanc4-git?tab=repositories).

## guide
[How to Dual-Boot Windows 11 & Bazzite](https://youtu.be/KAt49B6rSFI)\
[Dual Boot Preliminary and Post-Installation Setup Guide](https://docs.bazzite.gg/General/Installation_Guide/dual_boot_setup_guide/)\
[How to Dual Boot CachyOS and Windows 11 (EASY WAY) // Install CachyOS](https://youtu.be/LC3ByQYz5Jw)

## prerequisites
1. find **Control Panel** in serch box on task bar
2. `Control Panel > Hardware and Sound > Power Options`
3. select **Choose what the power buttons do**
4. click **Change settings that are currently unavailable**
5. deselect **Turn on fast startup**
6. deselect **Hibernate**
7. Save changes

  - option to device encryption
    1. find **Settings** in serch box on task bar
    2. `Settings > Privacy & Security > Device Encryption`
    3. turn off **Device Encryption**
    > re-enable later if possible

  - option to disk partitioning
    1. *Win+X*
    2. click **Disk Management**
    3. right-click on disk
    4. choose **Shrink Volume**

## rufus
*[Rufus 4.11 - October 2, 2025](https://rufus.ie/en/)*
1. `drive properties > boot selection`
2. select **ISO Image**
3. `drive properties_partition scheme`
4. set **GPT**
5. start

  - option to *[Ventoy 1.1.07 - August 18, 2025](https://www.ventoy.net/en/index.html)*
      1. `Option > Partition Style`
      2. set **GPT**
      3. **Install**

## UEFI
1. find **Settings** in search box on task bar
2. `Settings > System > Recovery > Recovery options > Advanced startup`
3. restart
4. `Choose an option > Use a device`
5. select **UEFI:Removable device**
6. restart

  - option to use BIOS
  1. press *ESC, F2, or DEL* when the system starts
  2. choose **USB**
  
## installation
*install windows first*
1. start **INSTALLATION SUMMARY**
2. `INSTALLATION SUMMARY > SYSTEM > Installation Destination > Device Selection > Local Standard Disks`
3. select disk
4. **Done**

  - option to [Manual Partitioning](https://docs.bazzite.gg/General/Installation_Guide/manual_partitioning/)
    1. select **Something Else to Manually Set Up**
    2. select **Unallocated Space**
    3. **ext4**
    > Root Filesystem

## optional
- option to mouse acceleration
    1. find **Settings** in serch box on task bar
    2. `Settings > Bluetooth & devices > Mouse > Related settings > Additional mouse settings`
    3. `Mouse Properties > Pointer Options > Motion`
    4. deselct **Enhance pointer precision**

- option to battery percent
  	1.  open **Microsoft Store**
  	2.  install **Battery Percentage Icon**

- option to
    1. find **Command Prompt** in search box on task bar
    2. **Run as adminstrator**
    ```
    diskpart
    list disk
    select disk 0
    list partition
    ```
    
    `select partition 1`
    > EFI partition

    `assign letter=r`
    > assign temporary drive

    ```
    exit
    r:
    dir
    cd EFI
    dir
    rd os{$osname} /s
      y
    exit
    ```
