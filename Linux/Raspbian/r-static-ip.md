# Set static IP on Raspbian Buster (Debian 10)

1. Retrieve the current DNS server:
`cat /etc/resolv.conf`

Note the DNS IP.

2. Edit the dhcpcd.conf file, uncommenting the static ip_address. static routers, static domain_name_servers
`vi /etc/dhcpcd.conf`

3. Reboot

4. Verify IP address:
`hostname -I`
