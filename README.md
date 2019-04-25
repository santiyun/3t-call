# 远程视频面签
随着社会节奏加快，传统视频客服效率较低，人力和时间成本过高的弊端逐渐显露，同时银保监会对金融行业提出了双录合规及视频留证的要求，远程视频面签基于音视频连麦，混频双录，AI辅助等手段，为客户提供高效快捷解决方案，政策合规，节约成本，满足泛金融行业服务合规要求，突破地域限制，大幅降低运营成本。

常见的几种远程视频面签类型及特点：
> 远程开户：通过手机音视频连麦，节省客户的时间和空间成本，提升客服效率。

> 保险理赔: 无需等待理赔员到达现场，远程指挥快速处理，在线办理赔付。

> 汽车信贷: 在线审核贷款资质，验明正身，签署贷款合同。

## 典型场景
客户方通过手机客户端发起在线业务视频连线申请，客服后台经过排队调度后，将业务处理分配给指定客服，客服人员通过PC客户端接通连线，开始进行业务介绍及流程处理，双方音频视频通话过程通过SDK接口进行实时混频双录，录制存档后的视频可进行点播回看。

# DEMO体验
1. 客户端下载：
   * 安卓端 https://www.pgyer.com/RGNY
   * iOS端 https://itunes.apple.com/cn/app/id1441875540?mt=8
2. 客服端下载：
   * Windows端 http://39.107.116.40/res/tpl/default/file/LiveBank2.1.5.exe

# 实现步骤

#### 准备工作
1. 在三体云官网SDK下载页 [http://3ttech.cn/index.php?menu=53]() 下载对应平台的 视频通话SDK。
2. 登录三体云官网 [http://dashboard.3ttech.cn/index/login]() 注册应用账号，进入控制台新建自己的应用并获取APPID。

#### Windows端SDK集成步骤
* 通过 [initialize]() 接口创建 3T SDK 引擎
* 设置通信模式 [setChannelProfile]()
* 启用视频通信功能 [enableVideo]()
* 打开本地视频 [setupLocalVideo]()
* 打开本地预览 [startPreview]()
* 退出房间，防止上次未退出成功 [leaveChannel]()
* 设定为主播 [setClientRole]()
* 通过 [configPublisher]() 接口设置CDN的推流地址
* 创建房间 [joinChannel]() 
* 通过 [setVideoCompositingLayout]()  设置SEI，实现录制
* 创建用户视频 [setupRemoteVideo]()
* 播放用户视频 [muteRemoteVideoStream]()
* 调整麦克风 [ConfMuteLocalAudio]()
* 开启禁用视频 [ConfMuteLocalAudio]()
* 退出房间 [leaveChannel]()
* 反初始化SDK [destroy]()
 
 #### 移动端SDK集成步骤
 * 初始化 [MyTTTRtcEngineEventHandler]() 用于接受3T SDK回调信息
* 通过 [TTTRtcEngine.create]() 接口创建 3T SDK 引擎
* 远程面签模式下需要采用SDK的通信模式 [setChannelProfile]()
* 视频模式下需要角色设定为副播 [setClientRole]()
* 视频模式下需要启用视频功能 [enableVideo]()
* 通过 [GlobalConfig.mPushUrl]() 接口设置CDN的推流地址
* 通过 [setVideoMixerParams]() 设置视频属性
* 通过 [setAudioMixerParams]() 设置音频属性
* 通过 [setVideoProfile]() 设置视频编码属性
* 通过 [enableAudioVolumeIndication]() 接口启用用户的音量上报
* 通过 [setVideoMirrored]() 设置前置摄像头镜像
* 通过 [CreateRendererView]() 创建SurfaceView
* 通过 [setupLocalVideo]() 打开手机摄像头
* 通过 [startPreview]() 打开手机摄像头预览
* 通过 [joinChannel]() 加入频道
* 通过 [setupRemoteVideo]() 打开远端视频流
* 通过 [leaveChannel]() 退出频道
 
 # 注意事项

 
