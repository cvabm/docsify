- [android编解码](#android编解码)


### RTP/H264开源项目
Android端的：
- https://github.com/qfsun/Jrtplib4Android 
- https://github.com/zhuohengfeng/Camera2Rtmp camera->rtmp
- https://github.com/dourgulf/CameraStreaming camera->rtmp
- https://github.com/JeffreyLau/AndroidRTSPLib camera/screen/mp4_file -> rtsp
- https://github.com/pedroSG94/RootEncoder 推送android摄像头/屏幕共享到RTMP, RTSP, SRT and UDP(没有RTP)
- https://github.com/Consti10/LiveVideo10ms 播放RTP或RAW中的udp的h264
- https://github.com/xcy396/MediaCodecDemo 使用 MediaCodec、jlibrtp 实现实时视频通话
- https://github.com/ChangeStrong/AndroidDemo 将摄像头yuv转H264
- https://github.com/mjlong123123/VideoRecorder 录屏发送到rtp，没验证过
- https://github.com/TomAdd/RTPServerDemo android端
- https://github.com/lxz2014/rtp_h264 android端，只编不发
- https://github.com/junerver/TestCaptureAndRecord websoket收发
- https://github.com/niezhiyang/TouPing websoket收发
- https://github.com/feifei2020/ffmpegrtmppusher 
- https://github.com/yrom/ScreenRecorder android录屏
- https://github.com/sszhangpengfei/AndroidShow
其他  
- https://github.com/licaibiao/v4l2_video_audio_encode_live c++
- https://github.com/tong123/rtp_stream
- https://github.com/tinydigger/RTPH264Streaming
- https://github.com/MontaukLaw/hisiv3518e
- https://github.com/z80020100/RKModules
- https://github.com/yundiantech/ScreenShare
- https://github.com/PanPersonalProject/RtspAndroid
- https://github.com/ChangeStrong/AndroidDemo
- https://github.com/mjlong123123/VideoRecorder
- https://github.com/ty6815/AvStackDocs
- https://github.com/Yang-Jianlin/Android_HK 基于海康sdk
- https://github.com/shenshuyu/es2ps  将h264流打包成ps流
- https://github.com/debugger999/gb28181ToH264 c++ 作为上级域，可以对接海康、大华、宇视等gb28181平台
### RTP开源库
- ORTP c
- JRTPLIB c++
- jlibrtp java

### B帧
官方的profile配置不管用  
https://developer.android.com/media/optimize/sharing?authuser=1&hl=zh-cn#b-frames_and_encoding_profiles
```
format.setInt32(KEY_PROFILE, AVCProfileHigh);
format.setInt32(KEY_LATENCY, 1);
```
### 调试
- vlc播放rtp流
  -  新建文件11.sdp，内容如下，用vlc打开即可播放：
```
m=video 6666 RTP/AVP 96
a=rtpmap:96 H264
a=framerate:20
c=IN IP4 10.166.10.8
```
### mediacodec
- 创建编解码器的两种方式
  - `MediaCodec.createEncoderByType("video/avc")`
  - `MediaCodec.createByCodecName("OMX.Nvidia.h264.encoder")`
##   udp/h264发送
- udp不能发送大于1472字节数据,一般设为1400
- 先发sps\pps
- 通过sps查看视频分辨率
```
.000 0011  1100 .... = pic_width_in_mbs_minus1: 59
.... 0000  0101 101. = pic_height_in_map_units_minus1: 44
```
- `X = (59+1)*16 = 960，Y = (44+1)*16 = 720`

  
- https://github.com/8kEatRadish/Live555OnAndroid

## android编解码

````
软解码器：通常以OMX.google开头，或者不以OMX开头的也为软解码器
硬解码器：通常以OMX.[hardware_vendor]开头

````

````

高通软编解码
OMX.google.aac.decoder
OMX.google.amrnb.decoder
OMX.google.flac.decoder
OMX.google.g711.alaw.decoder
OMX.google.g711.mlaw.decoder
OMX.google.gsm.decoder
OMX.google.mp3.decoder
OMX.google.opus.decoder
OMX.google.raw.decoder
OMX.google.vorbis.decoder
OMX.google.aac.encoder
OMX.google.amrnb.encoder
OMX.google.amrwb.encoder
OMX.google.flac.encoder
OMX.google.h264.decoder
OMX.google.h263.decoder
OMX.google.hevc.decoder
OMX.google.mpeg4.decoder
OMX.google.vp8.decoder
OMX.google.vp9.decoder
OMX.google.h264.encoder
OMX.google.h263.encoder
OMX.google.mpeg4.encoder
OMX.google.vp8.encoder
OMX.google.aac.decoder
OMX.google.amrwb.decoder

c2.android.vp8.decoder - 2048
c2.android.vp8.encoder -2048
c2.android.vp9.decoder - 2048
c2.android.vp9.encoder -2048
OMX.qti.audio.decoder.flac
OMX.qti.video.decoder.divxsw
OMX.qti.video.decoder.divx4sw
OMX.qti.video.decoder.h263sw
OMX.qti.video.decoder.mpeg4sw
OMX.qti.video.decoder.vc1sw

````

````

高通硬解
OMX.qcom.video.decoder.avc - 264
OMX.qcom.video.decoder.hevc -265
OMX.qcom.video.decoder.mpeg2
OMX.qcom.video.decoder.vp8 -2304
OMX.qcom.video.decoder.vp9 -4320
高通硬编
OMX.qcom.video.encoder.heic
OMX.qcom.video.encoder.avc -h264
OMX.qcom.video.encoder.h263sw
OMX.qcom.video.encoder.hevc -h265
OMX.qcom.video.encoder.hevc.cq
OMX.qcom.video.encoder.mpeg4sw -720
OMX.qcom.video.encoder.vp8 -2304
海思硬编
OMX.hisi.video.encoder.avc
OMX.hisi.video.encoder.hevc
海思硬解
OMX.hisi.video.decoder.avc
OMX.hisi.video.decoder.hevc
OMX.hisi.video.decoder.mpeg2
OMX.hisi.video.decoder.mpeg4
OMX.hisi.video.decoder.vp8  -1088

````

判断是否为软解

````
frameworks/av/media/libstagefright/MediaCodecList.cpp

 bool MediaCodecList::isSoftwareCodec(const AString &componentName) {
    return componentName.startsWithIgnoreCase("OMX.google.")
            || componentName.startsWithIgnoreCase("c2.android.")
            || (!componentName.startsWithIgnoreCase("OMX.")
                    && !componentName.startsWithIgnoreCase("c2."));
}

````

相关文档

[https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/data/media_codecs_google_c2_video.xml](https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/data/media_codecs_google_c2_video.xml)

## 获取手机最大解码数量

```java

public static void printMediaCodecInfo() {

    int CodecCount = 0;
    try {
        CodecCount = MediaCodecList.getCodecCount();
    }catch (Exception e) {
        Log.e(TAG, "#### Failed to get codec count!");
        e.printStackTrace();
        return;
    }

    for (int i = 0; i < CodecCount; ++i) {
        MediaCodecInfo info = null;
        try {
            info = MediaCodecList.getCodecInfoAt(i);
        } catch (IllegalArgumentException e) {
            Log.e(TAG, "Cannot retrieve decoder codec info", e);
        }
        if (info == null) {
            continue;
        }

        String codecInfo = "MediaCodec, name="+info.getName()+", [";

        for (String mimeType : info.getSupportedTypes()) {
            codecInfo += mimeType + ",";
            MediaCodecInfo.CodecCapabilities capabilities;
            try {
                capabilities = info.getCapabilitiesForType(mimeType);
            } catch (IllegalArgumentException e) {
                Log.e(TAG, "Cannot retrieve decoder capabilities", e);
                continue;
            }

            codecInfo += " max inst:"+capabilities.getMaxSupportedInstances()+",";

            String strColorFormatList = "";
            for (int colorFormat : capabilities.colorFormats) {
                strColorFormatList += " 0x" + Integer.toHexString(colorFormat);
            }
            codecInfo += strColorFormatList + "] [";
        }

        Log.w(TAG, codecInfo);
    }

    boolean bSupportHwVP8 = MediaCodecVideoEncoder.isVp8HwSupported();
    boolean bSupportHwVP9 = MediaCodecVideoEncoder.isVp9HwSupported();
    boolean bSupportHwH264 = MediaCodecVideoEncoder.isH264HwSupported();

    String webrtcCodecInfo = "WebRTC codec support: HwVP8=" + bSupportHwVP8 + ", HwVP9=" + bSupportHwVP9
            + ", Hw264=" + bSupportHwH264;

    if(bSupportHwH264) {
        webrtcCodecInfo += ", Hw264HighProfile=" + MediaCodecVideoEncoder.isH264HighProfileHwSupported();
    }

    Log.w(TAG, webrtcCodecInfo);
}

```

### 华为对 h264 的支持

```java
webrtc内部h264只支持两种 OMX.qcom. 和 OMX.Exynos.需改以下配置即可
HardwareVideoEncoderFactory.java

   private boolean isHardwareSupportedInCurrentSdkH264(MediaCodecInfo info) {
        if (H264_HW_EXCEPTION_MODELS.contains(Build.MODEL)) {
            return false;
        } else {
            String name = info.getName();
            return name.startsWith("OMX.qcom.") && VERSION.SDK_INT >= 19 || name.startsWith("OMX.Exynos.") && VERSION.SDK_INT >= 21 || name.startsWith("OMX.google.") && VERSION.SDK_INT >= 19;
        }
    }

```