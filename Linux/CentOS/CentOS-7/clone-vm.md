# Clone a VM in Qemu

1. Pause or shutdown VM.
2. Clone VM
3. While original is still paused, boot up clone.
4. Change: hostname, static IP, delete ssh-keys
-  Hostname: `hostnamectl set-hostname newhostname`
- Static IP : Edit the file `/etc/sysconfig/network-scripts/ifcfg-xxxxx`
- SSH keys: `/bin/rm -v /etc/ssh/ssh_host_*`  then  `ssh-keygen`
