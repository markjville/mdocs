# Batch converting audio formats

Example: Convert all .wav files to .ogg:

`$ for i in *.wav; do ffmpeg -i "$i" "${i%.*}.ogg"; done`
