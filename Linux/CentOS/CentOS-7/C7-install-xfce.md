# How To Install Xfce GUI In CentOS 7 Linux

1. Install the EPEL repo:

`yum install epel-release -y`

2. Install the GUI components
   
`yum groupinstall "Server with GUI" -y`

*Note* This installs Gnome3, because XFCE still needs some dependencies from Gnome3

3. Now we can install XFCE desktop environment

`yum groupinstall "Xfce" -y`

4. Check to see current GUI default
  
`systemctl get-default`

5. Set the system to boot into a graphical environment

`systemctl set-default graphical.target`

6. Verify that the change took

`systemctl get-default`

10. to launch the GUI from the multi-user.target
`systemctl isolate graphical.target`

To undo using XFCE: 
`yum groupremove "Xfce"`

Source:
https://www.rootusers.com/how-to-install-xfce-gui-in-centos-7-linux/
