# Install HFS+ drivers on CentOS 7

First thing first, you have to install kmod-hfs & kmod-hfsplus and hfsplus-tools. 

## 1. Import GPG Key 

`rpm --import http://elrepo.org/RPM-GPG-KEY-elrepo.org`

## 2. Install ELRepo for CentOS-7

`rpm -Uvh https://www.elrepo.org/elrepo-release-7.0-3.el7.elrepo.noarch.rpm`

To install ELRepo for CentOS-6

`rpm -Uvh https://www.elrepo.org/elrepo-release-6-8.el6.elrepo.noarch.rpm`

## 3.  Install kernel modules for HFS

`yum install kmod-hfs`

## 4. Install kernel modules for HFS+

`yum install kmod-hfsplus`

## 5. Install HFS+ utilities

`yum install hfsplus-tools`
