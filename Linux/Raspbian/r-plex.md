# Plex Media Server setup on Raspberry Pi

Source: https://pimylifeup.com/raspberry-pi-plex-server/

1. Mount the NAS share containing media

`192.168.0.xxx:/c/media /mnt/media nfs vers=3 0 0`

3. Update operating system, for Ubuntu:
```
sudo apt-get update
sudo apt-get upgrade
```

5. Add the official Plex package repository.

`sudo apt-get install apt-transport-https`

5. Add Plex repositories to the “apt” package managers key list.

`curl https://downloads.plex.tv/plex-keys/PlexSign.key | sudo apt-key add -`

6.Add the official plex repository to the sources list:

`echo deb https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plexmediaserver.list`

7. As we have just added a new repository to our sources, we will need to run the “update” command again to refresh the package list.

`sudo apt-get update`

If you get the error “/usr/lib/apt/methods/https could not be found.” Then the https transport package hasn’t been installed. Double check that it has been installed correctly.

6. To install the “plexmediaserver” package, go ahead and run the command below.

`sudo apt-get install plexmediaserver`

During installation:
```
Configuration file '/etc/apt/sources.list.d/plexmediaserver.list'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** plexmediaserver.list (Y/I/N/O/D/Z) [default=N] ? I
```

7. The Plex Media Server package will utilize a user named “plex“. Change the server’s default file so that it utilizes the “pi” user instead.

`sudo nano /etc/default/plexmediaserver`

8. Within this file change the PLEX_MEDIA_SERVER_USER line from *plex* to *pi* as we have shown in our example below.

Find

`export PLEX_MEDIA_SERVER_USER=plex`

Replace with

`export PLEX_MEDIA_SERVER_USER=pi`

Save and exit the file by pressing Ctrl + X then pressing Y and pressing ENTER.

9. Restart the Plex service:

`sudo systemctl restart plexmediaserver`

10. Check the hostname:

`hostname -I`

11. Now open up the cmdline.txt file.

`sudo nano /boot/cmdline.txt`

12. At the bottom of this file, add the following line: (Replacing “YOUR IP” with the IP you got from using hostname -I)

`ip=YOUR IP`

13. Exit by pressing ctrl x and then y to save.

15. Now simply restart the Pi by running the following command.

`sudo reboot`

16. The Raspberry Pi Plex media server should be ready.

## Connecting Clients to Plex on the Raspberry Pi

To connect to the browser, enter the IP followed by the port 32400 and /web/.
192.168.1.xxx:32400/web/



