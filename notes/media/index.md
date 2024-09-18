# 音视频

- [视频播放SDK](/notes/media/player.md)
- [webrtc](/notes/media/webrtc.md)
- [sip](/notes/media/sip.md)
- [sip](/notes/media/sdp.md)
- [Windows本地搭建rtmp推流服务](https://zhuanlan.zhihu.com/p/630493216)


- https://github.com/zhongwcool/nginx-rtmp-win64 exe程序，一键开启rtmp
- https://github.com/cvabm/Send_H264_File_RTP 
    - 将本地E:/record2.h264文件分片封装为rtp发送到远端udp端口
- https://github.com/cvabm/Jrtplib4Android
    - 获取android摄像头或屏幕共享流发送到远端udp端口
- https://github.com/cvabm/JrtpLibDemo
    - 推送摄像头或屏幕共享H264数据到socket
- [28181](/notes/media/28181.md)
- https://github.com/TomAdd/RTPServerDemo android作为服务端，发送摄像头视频流给调用者
- https://github.com/dourgulf/CameraStreaming Android RTMP直播的例子
- https://github.com/JeffreyLau/AndroidRTSPLib android作为rtsp服务端

- https://github.com/ShouChenICU/WebCamera  基于WebRTC的点对点网络摄像头实时监控工具



- https://github.com/leixiaohua1020/simplest_mediadata_test  c++源码，关于对音视频数据的处理

#### 屏幕共享/投屏
- https://github.com/lesa1127/AndroidScreenShare
- https://github.com/yundiantech/ScreenShare 局域网屏幕共享 ，c++
- https://github.com/tong123/rtp_stream 基于RTP协议传输H264数据流 c++

- https://github.com/lxz2014/rtp_h264/tree/master android录屏为h264
- https://github.com/bytestar/android-h264-stream-demo 如上

- https://gitee.com/Barryda/QtScrcpy 通过 USB/网络连接,投屏+控制 (推荐)
- https://github.com/dkrivoruchko/ScreenStream 手机app开启，chrome观看
- https://github.com/Genymobile/scrcpy
- https://github.com/AkiChase/scrcpy-mask 没投屏，号称延迟低
- https://github.com/viarotel-org/escrcpy 没有menu\home等快捷键，不是很方便



#### 其他
- https://github.com/licaibiao/v4l2_video_audio_encode_live c++
- https://github.com/Consti10/LiveVideo10ms 用于在安卓设备上以超低延迟（低于10ms）播放实时视频的库。支持播放通过RAW或RTP封装的UDP传输的.h264编码的实时视频数据，以及简单的文件播放。
- https://github.com/pedroSG94/RootEncoder android完整demo，使用rtmp、rtsp、SRT和UDP协议将视频/音频推送到媒体服务器

