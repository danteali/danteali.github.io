---
Created:  '2021-08-15 10:05:57 +01:00'
Modified: '2021-08-15 10:05:57 +01:00'
---

| Tags: #linux #virtual-machine #ubuntu #kali |
| ----- |

---

# Virtual Machine - Linux
   
Generally using VirtualBox for VMs, including replication of NAS environment to test things before intro to production.

Below is a sample of notes which have come in handy when setting up VMs.

## Installing
For Kali, see: https://www.kali.org/docs/virtualization/install-virtualbox-guest-vm/


## VirtualBox Guest Additions - shared clipboard/folders/etc

>Note that in Kali, you can install VB Guest Additions from command line without the virtual CD function, see [here](https://www.kali.org/docs/virtualization/install-virtualbox-guest-additions/). 
>We're going to search the package manager for the guest additions package first to confirm the package name.
>Note that the `--reinstall` is important as we want to make sure we're not leaving anything pre-existing installed.
Run:
>```bash
sudo apt update
sudo apt-cache search virtualbox-guest
sudo apt install -y --reinstall virtualbox-guest-x11
sudo shutdown -r now
>```


Inside VM go to `Devices menu -> Insert Guest Additions CD image menu`

Use the following command to mount the CD

```bash
sudo mount /dev/cdrom /media/cdrom
```

Install dependencies for VirtualBox guest additions:

```bash
sudo apt-get update
sudo apt-get install build-essential linux-headers-`uname -r`
```

Run installation script for the guest additions:
```bash
sudo /media/cdrom/./VBoxLinuxAdditions.run
```
>If you get a `permission denied` error when running the executable (even when running as root) it may be due to a security setting to prevent the direct execution of binaries on the mounted CD...
><br>
From [source](https://forums.virtualbox.org/viewtopic.php?f=3&t=58799):
...the filesystem is mounted with the noexec option, so the execute permission bits on all files are ignored, and you cannot directly execute any program residing on this filesystem. Note that the noexec mount option is implied by the user option in `/etc/fstab`. ... If you use user and want to have executable files, use user,exec.  
<br>
 To fix, either run mount command with exec option:
Or edit `/etc/fstab` to change
>```bash
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0
>```
To
>```bash
/dev/sr0        /media/cdrom0   udf,iso9660 user,exec     0       0
>```

Reboot
```bash
sudo shutdown -r now
```


## To get keyboard capture working properly

Reboot after first boot worked for me. Below should work otherwise.

Select keyboard from Menu Option initially to allow typing.

Install dependencies:

```bash
sudo apt-get install scim-bridge-client-qt scim-bridge-client-qt4 scim-bridge-client-gtk
```

## Shared folders with Windows host
1. Install guest additions per above note
2. Open VirtualBox
3. Right-click your VM, then click Settings
4. Go to Shared Folders section
5. Add a new shared folder
6. On Add Share prompt, select the Folder Path in your host that you want to be accessible inside your VM.
7. In the Folder Name field, type shared
8. Uncheck Read-only and Auto-mount, and check Make Permanent
9. Start your VM

## Panel Restart
In Kali 2021, using xfce4 (for the first time), the panel (taskbar) can disappear after a lock/unlock. 

To restart the panel, run:
```bash
nohup xfce4-panel &
```


## Give user root permissions (not recommended for production systems)

To give the user "foo" unlimited passwordless access to root privileges via the sudo command, edit `/etc/sudoers` by running `sudo visudo` and add the line:

```bash
foo ALL = NOPASSWD: ALL
```

## Enable root login (not recommended for production systems)

[Source](http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html)

Suggest only doing this for initial set up to save time. Also check notes on SSH auto-login.

```bash
sudo passwd root
```

Edit SSH config
```bash
nano /etc/ssh/sshd_config
```

and add/uncomment the following line:
```bash
PermitRootLogin yes
```

Can now log in via ssh with username root & password you set up above. 

Once config complete, edit ssh config again and also disable root log in with:

```bash
passwd -l root
```

While here, disable the ‘waiting for network config’ message on startup when LAN unplugged:
```bash
nano /etc/init/failsafe.conf
```

Change the sleep values to 10 and this will cause it to wait for only 10 secs.