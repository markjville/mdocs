# Installing FFmpeg on CentOS 8

## 1. Enable the Negativo repository and EPEL:
```
sudo dnf install epel-release dnf-utils
sudo yum-config-manager --set-enabled PowerTools
sudo yum-config-manager --add-repo=https://negativo17.org/repos/epel-multimedia.repo
```

## 2. Install ffmpeg
`sudo dnf -y install ffmpeg`
