# CentOS 7 server post install

## 1. Assign static IP on CentOS 7, edit the file /etc/sysconfig/network-scripts/ifcfg-eno1 to modify/add:

```
BOOTPROTO="static"
IPADDR="10.x.x.x"
NETMASK="255.255.255.0"
GATEWAY="10.x.x.x"
DNS1="10.x.x.x"
```

Restart networking stack: service network restart.

## 2. Enable ssh:
	- Install following, if not already installed: openssh openssh-server openssh-clients openssl-libs
	- Edit file: `/etc/ssh/sshd_config`
	- Uncomment line: `Port 22`
	- Add or uncomment line: `PermitRootLogin yes`
	- Restart ssh server: `service sshd restart`

## 3. Change hostname:
	- Run cmd: `hostnamectl set-hostname newname`
	- Reboot server. Restarting network will not reflect hostname changes fully.
	- Update the DNS servers if needed.

## 4. Install ClamAV: see separate document [Installing ClamAV on CentOS 7](./C7-install-ClamAV.md)

## 5. Install GUI with tools:
`yum groupinstall "GNOME Desktop" "Graphical Administration Tools"`

## 6. Make GUI start at startup:
`ln -sf /lib/systemd/system/runlevel5.target /etc/systemd/system/default.target`

## 7. Reboot:
`reboot`

## 8. Install KVM/Qemu

- Check that the CPU supports this, looking for flags VMX or SVM:
`# egrep '(vmx|svm)' /proc/cpuinfo`

- Install the packages:
`yum install -y qemu-kvm qemu-img virt-manager libvirt libvirt-python libvirt-client virt-install virt-viewer`

- Add a bridge interface:
`sudo echo "net.ipv4.ip_forward = 1" | sudo tee /etc/sysctl.d/99-ipforward.conf`

- Check that the change is good:
`sudo sysctl -p /etc/sysctl.d/99-ipforward.conf`

- Assign an interface to be the bridge:
`sudo vi /etc/sysconfig/network-scripts/[interface name]`

- Add the following to the end of the file:
`BRIDGE=brid0`

-Create a bridge interface file:
`sudo vi /etc/sysconfig/network-scripts/ifcfg-brid0`

-Inside this file we add:
```
DEVICE="brid0"
TYPE=BRIDGE		
ONBOOT=yes
BOOTPROTO=static
IPADDR="10.x.x.x" (fill in the blanks)
NETMASK="255.255.255.0"
GATEWAY="10.x.x.x"
DNS="10.x.x.x"
DNS="10.x.x.x"
```

-reboot the server

## 9. (Optional) Install NFTS support by fetching the EPEL repo package: 
`wget http://dl.fedoraproject.org/pub/epel/epel-release-latest-	7.noarch.rpm`

- Enable the repo: rpm -ivh epel-release-latest-7.noarch.rpm
- Verify repo is active: yum repolist
- Install nfts-3g: yum install ntfs-3g fuse
