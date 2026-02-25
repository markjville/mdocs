# Static IP on Ubuntu 16.04:

1. Edit /etc/network/interfaces changing:

```
iface <interface> inet dhcp
with
iface <interface> inet static
	addrss 10.170.1.x
	netmask 255.255.255.0
	gateway 10.170.1.31
	dns-nameservers 10.170.1.48 10.170.1.249
```

2. Restart networking:

`sudo /etc/init.d/networking restart`
