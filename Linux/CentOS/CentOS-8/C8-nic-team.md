# Configure NIC Team on CentOS 8

Note: Though managed switches may offer LACP, it appeared to cause problems. Let Linux kernel handle the team instead of switch.

## 1. Install Teamd daemon if not already installed:

`sudo dnf install teamd`

Verify:

`rpm -qi teamd`

## 2. Check current interfaces:

`nmcli device status`

Get UUID:

`nmcli connection show`

## 3. Delete the interfaces as they are to recreate them:

```
nmcli connection delete a2533841-93bf-4a78-9c84-4f7e8669e92f     (Interface 1)
nmcli connection delete 7c70d70-2fb2-4a19-bc02-d71b49a6ffac     (Interface 2)
```

## 4. Check status:

`nmcli device status`

## 5. Configure NIC teaming with nmcli tool:

`nmcli connection add type team con-name bond0 ifname bond0 config '{"runner": {"name": "activebackup"}}'`

Note: The value ‘activebackup’ is a runner that can be replaced with either round-robin, broadcast , random or lacp.

## 6. Verify that NIC team was created:
`nmcli connection show`

## 7. Configure the network config for the NIC team:

```
nmcli con mod bond0  ipv4.addresses 192.168.0.199/24
nmcli con mod bond0  ipv4.gateway 192.168.0.1
nmcli con mod bond0  ipv4.dns 8.8.8.8
nmcli con mod bond0  ipv4.method manual
nmcli con mod bond0  connection.autoconnect yes
```

## 8. Add the network slaves to the team interface:

```
nmcli con add type team-slave con-name bond0-slave0 ifname enp3s0 master bond0
nmcli con add type team-slave con-name bond0-slave1 ifname enp4s0 master bond0
```

Change interface in "enp3s0" and "enp4s0" to proper name.

## 9. Verify the team interface and slave:

`nmcli connection show`

## 10. Restart the team interface:

`nmcli connection down bond0 && nmcli connection up bond0`

## 11. Verify the config details of the team interface

`ip address show dev bond0`

## 12. Test the functionality of the Active-Backup team:
`nmcli device disconnect enp0s3`
`sudo teamdctl bond0 state`


## To delete a Team:

1. `nmcli connection down bond0`
2. `nmcli connection delete bond0-slave0 bond0-slave1`
3. `nmcli connection delete bond0`
