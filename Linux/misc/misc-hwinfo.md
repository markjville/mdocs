# Hardware info

## RAM:
`sudo dmidecode --type memory`

## Drives:
This shows info about disk, like what disk is named:

`sudo lshw -c disk`

or

`lshw -class disk -class storage`

`smartctl -a /dev/sda`
