# How to Set Up a Printer by Using the lpadmin Command

    1. Connect the printer to the system, then turn on the power to the printer.
       
    2. Become an administrator.
       
    3. Use the lpadmincommand with the "–p" option to add a printer to CUPS.
       Only the most commonly used options of the CUPS lpadmin command are shown here. For information about other options, see the lpadmin(8) man page.
       `/usr/sbin/lpadmin -p printer-name -E -v device -`
       
       P 
       specifies the full path to ppd file
       
       –p
       Specifies the name of the printer to add.
       
       –E
       Enables the destination and accepts jobs.
       
       –v
       Sets thedevice-uriattribute of the print queue.
       
       –P
       Specifies a PPD (Postscript Printer Description) file to use with the printer. The following are standard locations of PPD files:
        ◦ /usr/share/cups/model/foomatic-db-ppds/manufacturer name
        ◦ /usr/share/cups/model/SUNWhplip
        ◦ /usr/share/ppd/SUNWhpijs/HP
        
       See the examples at the end of this procedure.
       
    4. (Optional) If you are not using the lpadmin command with the "–E" option, enable the printer to accept print requests and to print those requests.
    
       `cupsaccept printer-name`
       
       `cupsenable printer-name`
       
    5. Verify that the printer is correctly configured.
    
       `lpstat -l -p printer-name`
       
## Example 2-1: Adding a Printer That Uses a PPD File

This example shows how to add an HP LaserJet printer LaserJet by using a JetDirect network interface with the IP address 10.1.1.1.
`/usr/sbin/lpadmin -p LaserJet -E -v socket://10.1.1.1 \ -P /usr/share/ppd/SUNWhpijs/HP/hp-laserjet_p4515-ps.ppd.gz`

Notes:

For the Sharp MX printers, use port 9100. For example:

socket://10.170.1.235:9100

Source: https://docs.oracle.com/cd/E36784_01/html/E36821/gllia.html
