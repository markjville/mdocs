#Mount NFS drive in CentOS 7

1. Install the NFS tools:

`yum install nfs-utils`

2. Open port on the firewall for this:

`firewall-cmd --permanent --zone=public –add-service=nfs`

3. Test mounting the NFS share on system into "/mnt/nas-share"

`mount -t nfs -o nfsvers=3 192.168.x.x:/c/nas-share /mnt/nas-share`

4. If sucessful, add the following to the /etc/fstab:
`192.168.0.104:/c/nas-share /mnt/ns-share	nfs	vers=3	0	0`
