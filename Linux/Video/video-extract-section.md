# Cut a section from a video with ffmpeg

`ffmpeg -i input.mp4 -ss 00:05:20 -t 00:10:00 -c:v copy -c:a copy output1.mp4`

“-ss” – starting section.

“-t” – time from starting section

The above cmd will extract video from the starting mark 5:20 and extract 10 min. of video labeling it “output.mp4”
