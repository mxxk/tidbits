# FFmpeg Tidbits

## Offset Subtitle Timestamps

```
ffmpeg -itsoffset -1900ms -i input.srt output.srt
```

`-itsoffset` accepts a time duration according to https://ffmpeg.org/ffmpeg-utils.html#time-duration-syntax

## Create Looping Animated PNG (With Pallette)

```
ffmpeg -i video.mp4 -vf 'split[sv],palettegen,[sv]paletteuse' -plays 0 -f apng output.png
```
