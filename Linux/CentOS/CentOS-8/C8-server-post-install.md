# CentOS 8 server post install

## 1. Update the system, change to admin user.
  
## 2. Assign static IP on CentOS 8:

Edit the file /etc/sysconfig/network-scripts/ifcfg-eno1 to modify/add:

```
BOOTPROTO="static"
IPADDR="10.10.x.x"
NETMASK="255.255.255.0"
GATEWAY="10.10.1.1"
DNS1="10.10.1.x"
```

Change the IPs above as your network requires.

Restart networking stack: 

`sudo systemctl restart NetworkManager.service`

## 3. Enable ssh:

	- Install following, if not already installed: # dnf install openssh-server
  
Start thesshd daemon and set to start after reboot:
```
systemctl start sshd
systemctl enable sshd
```

Edit file: `/etc/ssh/sshd_config`
- Uncomment line: `Port 22`
- Add or uncomment line: `PermitRootLogin yes`
- Restart ssh server: `service sshd restart`

## 4. Change hostname:
- Run cmd: `hostnamectl set-hostname newname`
- Reboot server. Restarting network will not reflect hostname changes fully.
	
## 5. Install EPEL & ClamAV: 

```
dnf -y install epel-release
install clamav clamav-update
```

Edit to clamav config:

`vi /etc/freshclam.conf`

Line 8: comment out if it enabled

`# Example`

Update Clam signatures and modify SE Linux to allow Clam to do its job:

```
freshclam
setsebool -P antivirus_can_scan_system 1
setsebool -P clamd_use_jit 1
```

Next, you have to verify the changes to SE Linux policies:

`getsebool -a | grep antivirus`

You should get this result:

```
antivirus_can_scan_system --&gt; on
antivirus_use_jit --&gt; off
```

## 6. Install GUI with tools:

`dnf groupinstall workstation`

Enable GUI to start at reboot:

`systemctl set-default graphical.target`

Startup GUI now:

`systemctl isolate graphical`

## 7. Reboot:

`reboot`
