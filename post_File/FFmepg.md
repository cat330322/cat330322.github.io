FFmpeg

```
ffmpeg -i input.mp4 -vf "scale=1280*720" output.mp4
ffmpeg -i old.mp4 -s 1280x720 new.mp4
常见的视频宽高比例有：
标准屏4/3=1.3333
QQVGA:160x120
QVGA:320x240
VGA:640x480
SVGA:800x600
XGA:1024x768
标准宽屏16/9=1.7777
1920x1080
1280x720
1024x576
640x360
非标尺寸
1024x612:1.673
720x408:1.764
1024x556:1.842
720x384:1.875
```

```
ffmpeg -i  https://dh5.cntv.myalicdn.com/asp/h5e/hls/450/0303000a/3/default/311110.m3u8 01.mp4
```

