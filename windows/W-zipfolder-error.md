# Fix Compressed Folder Access Denied Error

## Fix the `TEMP` environment variable

1. Right-click Computer, click Properties

2. Click Advanced System Settings(Alternately you can launch this page directly by running systempropertiesadvanced.exe)

3. Click Environment Variables

4. In the User variables for <username>, select TEMP and click Edit…(In case the TEMP variable is missing, you’ll have to create one by clicking the New… button.)

5. Verify that the variable value is set as: 
`%USERPROFILE%\AppData\Local\Temp`

Click OK.

7. Logoff and Login back to your user account.

## Verifying and Fixing Permissions for the %TEMP% Folder

If the %TEMP% variable is not the problem, then the next step is to verify & fix the NTFS permission for the %TEMP% folder.

1. Open an elevated or Administrator Command Prompt.

2. Type the following command: 
`takeown /f %TEMP% /r /d y`
3. Enter each command one by one:
```
icacls %TEMP% /grant SYSTEM:F /T
icacls %TEMP% /grant {username}:F /T
```
   
4. Replace {username} with the actual user account name. In the example below, the user is "John": 
`icacls %TEMP% /grant John:F /T`
