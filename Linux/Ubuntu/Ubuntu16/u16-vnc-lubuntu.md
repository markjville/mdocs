# Setup VNC on Lubuntu 16.04

After configuring static IP:

1. Install tightvncserver:

`sudo apt-get install tightvnc viewer`

2. Set VNC password:

`vncpasswd`

Enter password

3. Kill current session in order to edit the vnc config file:

`tightvncserver -kill :1`

4. Create the VNC config file:

```
vi ~/.vnc/xstartup
#!/bin/sh
xsetroot -solid grey
export XKL_XMODMAP_DISABLE=1
#autocutsel -fork
openbox &
/usr/bin/lxsession -s Lubuntu &
```

5. Give execute permissions to config file:

`sudo chmod +x ~/.vnc/xstartup`

6. Stop and restart tightvncserver

```
tightvncserver -kill :1
tightvncserver :1
```
