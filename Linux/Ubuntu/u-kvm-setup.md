# Setup KVM/Qemu on Ubuntu

1. Verify CPU supports:
2. 
`egrep -c ‘(svm|vmx)’ /proc/cpuinfo`

3. Install:
4. 
`sudo apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils virt-manager`


5. Add user account to users of libvirt:
6. 
`sudo adduser [username] libvirt`

7. Verify install:
8. 
`virsh -c qemu:///system list`
