# Issue: Network icon question mark appears in Gnome

1. Edit `sudo nano /etc/NetworkManager/NetworkManager.conf`
and change the line `managed=false` to `managed=true`

2. estart network stack:

`sudo service network-manager restart`
