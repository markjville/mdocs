# Converting images in qemu

## Convert from Virtualbox to qcow2

`qemu-img convert -f vdi -O qcow2 orignal-VM.vdi New-VM.qcow2 `

## Convert from raw to qcow2:

`qemu-img convert -f raw original.img -O qcow2 new.qcow2`
