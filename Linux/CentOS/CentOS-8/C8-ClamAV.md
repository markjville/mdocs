# Installation of ClamAV on CentOS 8

Last Updated on October 3rd, 2019 by Edgaras G.

## 1. Installing EPEL

We have to add the additional repository:

`sudo yum -y install epel-release`

`sudo yum clean all`

Install ClamAV:
`sudo yum -y install clamav-server clamav-data clamav-update clamav-filesystem clamav clamav-scanner-systemd clamav-devel clamav-lib clamav-server-systemd`

## 2. Configuring SELinux

Additional configuration is required if you want to use ClamAV with enabled SELinux kernel module.

```
sudo setsebool -P antivirus_can_scan_system 1
sudo setsebool -P clamd_use_jit 1
Next, you have to verify the changes:
sudo getsebool -a | grep antivirus
```

You should get this result:

antivirus_can_scan_system --&gt; on
antivirus_use_jit --&gt; off

## 3. Configuring ClamAV

Before you can enable ClamAV configuration, you need to remove Example string from the configuration file:

`sudo sed -i -e "s/^Example/#Example/" /etc/clamd.d/scan.conf`

Next, open the configuration file:

`sudo nano /etc/clamd.d/scan.conf`

Find the following line:

`#LocalSocket /var/run/clamd.scan/clamd.sock`

Remove the # symbol and save your changes.

Now, remove Example string from ClamAV’s freshclam update engine configuration file:

`sudo sed -i -e "s/^Example/#Example/" /etc/freshclam.conf`

Once that’s done, you can run virus definition database update:

`sudo freshclam`

You should get a similar output:

```
ClamAV update process started at Tue Dec  19 09:30:20 2016
main.cvd is up to date (version: 57, sigs: 4218790, f-level: 60, builder: amishhammer)
Trying host database.clamav.net (69.163.100.14)...
Downloading daily.cvd [100%]
daily.cvd updated (version: 22739, sigs: 1100989, f-level: 63, builder: neo)
Downloading bytecode-279.cdiff [100%]
Downloading bytecode-280.cdiff [100%]
Downloading bytecode-281.cdiff [100%]
Downloading bytecode-282.cdiff [100%]
Downloading bytecode-283.cdiff [100%]
bytecode.cld updated (version: 285, sigs: 57, f-level: 63, builder: bbaker)
Database updated (5319836 signatures) from database.clamav.net (IP: 168.143.19.95)
```

Make Clamd service start on boot:

```
sudo systemctl start clamd@scan
sudo systemctl enable clamd@scan
```

# Done!
