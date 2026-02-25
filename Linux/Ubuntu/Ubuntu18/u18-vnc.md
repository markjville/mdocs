# Install VNC Server with Gnome display on Ubuntu 18.04

--Note that this doesn’t persist on reboot

1. Install Tiger VNC

`sudo apt install xserver-xorg-core`
`sudo apt install tigervnc-standalone-server tigervnc-xorg-extension tigervnc-viewer`

2. Start VNC server and set VNC password

`vncserver`

3. Create startup script for VNC desired parameters 

```
vi ~/.vnc/xstartup
#!/bin/sh 
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
vncconfig -iconic &
dbus-launch --exit-with-session gnome-session &
```

4. Start VNC Server

`vncserver -localhost no -geometry 800x600 -depth 24`


5. Create startup script

`sudo nano /etc/systemd/system/vncserver@.service`

```
[Unit]
Description=VNC Server by TeknoTut
After=syslog.target network.target

[Service]
Type=forking
User=JohnDoe

# Clean any existing files in /tmp/.X11-unix environment
ExecStartPre=/usr/bin/vncserver -kill :%i > /dev/null 2>&1 || :
ExecStart=/usr/bin/vncserver -geometry 800x600 -depth 24 -localhost no :%i
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target
```

Note that in the User row, make sure the user matches the user you are using. Because we use a user JohnDoe, we fill the option JohnDoe.

6. Stop all VNC sessions if available.

`vncserver -kill :*`

7. Enable startup on boot:

```
sudo systemctl enable vncserver@1
sudo systemctl start vncserver@1
```

Source: [https://www.teknotut.com/en/install-vnc-server-with-gnome-display-on-ubuntu-18-04/[(https://www.teknotut.com/en/install-vnc-server-with-gnome-display-on-ubuntu-18-04/)
