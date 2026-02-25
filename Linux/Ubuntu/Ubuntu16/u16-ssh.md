# Setup SSH on Ubuntu 16.04

1. Install SSH:

`sudo apt-get install openssh-server`

2. Check status of ssh service:

`sudo service ssh status`

3. Edit the SSH config file:

`sudo vi /etc/ssh/sshd_config`

Uncommenting: `Port 22`

5. Restart SSH:

`sudo service ssh restart`

6. Allow through firewall:

`sudo ufw allow 22`
