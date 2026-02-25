# To Batch Rename Files in Linux (and Mac too)

```
for filename in *.mp3; do 
    [ -f "$filename" ] || continue
    mv $filename ${filename//deti-online.com_-_/}

done
```
