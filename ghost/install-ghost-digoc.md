# Notes on installing Ghost on Digital Ocean

1) Networking:
- Create A record for domain in DNS settings.
- Add A record to the digital ocean firewall for this droplet.

2) Update Ubuntu
`sudo apt update;sudo apt upgrade`

3) Install Node.js on Ubuntu
`	curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -`
`	sudo apt install nodejs`

- Check Node version.
`	node -v`
- Sample output:
`	v10.18.1`

- Check npm version:
`	npm -v`
- Sample output:
`	6.13.4`

4) Install MariaDB Database Server
`	sudo apt install mariadb-server mariadb-client`

- Check status of MariaDB:
`	systemctl status mariadb`

-Make persistent:
`	sudo systemctl enable mariadb`

- Secure MariaDB
`	sudo mysql_secure_installation`
- Check MariaDB version:
`	mariadb --version`
- Create Database:
`	sudo mariadb -u root`
`	create database ghost;`
- Create MDB user and grant privileges:   *PLEASE CHANGE PASSWORD*
`	grant all privileges on ghost.* to ghost@localhost identified by 'ghost_password';`
`	flush privileges;`
`	exit;`

5) Install Nginx Web Server
`	sudo apt install nginx`

- Open port 80 and 443.
`	sudo ufw allow ‘Nginx Full’`

6) Install Ghost
`	sudo npm install ghost-cli@latest -g`
- Create a directory (/var/www/ghost/) for Ghost.
`	sudo mkdir -p /var/www/ghost/`
- Grant permissions to your user account.
`	sudo setfacl -R -m u:youruser:rwx /var/www/ghost/`
`	sudo chmod 775 /var/www/ghost`
- Now change the working directory to /var/www/ghost/ and install Ghost.
`	cd /var/www/ghost/`
`	ghost install`
- Answer questions:
`	? Enter your blog URL: https://yourdomain.com`
`	? Enter your MySQL hostname: localhost`
`	? Enter your MySQL username: ghost`
`	? Enter your MySQL password: ghost_password`
`	? Enter your Ghost database name: ghost`
- Recommended that you accept to set up Nginx, SSL, and Systemd.
	
7) Edit the Nginx Config File
`	sudo vi /etc/nginx/sites-enabled/yourdomain.com.conf`
- Find the following line
`	server_name yourdomain.com;`
- Add the www domain.
`	server_name yourdomain.com www.yourdomain.com;`
- Save and close the file. Then delete the /etc/nginx/sites-enabled/yourdomain.com-ssl.conf file.
`	sudo rm /etc/nginx/sites-enabled/yourdomain.com-ssl.conf`

8) Install the Certbot Let’s Encrypt client
`	sudo apt install certbot python3-certbot-nginx`
- Obtain SSL certificate for both the www domain and the non-www domain.

`	sudo certbot --nginx --agree-tos --redirect --hsts --staple-ocsp --email your@email.com -d your-domain.com,www.your-domain.com`

-Restart Nginx.
`sudo systemctl restart nginx`

8. Misc tasks
- add markjville to ghost group
- change` /var/www/ghost ownership to your-user`


* * * * * * * * * * * *

Notes on installing ghost on Ubuntu:

- I always get hung up on ssl cert failing to generate. It is resolved by adding an A record to the digital ocean firewall for this droplet.
https://blog.stephsmith.io/setting-up-blog-with-ghost-and-digital-ocean-droplet/

- Issue: Navigation links don’t work. Fix: add “www” to link. Ex. your-domain.com/home   should be:  www.your-domain.com

- If installing from  ghost droplet without domain, use the IP address instead of domain name when configuring ghost for the first time.
