# Deleting stubborn print jobs

Open cmd prompt as admin:

```
net stop spooler
del %systemroot%\System32\spool\printers\* /Q
net start spooler
```

If this still fails, restart computer and try again.
