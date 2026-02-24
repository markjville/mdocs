# Install Wine64 on CentOS 8

## 1. Preliminary steps

Change to root:

`sudo -i`

Update the system: 
```
dnf clean all
dnf update
```

Install some needed packages:

```
dnf groupinstall 'Development Tools'
dnf install libX11-devel freetype-devel zlib-devel libxcb-devel libxslt-devel libgcrypt-devel libxml2-devel gnutls-devel libpng-devel libjpeg-turbo-devel libtiff-devel gstreamer1-devel dbus-devel fontconfig-devel
```

## 2. Install Wine source code. Adjust code for the latest version

```
cd /opt
wget https://dl.winehq.org/wine/source/7.0/wine-7.0.tar.xz
tar -Jxf wine-7.0.tar.xz
cd wine-7.0
```

Set the installation environment for Wine according to your system.

For 64-Bit Systems:

`./configure  --enable-win64`

Compile the wine source and install it on your system.

```
make
make install
```

## 3. Verify the version of Wine

`wine64 --version`

# Done!
