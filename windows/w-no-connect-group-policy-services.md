# Error: Windows could not connect to the group policy client service 

## Fix:
1. `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services` this path should contain gpsvc key (a folder), which is responsible for service parameters and configuration.  I found that the key wasintact, so, you do not touch anything here.
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SVCHOST` This is the most important path you should look into, as it must contain the keys and values referred in the key #1.  Below are descriptions what must be present there.
- There must be Multi-String value called GPSvcGroup. My laptop was missing it.  So, you should create multi-string value named GPSvcGroup and assign it value GPSvc.
- Next, you must create a key (a folder) and name it GPSvcGroup
- Then open newly-created GPSvcGroup folder and create 2 DWORD values.
   
-- First called `AuthenticationCapabilities` and you must give it a value of `0x00003020` (or 12320 in decimal)
-- Second is called `CoInitializeSecurityParam` and it must have value of 1.
    
Once you completed all steps above, reboot the computer and the problem will be fixed. 
