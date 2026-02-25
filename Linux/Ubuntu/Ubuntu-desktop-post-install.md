# Ubuntu Desktop Setup

1) Update system and drivers

2) Test:
- audio
- headphones
- wifi/networkcard
- suspend
- restart
- shutdown
- webcam
- optical disk eject button
- volume keys
- screen brightness keys


3. Apps:
- VLC
- Chrome
- Teamviewer
- SimpleScan

4. Media config:

- Install restricted extras: sudo apt-get install ubuntu-restricted-extras
- DVD: sudo apt install libdvd-pkg && sudo dpkg-reconfigure libdvd-pkg gstreamer1.0-plugins-bad
- Change default DVD player to VLC:

Go to Settings. 
- Select "Devices" 
- Select "Removable media" 
- On the line that says "DVD video" select VLC from the pull down.
   
5. Add to dock:
- System Settings

6. ReadyNAS access:
- To access ReadyNAS, one must edit the /etc/smb.conf => Global Settings to allow:
`client min protocol = NT1`
