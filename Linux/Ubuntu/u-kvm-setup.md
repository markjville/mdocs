# Setup KVM/Qemu on Ubuntu

1. Verify CPU supports:

`egrep -c ‘(svm|vmx)’ /proc/cpuinfo`

2. Install:

`sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager`


3. Add user account to users of libvirt:

`sudo adduser [username] libvirt`

4. Verify install:

`virsh -c qemu:///system list`
