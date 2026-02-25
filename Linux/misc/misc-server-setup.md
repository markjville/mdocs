# Notes on server setup:

1. Install OS and update
2. Networking: static IP and change hostname
3. Enable ssh
4. Install programs and ClamAV. Make services persistent at startup: sudo systemctl enable service
5. Open ports 80 and 443 (for webservices), port 22  for SSH and any other ports for services.
6. Setup backup of DBs, files, etc.
