# **virtualbox setup guide**
UNLV\
the new version is available on GitHub.

## virtualbox settings
*[VirtualBox 7.2.4 - October 17, 2025](https://www.virtualbox.org)*

  - option\
	[Microsoft Visual C++ Redistributable latest supported downloads](https://learn.microsoft.com/en-US/cpp/windows/latest-supported-vc-redist?view=msvc-170)\
	[VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads)

## create vitual machine
1. `New\Virtual machine name and operationg system`
2. create *VM Name*
3. select **ISO Image**
4. select **OS** and **OS Distribution**
5. deselect **Proceed with Unattended Installation**
6. `New\Specify virtual hardware`
7. choose **Base Memory** and **Number of CPUs** in <span style="color:green;">green</span>
8. `New\Specify virtual hard disk`
9. choose **Disk Size**
10. Finish
11. `Settings\System\Display`
12. maximize **Video Memory**

	- option
		1. `Settings\General\Features\Shared Clipboard and Drag-and-Drop`
 		2. set **Bidirectional**
		3. `Settings\Shared Folders`
 		4. click **Add new shared folder**
  		5.	set **Folder Path**
   		6.	select **Auto-mount**
    	7.	OK 

## run
1. `Details\Storage\Controller: IDE`
2. click **IDE Secondary Device 0:**
3. select **Remove Disk From Virtual Drive**
4. click **Start**

## shared folders access
1. open **Terminal** *`Ctrl+Alt+T`*\
`sudo adduser user{$username} vboxsf`

## optional
- option to set up virtualbox 6.1
	1. `Settings\System`
 	2.	set **KVM**
	>Paravirtualization Interface

	3. `Settings\Display`
	4. set **Hyper-V**
	>for windows

- option to set up windows 11\
	*not recommended*\
	open **Command Prompt** *(Shift+F10)* as administrator\
	`bcdedit /set hypervisorlaunchtype off`
	>disable windows hypervisor

- option to enable hypervisor
	1. `bcdedit /set hypervisorlaunchtype auto`
	2. find *Settings* in search box on task bar
	3. `Settings\Privacy & Security\Windows Security\Device Security\Core Isolation Details
	4. disable **Memory Integrity**
	5. restart
