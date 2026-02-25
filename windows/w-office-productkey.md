# Office product key retrieval

*Note: Way too many times, I have encountered situations where IT or staff don't keep track of their product keys. When the inevitable clean install happens, Office must be repurchased for the same computer. To prevent this unnecessary charge, below is a way to retrieve for the honest paying customer of the Office SW.*

## For Office 2010:
1. Go to: https://support.microsoft.com/en-us/contactus/
2. Start chat with automated chatbot, asking for product download. Chatbot will ask for product key.
3. Enter 25-character key and link will appear for download.

## For Office 2013/2016:
First, find the last five digits of the product key associated with your computer.
    1. Go to the PC that has Office 2013 installed
    2. Right click the Windows icon and select Command Prompt.
    3. Enter the appropriate command:
    
### For 32 bit Windows:
`cscript “C:\Program Files\Microsoft Office\Office15\OSPP.VBS” /dstatus`

### For 64-bit Windows:
cscript “C:\Program Files (x86)\Microsoft Office\Office15\OSPP.VBS” /dstatus

1. The command prompt box will show you the last five digits of the product key associated with the installation on that PC.

2. Make a note of the PC the Office 2013 product is installed on, and five digit number. You will need this for reference.
