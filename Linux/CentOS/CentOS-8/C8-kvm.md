# Install KVM on CentOS 8

## 1. Check CPU spec for virtualization support:

`lscpu | grep Virtualization:'

It should show something like:

`Virtualization:      VT-x`

If there is no output, your cpu cannot support virtualization.

## 2. Install the needed packages:

`dnf install qemu-kvm qemu-img libvirt virt-install libvirt-client virt-manager -y`

## 3. Verify that the KVM module installed:

`lsmod | grep -i kvm`

## 4. Enable and Start libvirtd service

```
systemctl enable libvirtd
systemctl start libvirtd
```

## 5. Create a network bridge for VMs to host's NIC

To be continued: 

For further reading, see [https://www.linuxtechi.com/install-configure-kvm-on-rhel-8/](https://www.linuxtechi.com/install-configure-kvm-on-rhel-8/)

[https://computingforgeeks.com/how-to-install-kvm-on-rhel-8/](https://computingforgeeks.com/how-to-install-kvm-on-rhel-8/)
