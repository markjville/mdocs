# Hardware info

## dmidecode: To display detailed info on hardware:

Example: to get info on memory hardware:

`sudo dmidecode --type memory`

## lshw: another utility to get info on hardware

This example shows info about disk, like what disk is named:

`sudo lshw -c disk`

or

`lshw -class disk -class storage`

## smartctl: to get smart info on drives

`smartctl -a /dev/sda`
