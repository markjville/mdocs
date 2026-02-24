# Qemu with UEFI support

Source: https://www.server-world.info/en/note?os=CentOS_7&p=kvm&f=11

Issues: When Libvirt refuses to boot a VM, complaining that no bootable device is found (code: 0009). This affects servers that boot with UEFI, Libvirt must have UEFI support to function properly.

## 1.	Install OVMF (Open Virtual Machine Firmware).

`vi /etc/yum.repos.d/kraxel.repo`
# create new entry

```
[qemu-firmware-jenkins]
name=firmware for qemu, built by jenkins, fresh from git repos
baseurl=https://www.kraxel.org/repos/jenkins/
enabled=0
gpgcheck=0
[root@dlp ~]#
yum --enablerepo=qemu-firmware-jenkins -y install OVMF
[root@dlp ~]#
vi /etc/libvirt/qemu.conf
# line 682: add

nvram = [
    "/usr/share/edk2.git/ovmf-x64/OVMF_CODE-pure-efi.fd:/usr/share/edk2.git/ovmf-x64/OVMF_VARS-pure-efi.fd",
]

[root@dlp ~]#
systemctl restart libvirtd
```

## 2.	Check current version and update QEMU.

```
`/usr/libexec/qemu-kvm -version

QEMU emulator version 1.5.3 (qemu-kvm-1.5.3-141.el7_4.6), Copyright (c) 2003-2008 Fabrice Bellard
```

Install the latest:
`yum -y install centos-release-qemu-ev`

It is recommended to disable at this step:

`sed -i -e "s/enabled=1/enabled=0/g" /etc/yum.repos.d/CentOS-QEMU-EV.repo`

For this installion, qemu-kvm package is replaced to qemu-kvm-ev package

`yum --enablerepo=centos-qemu-ev -y install qemu-kvm-ev`

Restart libvirtd

`systemctl restart libvirtd`

Verify the new version

```
/usr/libexec/qemu-kvm -version

QEMU emulator version 2.9.0(qemu-kvm-ev-2.9.0-16.el7_4.13.1)
Copyright (c) 2003-2017 Fabrice Bellard and the QEMU Project developers
```

## 3 Create a VM to install Windows Server 2016 as an example.

Specify for [--boot] with [uefi] like follows. For other items, specify anything you like.

```
virt-install \
--name Win2k16 \
--ram 8192 \
--disk path=/var/kvm/images/Win2k16.img,size=80 \
--vcpus=4 \
--os-type windows \
--os-variant=win10 \
--network bridge=br0 \
--graphics spice,listen=0.0.0.0,password=password,keymap=ja \
--video qxl \
--cdrom /tmp/Win2016_JA-JP.ISO \
--boot uefi
```
