# Ubuntu: Revert to an older kernel

1. Verify the kernel versions from dpkg to confirm that the broken kernel has been installed. If the currently broken kernel was linux-image-4.4.0-64-generic it should show up in the following command.

`dpkg -l | grep linux-image`

2. remove the broken kernel

`sudo apt-get purge linux-image-4.4.0-64-generic`

3. remove its headers too

`sudo apt-get purge linux-headers-4.4.0-64-generic`
