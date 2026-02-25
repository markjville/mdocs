# Restore lost "Documents" folder

Source: [here](https://www.backup-utility.com/windows-7/my-documents-folder-missing-windows-7-5740.html)

Scenario: when troubleshooting mapped drive issue, one deletes it when Documents is mapped to X:Drive. The result

1. Recreate *My Documents* folder in Explorer 
2. Reset the Registry User Folder Settings

a) Go Start and input regedt32 in search box to run Registry Editor Utility. Locate the path:
`HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\User Shell Folders`

b) Then the Documents folder corresponding default Name and Data are: Personal, %USERPROFILE%\Documents. Make sure they are correct. If not, change them to the right value.

c) To correct the Name field, right click the Name and choose Rename, input Personal. To change the Data value, double click the Name field, and type %USERPROFILE%\Documents, and click OK.


4. As admin: `attrib +r -s -h %USERPROFILE%\Documents /S /D` 
5. Reboot
