# **dual-boot linux and windows guide**
UNLV\
the new version is available on [GitHub](https://github.com/hanc4-git?tab=repositories).

## prerequisites
1. find **Settings** in serch box on task bar
2. `Settings > Privacy & Security > Device Encryption`
3. turn off **Device Encryption**
> re-enable later if possible

4. find **Control Panel** in serch box on task bar
5. `Control Panel > Hardware and Sound > Power Options`
6. select **Choose what the power buttons do**
7. click **Change settings that are currently unavailable**
8. deselect **Turn on fast startup**
9. Save changes

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
1. start linux installation
2. select **Alongside Windows Boot Manager**

  - option to manually
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
