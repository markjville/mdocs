# To partition a USB drive on macOS

In Terminal, run the command below adjusting ":NAME-OF_DEVICE" as needed:

`diskutil partitionDisk /dev/disk1 GPT FAT32 NAME-OF-DEVICE 0b`
