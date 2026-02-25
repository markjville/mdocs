# Determine the Desktop Environment (gnome, kde, etc...):

`echo $XDG_CURRENT_DESKTOP`

## Determine the display manager (wayland or xorg):

`loginctl show-session $(awk '/tty/ {print $1}' <(loginctl)) -p Type | awk -F= '{print $2}'`
