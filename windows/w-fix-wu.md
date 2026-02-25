# Windows Update not working 
Make certain that the KB3102810 is installed. Wait patiently while the green bar marches from left to right all the way. Then put KB3102810 into the search box. Windows Update not working 

See this [thread](http://answers.microsoft.com/en-us/windows/forum/windows8_1-update/windows-update-problem-error-code-80080008/de8114b5-1487-4b31-9b28-f11974718df1?auth=1) for more details:

Run as administrator the command promptType the following:

1. `net stop wuauserv`
    
2. `net stop cryptSvc`
   
3. `net stop bits`

4. `net stop msiserver`

5. `ren C:\Windows\SoftwareDistribution SoftwareDistribution.old`

6. `ren C:\Windows\System32\catroot2 catroot2.old`

7. `net start wuauserv`
  
8.`net start cryptSvc`

9. `net start bits`

10. `net start msiserver`

11. `pause`

19. `Exit`
    
Type "services" in the search box at start button. Find each of the following and ensure they are set to automatic: Background Intelligent Transfer services, Cryptographic, Windows Installer, Windows Update.  Double click on each item and choose automatic.

Now re-start Windows Update.  Do NOT restart Windows. It will likely take a long time. If that does not produce results, you should download and run the following.  It takes a very long time to run as well.

If the above fails, use one of the following:

The 64 bit version Microsoft’s [System Readiness tool](https://www.microsoft.com/en-ca/download/details.aspx?id=20858)  

The 32 bit version. [System Readiness tool](https://www.microsoft.com/en-us/download/details.aspx?id=3132)

If it is not installed, serach for the “KB3102810 Windows 7 64” if your system is 64 bit.  Download an install it.
