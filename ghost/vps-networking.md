1. Get DNS A record pointed to server IP address before starting next step. Otherwise, SSL cert will not generate. Example:

| Host	| Type | Value | TTL |
| :---: | :---: | :---: | :---: |
| @ | A	| 111.222.333.444	| 1800 |

2. In DO portal, create new project and add droplet. For Droplet, instead choosing the settings, go to marketplace tab and find Ghost droplet. Set root passwd.

3. After creation of droplet, log in to droplet via console. Follow prompts to setup Ghost: choose domain name of site instead of IP so that SSL cert is generated. enable ssh.

4. Reconnect through SSH, run updates to Ubuntu.

5. Set firewall rules to droplet:
   
*Inbound Rules*

| Type	| Protocol | Port Range	| Sources	|
| :---: | :---: | :---: | :---: |
| SSH	| TCP	22	| All IPv4 All IPv6	| More |
| Custom	| TCP 25	| All IPv4 All IPv6	| More |
| DNS |	TCP	53	|All IPv4 All IPv6	| More |
| HTTP	| TCP	80	| All IPv4 All IPv6	| More |
| HTTPS	| TCP	443 |	All IPv4 All IPv6	| More |
| Custom	| TCP	2368	| All IPv4 All IPv6	| More 
| DNS |	UDP	53	| All IPv4 All IPv6	| More |

*Outbound Rules*

| Type | Protocol | Port Range | Destinations |
| :---: | :---: | :---: | :---: |
| ICMP	| ICMP	|	All IPv4 All IPv6	| More |
| SSH	| TCP	22	| All IPv4 All IPv6 |	More |
| DNS |	TCP	53	| All IPv4 All IPv6 |	More |
| HTTP	| TCP	80	| All IPv4 All IPv6 |	More |
| HTTPS	| TCP	443	| All IPv4 All IPv6	| More |
| Custom	| TCP	465	| All IPv4 All IPv6	| More |
| Custom	| TCP	2368	| All IPv4 All IPv6	| More |
| DNS | UDP	53	| All IPv4 All IPv6	| More 
