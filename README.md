# Jrtplib4Android
基于开源项目jrtplib，自主编译出jni依赖库，在Android平台上实现RTP/RTCP数据接收、发送等示例。（包含H264数据分包发送）

本人采用的是android-ndk-r14b，并不是as自带的。（自带的会出现各种异常）

## jni目录编译项目
### 接收端实现的功能：
  1、接收rtp数据，回调数据至java(目前只有byte[],length,isMarker,可根据需求自行修改)；<br>
  2、接收rtcp、bye命令等，回调至java,通过自定义的int值type来区分，同时传递了数据发送端的IP字符串。
  
### 发送端实现的功能：
  1、实现FU-A分包发送H264数据；<br>
  2、实现发送RTP数据；<br>
  3、实现接收rtcp、bye命令等，回调至java,通过自定义的int值type来区分，同时传递了数据发送端的IP字符串。
  
## app项目是实际应用项目
  1、Android实现采集摄像头数据，异步编码为H264数据，通过jni发送至指定接收端；<br>
  2、实现网络摄像机RTSP协议对接（单通道视频流）；<br>
  3、实现接收RTSP服务端的RTP数据，转发至指定接收端。（项目使用是局域网接收摄像机，通过Android手机传递至公网服务器）；
  
## 使用方法
  RtpHandle是jni操作对象。<br>
    initSendHandle方法适用于只发送数据；<br>
    initReceiveHandle方法适用于只接收数据；<br>
    initReceiveAndSendHandle方法适用于接收并转发数据；
