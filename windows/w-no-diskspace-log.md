# Low or No Disk Space

Symptom: Windows 7 computer's C: drive fills up, though user files are not the cause.

## Cause A: 

Component-Based Servicing logs are consuming too much space in `C:\Windows\Logs\CBS `

### To fix:
1. Delete the excessive "cab_xxxxx" files.
2. Stop the Windows Modules Installer (TrustedInstaller) service
3. Delete or move the large `Cbspersist_XX.log` file out of `\Windows\Logs\CBS`.
4. Start the Windows Modules Installer (TrustedInstaller) service

## Cause B:

Component-Based Servicing logs (CBS) compression is at fault. Check sizes in `C:\Windows\TEMP` for excessive cab files

### To fix:
1. Stop the Windows Modules Installer (TrustedInstaller) service.
2. Delete or move the large Cbspersist_XX.log file out of \Windows\Logs\CBS.
3. Start the Windows Modules Installer (TrustedInstaller) service
