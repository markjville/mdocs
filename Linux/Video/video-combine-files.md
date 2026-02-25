# Combine video files on Linux

## Concatenate m4v videos

`mencoder -oac pcm -ovc copy -idx -o FinalVideo.m4v VTS_02_1.m4v VTS_02_2.m4v`

## Concatenate vob files

`cat file1.vob file2.vob file3.vob > files.vob`

then

handbrake/ffmpeg to smaller size
