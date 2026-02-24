# Make a USB Installer for macOS

## 1. Download the needed MacOS image: 
[https://support.apple.com/en-us/HT201372](https://support.apple.com/en-us/HT201372)

Note that the downloaded installer must be the 5+ GB size, not the 20MB size. The host OS may need to update to rectify this.

## 2. Install the MacOS package on a current Mac.
This includes a utility for making USB installer

## 3. In terminal, we will make USB installer using Yosemite as the example:
`sudo /Applications/Install\ OS\ X\ Yosemite.app/Contents/Resources/createinstallmedia --volume /Volumes/YosemiteInstaller --applicationpath /Applications/Install\ OS\ X\ Yosemite.app/`

## 4. Follow terminal prompts
