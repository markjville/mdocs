# Restart networking on CentOS 8:

## Method 1 – Using NetworkManager Service 

Use the followings commands to start/stop network service on your CentOS/RHEL 8 Linux system.
```
sudo systemctl start NetworkManager.service
sudo systemctl stop NetworkManager.service
```

Use the followings commands to restart network service on your CentOS/RHEL 8 Linux system.

`sudo systemctl restart NetworkManager.service`

## Method 2 – Using nmcli Tool

The nmcli is the command-line utility for the managing NetworkManager on CentOS/RHEL 8 Linux system. You can simply use this utility to stop/start network service on your CentOS 8 or RHEL 8 system.

`sudo nmcli networking off`

`sudo nmcli networking on`
