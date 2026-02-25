# Adding Static Route to Fix Networking conflicts

## Scenario: On Windows, other network connections stop working when VPN is active.

route -p add [destination_network] MASK [subnet_mask] [gateway_ip] METRIC [metric_value]

Example

`route add -p 10.10.10.0 mask 255.255.255.0 10.10.1.200
`
All traffic destined to 10.10.10.0 goes through the gateway 10.10.1.200


## Scenario: On Windows, email stops working when connected to VPN with conflicting config.

`route add -p 10.100.0.0 mask 255.255.0.0 10.100.3.1` (for VLAN 3, adjust for particular VLAN)
