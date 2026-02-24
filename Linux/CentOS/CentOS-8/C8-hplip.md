# HPLIP setup on CentOS 8

Note the default install through the repos is an older version, which does not support the latest models.

## 1. Remove previous lib if necessary
`dnf remove hplip-common-3.18.4-9.el8.x86_64`

## 2. Install the broken HP version by brute force (on your own responsibility) from here https://developers.hp.com/hp-linux-imag ... g/gethplip (You need RHEL 8 variant)
`rpm -ivh hplip-3.20.6-RHEL8-x86_64.rpm –nodeps`

## 3. Install the SNMP package if needed
`dnf install net-snmp`

## 4. Break the common sense and link python3 as python to make hp-setup command happy
`ln -s /usr/bin/python3 /usr/bin/python`

## 5. Install your printer by IP. May work without, but I had to give it the IP address manually.
`hp-setup -i 192.168.X.Y`
