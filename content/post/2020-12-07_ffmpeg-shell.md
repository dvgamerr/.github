+++
title = "รวมคำสั่งที่ใช้ enhance video ด้วย ffmpeg"
description = "ffmpeg enhance video for loop windows command"
tags = [
    "ffmpeg",
    "shell",
    "bash",
    "windows"
]
date = 2020-12-07T14:52:13Z
author = "Kananek Thongkam"
+++

Windows 10 user installation `ffmpeg` from chocolatey.

```bash
choco install ffmpeg
```

```shell
# *.flv files convert to *.mp4 and scale to 480p
for %a in (*.flv) do ffmpeg -y -i "%a" -vf scale=-1:480 -vcodec libx264 -b 400k -ac 2 -ar 44100 -ab 128k "%~na.mp4"


# merge 2 files mp4 video without change fps video and audio.
ffmpeg -i 10-A.mp4 -i 10-B.mp4 -filter_complex "[0:v:0] [0:a:0] [1:v:0] [1:a:0] concat=n=2:v=1:a=1 [v] [a]" -map "[v]" -map "[a]" output.mp4


# Convert *.dat files from dvd enchance to *.mp4 
for %a in (*.dat) do ffmpeg -i "%a" -vf yadif -c:v libx264 -crf 20 -c:a aac -b:a 128k -movflags +faststart "%~na.mp4"


# Resize *.mp4 video to 720p
for %a in (*.mp4) do ffmpeg -y -i "%a" -vf scale=-1:720 -vcodec libx264 -b 400k -ac 2 -ar 44100 -ab 128k "%~na.mp4"


# Convert audio e_ac3 to ac3 from *.mkv
for %a in (*.mkv) do ffmpeg -y -i "%a" -map 0 -c:v copy -c:a ac3 -b:a 640k -c:s copy "out_%~na.mkv"


# Extract Subtitle Track ID 3
for %a in (*.mkv) do mkvextract tracks "%a" 2:"%~na_und.sup"
```