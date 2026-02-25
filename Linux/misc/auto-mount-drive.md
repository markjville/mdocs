# Auto-mount a local drive

Edit /etc/fstab. Include UUID, locat mount point, filesystem, and options:

UUID=a9e8c53a-2225-425c-8b64-1c87259e496f    /mnt/Drive1 ntfs  auto,nofail,noatime,rw,user    0   0
