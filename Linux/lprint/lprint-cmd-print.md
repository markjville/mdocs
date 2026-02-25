# Command line printing of multiple files:

1. Determine available printers and their names:

`cat /etc/printcap`

2. Insert file names into command below:

`lpr -Pprintername-from-step-1 file1.txt. file2.txt file3.txt`
