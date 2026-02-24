# Resizing the root filesystem of a VM on CentOS 6

*Warning: this is missing some info after step 3. I will update soon, check back later.* 

Notes:
- This does not apply to CentOS 7. Please refer to similar document for CentOS 7.
- In the sample commands, I will use the case of dev3 (10.170.1.86, VM name dev3)
- The goal in this example is to increase the size of the "/" partition.
- VMM is Virtual Machine Manager, as a GUI for KVM/QEMU.

1. On command line, run pvs on the VM. Note the details of the name and size of the target partition for comparing after. Example output:
`PV VG Fmt Attr PSize PFree `
`/dev/vda2 centos lvm2 a-- <79g 0`

"/dev/vda2" is how filesystem is mounted within the VM.
"centos" is the label of the volume on the disk.
79g is current size: 27 GB, 0 MB free.

2. Note where the file system is located. If VM, open VMM, navigate to details of the VM specifically where the virtual disk is (typcally VirtIO Disk). If stored locally, the default is /var/lib/libvirt/images/"name-of-filesystem".img

3. Shutdown the VM:
`shutdown -P now`

4.  On the host, run
```
qemu-img info /var/lib/libvirt/images/"name-of-filesystem".img
image: /var/lib/libvirt/images/"name-of-filesystem".img
file format: qcow2
virtual size: 27G (27737418240 bytes)
disk size: 3.7G
cluster_size: 65536
Format specific information:
 compat: 1.1
 lazy refcounts: true
```

5. Expand the .qcow2 file:
`sudo qemu-img resize /var/lib/libvirt/images/"name-of-filesystem".qcow2 +15G`
`Image resized.`

The "+15G" parameter expands the qcow2 file by 15GB. Adjust this number accordingly.
6. Check the size of .qcow2 file to verify the expansion:
`qemu-img info /var/lib/libvirt/images/"name-of-filesystem".qcow2`

7. Although the drive is larger, the partitions on it are still the same size. To adjust the partition size of the VM's "/" partition, Download the GParted Live iso. mount it as a CD/optical drive within the VM in question on VMM. Either set the optical drive to be first boot option or enable boot menu at startup. Boot the VM from the virtual optical drive.

8. As GParted boots up, it will ask config questions, answers: English, start X.

9. First select /dev/vda2 (device names may vary) and select Resize/Move from the toolbar. The Resize / Move window will open. Drag the end of the partition to the right to regain the extra space. Click Apply, shut down the guest machine and remove the live CD from the drive as was done in step 7.

10. Startup the VM. Verify the changes in size of disk:
`pvs` (about the disk)
and
`vgs` (about the volume group)
and
`lvs` (about the logical volume)

Note that the size of the disk (qcow2) is bigger, but that the logical volume is still the old size.

11. To resize the volume, run:
`xfs_growfs /dev/centos/root`
Note: this is where I was stuck. I was using the resizefs cmd and the operation failed. It turns out that this cmd doesn't play with xfs filesystems, which is the default for CentOS 7.

12. If all went well, the output will return that volume size increased and it will show within VMM as well.

Reference: 
http://www.naturalborncoder.com/virtualization/2014/12/05/increasing-the-size-of-a-qcow2-image-under-kvm/
Resources: 
https://serverfault.com/questions/324281/how-do-you-increase-a-kvm-guests-disk-space
https://sandilands.info/sgordon/increasing-kvm-virtual-machine-disk-using-lvm-ext4
