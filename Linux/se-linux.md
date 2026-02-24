# SE Linux

### Configuration file:/etc/selinux/config

## To check the status of SE Linux:
- `getenforce`
- `cat /etc/selinux/config`
-  `sestatus`

### To temporarily enable/disable SELinux # setenforce [1|0]

### To turn off SE Linux permanently:
1. `sudo vi /etc/selinux/config`
2. Modify the config:
`SELINUX=disabled`
3. reboot

## Different types of security policy
The /etc/selinux/config file controls the state of SELinux on the system. SELINUX= can take one of these three values:
    • enforcing – SELinux security policy is enforced.
    • permissive – SELinux prints warnings instead of enforcing (disabled).
    • disabled – No SELinux policy is loaded (disabled).
    
SELINUXTYPE= can take one of following:
    • targeted – Targeted processes are protected.
    • minimum – Modification of targeted policy. Only selected processes are protected.
    • mls – Multi Level Security protection.


More info:
https://opensource.com/article/18/7/sysadmin-guide-selinux
