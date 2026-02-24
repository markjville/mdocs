# Install NFTS on CentOS 8

## 1. Make sure you have prereqs:
`sudo dnf groupinstall "Development Tools"`
`sudo dnf install tar`

## 2. Download package:
`curl https://tuxera.com/opensource/ntfs-3g_ntfsprogs-2017.3.23.tgz | tar -xvpz`

## 3. Change into the newly formed directory and run configure:
`./configure --prefix=/usr/local --disable-static`

## 4. Complile it
`make`

## 5. Install it
`sudo make install`
