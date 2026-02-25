# To make appimage appear in Application menu

For a solid and extensive answer read this: https://askubuntu.com/a/112812/1024353, for a minimal working example, continue reading.

Besides the Exec, you should also add a Name and Type field to your .destop file. These fields are required by the desktop entry spec.
So your minimal .desktop file could look like this:

```
Exec=/path/to/AppImage
Name=AppImageLauncher
Type=Application
```

I'll assume from this point that you named your file myappimage.desktop and placed it in ~/.local/share/applications/.

Note that putting this .desktop file in ~/.local/share/applications/ is probably more appropriate than in /usr/share/applications in this case, because you won't require root access.
Now make it executable:

`chmod 700 ~/.local/share/applications/myappimage.desktop`
