# Install GUI on CentOS 8

## 1. Install GNOME desktop environment:

`dnf groupinstall workstation`

## 2. Enable GUI to start at reboot:

`systemctl set-default graphical.target`

## 3. Startup GUI now:

`systemctl isolate graphical`
