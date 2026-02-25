# Ubuntu server post install

## 1. Create User, other than root. Add user to sudoers:

`adduser JoeShmoe`

Add user to sudoers:

`usermod -aG sudo JoeShmoe`

## 2. Assign static IP

- Edit the network config `/etc/netplan/01-netcfg.yaml`. Change the values as desired.

- Apply changes:
  
sudo netplan apply

or

- Edit the file /etc/network/interfaces to modify/add:

```
auto enp0s3 (choose appropriate device)
iface enp0s3 inet static
address 10.1.1.83
netmask 255.0.0.0
gateway 10.1.1.1
dns-nameservers 8.8.8.8 8.8.4.4
```

- Restart networking stack:

```
$ sudo ip a flush enp0s3
$ sudo systemctl restart networking.service
```

## 3. Enable ssh:

- Install SSH server:

`sudo apt install openssh-server`
- Ensure that ssh service is running

`sudo systemctl status ssh`

- Edit ssh config:

`sudo vi /etc/ssh/sshd_config`

Uncommenting: `Port 22`

and

`PasswordAuthentication` yes

- Open port in Firewall

`sudo ufw allow ssh`

## 4. Change hostname:

- Type the hostnamectl command:

`sudo hostnamectl set-hostname newNameHere`


Delete the old name and setup new name

- Next Edit the /etc/hosts file:

`sudo nano /etc/hosts`

- eplace any occurrence of the existing computer name with your new one.

- Reboot the system to changes take effect:

`sudo reboot`

## 5. Install ClamAV

- Install depdencies:

`sudo apt-get install clamav clamav-daemon`

- Verify install:

`clamscan --version`

- Manually run a scan/clean on whole system:

`sudo clamscan --infected --remove --recursive /`

## 6. (Optional) Install GUI with tools:

## 7. (Optional) Make GUI start at boot:

## 8. (Optional) Install NFTS support:
