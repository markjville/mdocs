# To extract audio from mp4 on linux

`ffmpeg -i foo.mp4 foo2.mp3`

For .ogg
`ffmpeg -i foo.mp4' -vn -acodec libvorbis -y foo2.ogg`


To extract from (time) to (time) and keep original:

`ffmpeg -i foo.mp4  -ss 00:02:35 -to 00:06:37 -c:v copy -c:a copy foo-section.mp4`

This copies from minute 2:35 to 6:37 into "foo-section.mp4" and keeps the original.
