# Shutting Down, Suspending, or Rebooting Commands with systemctl

For a clean shutdown (recommended choice)
`systemctl poweroff`

Shutting down in dirty state (last resort)

`systemctl halt`

For a simple reboot

`systemctl reboot`

To sleep (put data in RAM)

`systemctl suspend` 

To hibernate (put data on disk)

`systemctl hibernate`
