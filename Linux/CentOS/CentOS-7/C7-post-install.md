# CentOS 7 server post install

1. Assign static IP on CentOS 7, edit the file /etc/sysconfig/network-scripts/ifcfg-eno1 to modify/add:

```
BOOTPROTO="static"
IPADDR="10.170.x.x"
NETMASK="255.255.255.0"
GATEWAY="10.170.1.31"
DNS1="10.170.1.48"
```

Restart networking stack: service network restart.

2. Enable ssh:
	- Install following, if not already installed: openssh openssh-server openssh-clients openssl-libs
	- Edit file: `/etc/ssh/sshd_config`
	- Uncomment line: `Port 22`
	- Add or uncomment line: `PermitRootLogin yes`
	- Restart ssh server: `service sshd restart`

3. Change hostname:
	- Run cmd: `hostnamectl set-hostname newname`
	- Reboot server. Restarting network will not reflect hostname changes fully.
	- Update the DNS servers if needed.

4. Install ClamAV: see separate document [Installing ClamAV on CentOS 7](./C7-install-ClamAV.md)

5. Install GUI with tools:
`yum groupinstall "GNOME Desktop" "Graphical Administration Tools"`

6. Make GUI start at startup:
`ln -sf /lib/systemd/system/runlevel5.target /etc/systemd/system/default.target`

7. Reboot:
`reboot`

8. Install KVM/Qemu
	-Check that the CPU supports this, looking for flags VMX or SVM:
		# egrep '(vmx|svm)' /proc/cpuinfo
	-Install the packages:
