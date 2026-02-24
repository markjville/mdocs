# Install “rar” compression and decompression program

## 1. Download cert-forensics-tools-release-el8 rpm:
`wget https://forensics.cert.org/cert-forensics-tools-release-el8.rpm`

## 2. Install cert-forensics-tools-release-el8 rpm:
`rpm -Uvh cert-forensics-tools-release*rpm”`

## 3. Install rar rpm package:
`dnf --enablerepo=forensics install rar`
