# Permanently mount NFS share on Ubuntu 18.04:

1. Install `nfs-common`

2. In /etc/fstab:
3. 
`192.168.0.x:/c/backup /mnt/NAS-backup nfs auto,noatime,nolock,bg,nfsvers=4,intr,tcp,actimeo=1800 0 0`
