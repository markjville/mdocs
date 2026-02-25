# Windows 10 password reset

1. Boot off a Windows 10 DVD (or USB)
2. When the WINDOWS SETUP screen appears, press SHIFT+F10 to launch a CMD window
3. Type `ren d:\windows\system32\utilman.exe utilman.exe.bak` and press the ENTER key
4. Type `copy d:\windows\system32\cmd.exe d:\windows\system32\utilman.exe` and press the ENTER key
5. Exit the Windows 10 setup (just power down)
6. Boot normally to your hard drive
7. At the Login Screen click the EASE OF ACCESS icon (beside the Power icon in the bottom right corner of the screen).  Because of step 4, this will launch a CMD window
8. Type `net user test /add` and press the ENTER key
9. Type `net localgroup administrators test /add` and press the ENTER key
10. Press ALT+F4 to close the CMD prompt
11. Click the Power icon (bottom right corner of the screen) and select RESTART
12. Sign in as TEST without a password
13. Reset user's password
14. Delete TEST user and restore original utilman.exe
