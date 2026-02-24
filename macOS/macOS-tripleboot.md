# Notes on triple boot Mac:

1. Install macOS, but during installation, chose to make 3 partitions on macintoshHD

2. During Linux installation, delete the partition for Linux into free space. Then create 3 new partitions from this space: `/boot/efi`, `/`, and `swap`. Install Linux assigning former partitions as is proper.

3. Install Windows on remaining partition. It will further subdivide this last partiton as it needs.

4. Install rEFInd as boot loader:
[https://www.rodsbooks.com/refind/installing.html](https://www.rodsbooks.com/refind/installing.html)
