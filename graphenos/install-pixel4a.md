# Install GrapheneOS on Pixel 4a

1. On Android, run system updates.

2. Install fastboot and signify. Make sure it is v. 29.0.6 or greater.
```
sudo dnf install android-tools
dnf copr enable lhajn/signify
dnf install signify
```

3. On the Pixel, enable developer options and OEM unlocking with an internet connection:
a) Enable the developer options menu by going to Settings ➔ *About phone* and pressing on the build number menu entry until developer mode is enabled.
b) Go to Settings ➔ System ➔ Advanced ➔ Developer options and toggle on the 'Enable OEM unlocking' setting. This requires internet access on devices with Google Play services as part of Factory Reset Protection (FRP) for anti-theft protection.

4. Export path of SDK Platform Tools to root:
a) Download and extract tools to `/home/mark/tools`
b) run cmd:
`export PATH=/home/mark/tools:/home/mark/tools/bin:$PATH`
5. Unlocking the bootloader
a) change to root
b) Turn off the device and then turn it on by holding both the Volume Down and Power buttons. It should be in “fastboot mode”, not recovery or rescue.
c) Unlock the bootloader to allow flashing the OS and firmware:
`fastboot flashing unlock`
6. Download the latest GrapheneOS image:
a) Download the factory images public key (factory.pub) in order to verify the factory images:
`curl -O https://releases.grapheneos.org/factory.pub`
b) Download the factory images for the device from the releases page.
`curl -O https://releases.grapheneos.org/sunfish-factory-2020.11.05.18.zip`
`curl -O https://releases.grapheneos.org/sunfish-factory-2020.11.05.18.zip.sig`

c) Verify the factory images using the signature if you were able to obtain signify from trusted package repositories (see above):
`signify -Cqp factory.pub -x sunfish-factory-2020.11.05.18.zip.sig && echo verified`
This will output verified if verification is successful. If something goes wrong, it will output an error message rather than verified.
7. Flash the image to the phone. Make sure to plug USB cable to built in port on motherboard, not hub or front ports:
	a) Extract the image: `unzip sunfish-factory-2020.11.05.18.zip`
	b) Change into that directory:  `cd sunfish-factory-2020.11.05.18`
	c) Flash the Pixel as root: `./flash-all.sh`

8. Lock the boot loader as root: `fastboot flashing lock`
9. Disable OEM unlocking within GrapheneOS: Developer settings menu found in same place as Android: turn on Developer Mode in “About this Phone”, tapping model number 7 times. Then go to System-> Advanced→Developer options.

Notes:
-The default android-tools from Ubuntu repos is way out of date. One can only use the latest from Google.
-I had trouble with fastboot “waiting for any device”, despite having latest adb and fastboot installed. It turned out that I need to run the commands as root, by exporting the  path of the SDK tools directory in home/mark/tools into root’s $PATH:
`export PATH=/home/mark/tools:/home/mark/tools/bin:$PATH`


To manually update platform-tools:
1. download the latest toolset: https://developer.android.com/studio/releases/platform-tools.html
2. Extract and copy contents to `/home/mark/tools`
3. Add path for tools: `export PATH=/home/mark/tools:/home/mark/tools/bin:$PATH`
4. cd to extracted latest Graphene image and continue from step 8.

-Install f-droid:
In Vanadium, browse to https://f-droid.org.
    1. Tap the DOWNLOAD F-DROID button.
    2. Tap Download in the Download file dialog.
    3. Tap OK in the This type of file can harm your device notification.
    4. Once the FDroid. ...
    5. Tap INSTALL in the F-Droid Do you want to install this application? ...
    6. Tap DONE in the F-Droid App installed dialog.
