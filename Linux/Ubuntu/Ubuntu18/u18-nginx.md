# Nginx on Ubuntu 18.04

1.Install:

`sudo apt install nginx`

2. Check the status of the Nginx service:

`sudo systemctl status nginx`

3. If you need to start the service:

`sudo systemctl start nginx`

4. Make persistant:

`sudo systemctl enable nginx`

5. Allow Nginx traffic through firewall:

`sudo ufw allow ‘Nginx HTTP’ or ‘Nginx Full’`

6. Test nginx in web browser with ip address

7. Create a Sample Server Block

Set up an HTML file. Going through a sample configuration is helpful. In a terminal window, enter the following command to create a “test” directory to work with:

`sudo mkdir /var/www/example`

Create and open a basic HTML index file to work as a test webpage:

`sudo vi /var/www/example/index.html`

In the Vi text editor (you can substitute your preferred text editor if you’d like), enter the following:
`Welcome to the Example Website!`

Save the file and exit.

8. Set up a Simple Server Block

Use the following command to create a new server block file for our Test website:

`sudo vi /etc/nginx/sites-available/example.com`
This should launch the Vi text editor and create a new server block file.
Enter the following lines into the text file:
```
server {
listen 80;
root /var/www/example;
index index.html;
server_name www.example.com;
}
```

This tells Nginx to look at the /var/www/example directory for the files to serve, and to use the index.html file we created as the front page for the website.
Save the file and exit.

9. Create a Symbolic Link to Activate Server Block
   
In the terminal window, enter the following command:

`sudo ln –s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled`

This creates a link and enables your test website in Nginx. Restart the Nginx service to apply the changes:

`sudo systemctl restart nginx`

10. Start Testing

In a browser window, visit www.example.com.

Source: [https://phoenixnap.com/kb/install-nginx-on-ubuntu](https://phoenixnap.com/kb/install-nginx-on-ubuntu)
