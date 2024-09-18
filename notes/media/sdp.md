
## SDP 详细介绍

**SDP 主要包括以下信息：**

````
>会话的名称与目的
>会话的存活时间
>会话中的媒体信息，这是最主要的，它又包括以下内容：
>   - 媒体类型
>   - 媒体格式
>   - 传输协议
>   - 传输的IP和端口

````

**SDP 的格式**

````
SDP是由多个<type>=<value>组成的。
其中<type>是一个字符， <value>是一个字符串。需要特别注意的是，=两边是不能有空格的。

SDP会话描述由一个会话级描述（session_level description）和多个媒体级描述（media_level description）组成。

会话级（session_level）的作用域是整个会话。其位置是从’v=’行开始到第一个媒体描述为止。

媒体级（media_level）描述是对单个的媒体流进行描述，其位置是从’m=’行开始到下一个媒体描述为止。

总之，除非媒体部分重载，会话级的值是各个媒体的缺省默认值。

````

**参数结构**

````
Version（必选）
v=0 SDP的版本号，不包括次版本号。

origion（必选）
o=<username> <session id> <version> <network type> <address type> <address>

“o=”项对会话的发起者进行了描述。
<username>是用户的登录名。如果主机不支持<username>，则为 ”－” 。
注意：<username>不能含空格。

<session id>：是一个数字串。在整个会话中，必须是唯一的。为了确保其唯一，建议使用NTP(Network Time Protocol) timestamp。
<version>：该会话公告的版本,供公告代理服务器检测同一会话的若干个公告中哪个是最新公告。基本要求是会话数据修改后该版本值递增,建议用NTP时戳。
<network type>：网络类型，一般为”IN”,表示”internet”
<address type>：地址类型，一般为IP4
<address>：地址
Session Name（必选）
s=<session name> 会话名，在整个会话中有且只有一个”s=”。

Connection Data（可选）
c=<network type> <address type> <connection address>

表示媒体连接信息。 一个会话声明中，会话级描述中必须有”c=”项或者在每个媒体级描述中有一个”c=”项。
可能在会话级描述和每个媒体级描述中都有”c=”项。

<network type>：网络类型，一般为”IN”,表示”internet”
<address type>：地址类型，一般为IP4。
<connection address>：应用程序必须处理域名和ip地址两种情形。
单播时，为域名或ip地址，推荐使用域名；
多播时，为ip地址，且ip后面必须有TTL（取值范围是0－255）。地址和TTL决定了多播包被传播的范围，例： c=IN IP4 224.2.1.1/127。分层编码方案是一个数据流被分为多层，接受者能够通过申请不同层的流选择流的质量。如下：<base multicast address>/<ttl>/<number of addresses> 如果<number of addresses>没有给定，则默认为1。 c=IN IP4 224.2.1.1/127/3 等价于： c=IN IP4 224.2.1.1/127 c=IN IP4 224.2.1.2/127 c=IN IP4 224.2.1.3/127

Bandwidth（可选）
b=<modifier>:<bandwidth-value>

描述了建议的带宽，单位kilobits per second，可选。

<modifier>：包括两种CT和AS。CT：Conference Total，总带宽。AS：Application-Specific Maximum，单个媒体带宽的最大值。 扩展机制：<modifier>以”X－”开始。建议modifier越短越好。例 b=X-YZ:128
Times（必选）
t=<start time> <stop time>

描述了会话的开始时间和结束时间。 <start time> 和<stop time> 为NTP时间，单位是秒。假如<stop time>为零表示过了<start time>时间后会话一直持续。当<start time> 和<stop time>均为零时表示持久会话。

建议start time和stop time不要设为0。因为不知道此会话的开始和结束时间，增加了调度（scheduling）的难度。

Media Announcements （必选）
m=<media> <port> <transport> <fmt list>

一个会话描述包括几个媒体描述。一个媒体描述以”m=”开始到下一个”m=”结束。

<media>：表示媒体类型。有"audio", "video", "application"（例白板信息）, "data"（不向用户显示的数据） 和"control"（描述额外的控制通道）。

<port>：媒体流发往传输层的端口。取决于c=行规定的网络类型和接下来的传送层协议：对UDP为1024-65535；对于RTP为偶数。

当分层编码流被发送到一个单播地址时，需要列出多个端口。方式如下： m=<media> <port>/<number of ports> <transport> <fmt list> 对于RTP，偶数端口被用来传输数据，奇数端口用来传输RTCP包。例： m=video 49170/2 RTP/AVP 31 端口49170和49171为第一对RTP/RTCP端口，49172和49173为第二对的端口。传输协议是RTP/AVP，媒体格式为31。

<transport>：传输协议，与c=行的地址类型有关。两种： RTP/AVP，表示Realtime Transport Protocol using the Audio/Video profile carried over UDP；UDP。

<fmt list>：媒体格式。对于音频和视频就是在RTP Audio/Video Profile定义的负载类型(payload type)。但第一个为缺省值，分为静态绑定和动态绑定：静态绑定即媒体编码方式与RTP负载类型有确定的一一对应关系，动态绑定即媒体编码方式（如时钟频率，音频信道数等）没有完全确定，需要进一步的属性说明（用rtpmap）。

分别举例如下：
静态绑定的例子：u_law的PCM编码单信道Audio，采样率8KHZ。在RTP Audio/Video profile中对应的payload type为0。即： m=audio 49232 RTP/AVP 0

动态绑定的例子：16位线形编码，采样率为16KHZ，假如我们希望动态RTP/AVP 类型98表示此此流，写法如下： m=video 49232 RTP/AVP 98 a=rtpmap:98 L16/16000/2

rtpmap（可选）
a=rtpmap:<payload type> <encoding name>/<clock rate>[/<encodingparameters>]

a=rtpmap:<负载类型><编码名>/<时钟速率>[/<编码参数>]

对于音频流，<编码参数>说明了音频的通道数。通道数默认缺省值为1。
对于视频流，现阶段没有<编码参数>。
m=audio 49230 RTP/AVP 96 97 98 a=rtpmap:96 L8/8000 a=rtpmap:97 L16/8000 a=rtpmap:98 L16/11025/2

在rtpmap中，实验性的编码方案也可以用。其格式名前一定为”X－”例：一种新的实验性的被称为GSMLPC的音频流，使用的动态负载类型为99。 m=video 49232 RTP/AVP 99 a=rtpmap:99 X-GSMLPC/8000 9．Suggested Attributes（可选） a=<TYPE>或 a=<TYPE>:<VALUES> a=framerate:<帧速率>//单位:帧/秒 a=lang:<语言标记>//会话描述的缺省语言或媒体描述的语言

注： 如果SDP语法分析器不能识别某一类型(Type),则整个描述丢失。 如果”a=”的某属性值不理解,则予以丢失此属性。 会话级的描述就是媒体级描述的。

````

```java
Session description

v= (protocol version)
o= (owner/creator and session identifier).
s= (session name)
i=* (session information)
u=* (URI of description)
e=* (email address)
p=* (phone number)
c=* (connection information - not required if included in all media)
b=* (bandwidth information)
z=* (time zone adjustments)
k=* (encryption key)
a=* (zero or more session attribute lines)

Time description
t= (time the session is active)
r=* (zero or more repeat times)

Media description
m= (media name and transport address)
i=* (media title)
c=* (connection information - optional if included at session-level)
b=* (bandwidth information)
k=* (encryption key)
a=* (zero or more media attribute lines)

```