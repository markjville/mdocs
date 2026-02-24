# How to Upgrade Kernel on CentOS 7

## 1. Update and upgrade CentOS 7

The first thing we must do before upgrading the kernel is to upgrade all packages to the latest version. Update the repository and all packages to latest versions with the yum command below.

`yum -y update`

Now install the following package to make installation and updating process fast.

`yum -y install yum-plugin-fastestmirror`

CentOS 7 System updated and all packages upgraded to latest versions.

## 2. - Checking kernel version

In this tutorial, we will use CentOS 7.3 with default kernel 3.10. Check your CentOS version with the following commands.
```
cat /etc/redhat-release
cat /etc/os-release
```

You will get the system info as shown below.

## 3. Add ELRepo Repository

Before installing new kernel version, we need to add new repository ELRepo repository. That's because we want to use the kernel version from the ELRepo community.
Add ELRepo gpg key to the system.

`rpm --import https://www.elrepo.org/RPM-GPG-KEY-elrepo.org`

Now add new ELRepo repository with rpm command.

`rpm -Uvh http://www.elrepo.org/elrepo-release-7.0-2.el7.elrepo.noarch.rpm`

Next, check all repositories enabled on the system, and make sure ELRepo is on the list.

```
yum repolist
ELRepo repository has been added to the CentOS 7 server.
```

## 4. Install new Kernel version

In this step, we will install latest kernel version (4.11.2 - the Latest stable version on kernel.org) from the ELRepo repository.
Use the following yum command for this.

`yum --enablerepo=elrepo-kernel install kernel-ml`

`--enablerepo` is an option to enable specific repository on CentOS system. By default, 'elrepo' repository is enabled, but for our case, we needed 'elrepo-kernel'.
You can check all of the available repositories on the system (enabled as well as disabled) with the following command.

`yum repolist all`

## 5. Configure Grub2 CentOS 7

At step 4, we've already installed a new kernel 4.11.2 to the system. Now we will show you how to make it the default kernel version that will load when the system is starting.
Check all available kernel versions with the awk command below.

`sudo awk -F\' '$1=="menuentry " {print i++ " : " $2}' /etc/grub2.cfg`

We want to use kernel 4.11 as our default, so you can use the following command to make this happen.

`sudo grub2-set-default 0`

`0` - it's from the awk command on the top. Kernel 4.11.2 = 0, and Kernel 3.10 = 1. When you want to revert back to the old kernel, you can change the value of the grub2-set-default command to 1.

Next, generate the grub2 config with 'gurb2-mkconfig' command, and then reboot the server.

```
sudo grub2-mkconfig -o /boot/grub2/grub.cfg
sudo reboot
```

Please login to the server again, and check currently used kernel.

`uname -msr`

The result should be that the kernel version 4.11.2 is being used on your system.

## 6. Remove old kernel (optional)

This is an optional step that we think you need in order to get more free space. In this step, we will show you how to remove an old kernel from your CentOS 7 system. This can be done when you have several kernel versions installed on the server.
For this purpose, we need to install the yum-utils utility from the repository.

`yum install yum-utils`

Now clean your old kernel with the following command.

`package-cleanup --oldkernels`

That means you've only 2 or 3 versions of kernel installed. If you have more than 3 version installed, the command will automatically remove old kernel from your system.
CentOS 7 Kernel has been updated to the latest stable using ELRepo kernel version.

Source:
https://www.howtoforge.com/tutorial/how-to-upgrade-kernel-in-centos-7-server/
