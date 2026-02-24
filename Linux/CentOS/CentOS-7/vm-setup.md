# VM setup on QEMU/KVM:

## 1. If VM is on NFS mount, one must tell SELinux to allow this or it will block installation.

`setsebool -P virt_use_nfs 1`

## 2. New VM:

- choose iso, RAM, CPU, etc...

## 3. Storage

- Select of create custom storage, click Manage
- Navigate to desired storage location, click "+" to add volume
- Add title to the .qcow disk volume

## 4. Boot VM to begin installation of OS

## 5. Install updates

## 6. Change hostname to appropriate hostname:

`hostnamectl set-hostname newname`

## 7. Set static IP address:
- edit `/etc/sysconfig/network-scripts/ifcfg-xxxx` (typically eth0), adding:
- 
  ```
		-BOOTPROTO=static
		-IPADDR="10.10.1.xxx" (desired IP)
		-NETMASK="255.255.255.0"
		-GATEWAY="10.10.1.1"
		-DNS1="10.10.1.x"
		-ONBOOT=yes
  ```
  
## 8. Restart networking service:

`sudo systemctl restart network.service`

# Networking on physical host:

## 1. In VMM, Edit/Connection details

## 2. Virtual Networks tab: 

```
Name: "default"
Device: virbr0
Autostart: On Boot
IPv4 configuration
	Network: default (192.168.1.0/24)
	DHCP range: default (192.168.1.2 - 192.168.1.254)
	Forwarding: NAT
```

## 3. Network Interfaces

```
create "br(x)"
State: Active
Start Mode: onboot
IPv4 configuration:
  Static
	10.10.1.xxx/24
```
