# Batch print file on a printer

1. Change to directory where files are.

2. Run a FOR-DO loop:
`for FILE in *.jpg ; do lpr "$FILE" ; done`

or

`lpr -PNetwork-ColorLaserJet_M283 /path/to/files…`
