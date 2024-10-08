# ffmpeg

- https://github.com/cvabm/FFmpeg4Android-mkBuild

- 将本地mp4文件推流到rtsp
`ffmpeg -re -i 720.mp4 -c:v copy -c:a copy -f rtsp rtsp://localhost:8554/live`
- 将本地mp4文件推流到rtsp
`ffmpeg -re -stream_loop -1 -i .\\720.mp4 -vcodec libx264 -acodec aac -f flv rtmp://127.0.0.1:1935/live/hls`
- ffplay半屏播放
`ffplay -vf "scale=iw/2:ih/2" http://samples.mplayerhq.hu/V-codecs/h264/interlaced_crop.mp4`
- h264 ->rtp
`ffmpeg -re -i d:\videos\1080P.264 -vcodec copy -f rtp rtp://127.0.0.1:1234>test_rtp_h264.sdp`
`ffplay -protocol_whitelist "file,udp,rtp" -i test_rtp_h264.sdp`
- h264 -> ts
`ffmpeg -re -i d:\videos\1080P.264 -vcodec copy -f rtp_mpegts rtp://127.0.0.1:1234`
参考：https://zhuanlan.zhihu.com/p/450527182
- ffplay低延迟播放
`ffplay -fflags nobuffer -flags low_delay -framedrop -strict experimental -rtsp_transport tcp rtsp://admin:xxxx@10.166.5.11`
- 截屏
`ffmpeg -rtsp_transport tcp -hide_banner -i "rtsp://xxx" -y -r 0.5 -t 1 -q:v 2 "E:/test.jpeg"`
- 录像
`ffmpeg -i "rtsp://xxx" -y -f mp4 -t 5 -s 1280x720 "E:/record.mp4"`
- 录像(如果花屏，指定tcp传输)
`ffmpeg -rtsp_transport tcp -i "rtsp://xxx" -y -f mp4 -t 5 -s 1280x720 "E:/record.mp4"`
- 去水印（添加水印用IrfanView）
`ffmpeg -i output.mp4 -vf "delogo=x=696:y=449:w=75:h=32" -c:a copy water1.mp4`

### ffmpeg使用

* List Devices

```bash
ffmpeg -list_devices true -f dshow -i dummy
ffmpeg -hide_banner -devices
```

* Start Recording Camera (AVI Format)

```lua
ffmpeg -f dshow -i video="USB2.0 PC CAMERA" -c:v libx264 -preset ultrafast -qp 0 output.avi
ffmpeg -f dshow -i video="USB2.0 PC CAMERA" -c:v h464 -preset ultrafast -qp 0 output.avi
ffmpeg -f dshow -i video="USB2.0 PC CAMERA" -c:v h464 -preset medium output.avi
```

* Screen Recording (Requires FFmpeg with x11grab)

```csharp
ffmpeg -f x11grab -framerate 25 -video_size 1366x768 -i :0.0 -c:v libx264 -preset ultrafast out.mp4 ffmpeg -f x11grab -framerate 25 -video_size 1366x768 -i :0.0 -c:v libx264 -preset ultrafast out.mp4
```

* 其他

```bash
ffplay -vf "scale=iw/2:ih/2" your_video.mp4

ffprobe -v error -select_streams v:0 -show_entries stream=width,height,codec_name,bit_rate,duration your_h264_file.mp4 

ffprobe -v error -show_streams -show_format out.h264

ffmpeg -re -i 720.mp4 -c:v copy -c:a copy -f rtsp rtsp://localhost:8554/live

ffplay -vf "scale=iw/2:ih/2" https://iptv.luas.edu.cn/liverespath/c70d81eefb04fef7777c2a5aab4ddc9459ce4246/0baa43f537-0-0-5bc4eda6a2031a1140906b86d867a79e/index.m3u8

ffplay -vf "scale=iw/2:ih/2" http://samples.mplayerhq.hu/V-codecs/h264/interlaced_crop.mp4

ffmpeg -re -stream_loop -1 -i .\720.mp4 -vcodec libx264 -acodec aac -f flv  rtmp://127.0.0.1:1935/live/hls              
            
```
```
查看支持的编解码器（也就是-vcodec后面可以接的参数）:
命令：ffmpeg -codecs > codec.txt


查看支持的封装格式（也就是-f后面可以接的参数）
命令：ffmpeg -formats > formats.txt

查看支持的滤镜（也就是-vf后面可以接的参数）:
命令：ffmpeg -filters > filters.txt
```

## 其他
- https://github.com/xufuji456/FFmpegAndroid
- https://github.com/tanersener/mobile-ffmpeg