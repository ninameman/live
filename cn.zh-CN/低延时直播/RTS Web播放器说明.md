RTS Web播放器说明 
=================================



概述 
-----------------------

RTS Web SDK是通过HTML网页加载的JavaScript 库，不包含普通直播Web播放器功能，此SDK只用于RTS低延时直播协议拉流。可以解决在手机浏览器、微信浏览器和PC浏览器上播放音视频流的问题，可以不依赖用户安装 App实现直播播放，本文档适合有一定 Javascript 语言基础的开发人员阅读。SDK视频播放能力本身不是网页代码实现的，而是靠浏览器支持，因此不是所有的浏览器都能有符合预期的表现，其兼容性参考下文建议。



兼容性说明 
--------------------------



|   平台    |   浏览器   |   最低支持版本    |
|---------|---------|-------------|
| Windows | Chrome  | 63          |
|         | Firefox | 62          |
|         | Opera   | 15          |
| Mac     | Chrome  | 63          |
|         | Safari  | 11          |
|         | Firefox | 62          |
|         | Opera   | 15          |
| Android | Chrome  | 63          |
|         | 微信浏览器   | 7.0.9       |
| iOS     | Safari  | 11          |
|         | 微信浏览器   | 7.0.9       |
|         | 钉钉浏览器   | 系统版本号11.2.5 |





使用说明 
-------------------------

接入方法 
----------------------

**1、实例化** 

    var aliRts = new AliRTS()



**2、isSupport检测浏览器是否可用** 

    /** 
     * isSupport检测是否可用 
     * @param {Object} supportInfo 检测信息 
     * @param {Boolean} supportInfo.isReceiveVideo 是否拉视频流 
     * @return {Promise}  
     */ 
    aliRts.isSupport(supportInfo).then(re=> { 
        // 可用 
    }).catch(err=> { 
      // 不可用 
      console.log(`not support errorCode: ${err.errorCode}`); 
      console.log(`not support message: ${err.message}`); 
    })



**3、RTS开始拉流** 

    /** 
     * rts开始拉流接口 
     * @param {String} pullStreamUrl 拉流地址 
     * @param {HTMLMediaElement|null} mediaElement 播放视频的video标签 
     * @return {Promise}  
     */ 
    aliRts.startLiveStream(pullStreamUrl, mediaElement);



**4、RTS停止播放** 

    /** 
     * 停止rts播放接口 
     */ 
    aliRts.stopLiveStream();



**5、静音接口** 

    /** 
     * 拉流静音接口 
     * @param {Boolean} muted 是否开启静音 
     */ 
    aliRts.muteLiveStream(muted);



**6、回调监听** 

    /*
     * 在onError中获取到错误码10201时，此时网页的音频是静音的，
     * 需要用户在网页上手动触发事件（必须有用户交互，不能直接通过代码控制）
     * 调用aliRts.muteLiveStream(false) 来取消静音
     */
    aliRts.on("onError", (err)=> {
      console.log(`errorCode: ${err.errorCode}`);
      console.log(`message: ${err.message}`);
    })
    
    const PLAY_EVENT = {
      CANPLAY: "canplay",
      WAITING: "waiting",
      PLAYING: "playing"
    }
    
    aliRts.on('onPlayEvent', (play)=>{
      if(play.event === PLAY_EVENT.CANPLAY){
        // 拉流可以播放
      }else if(play.event === PLAY_EVENT.WAITING){
        // 拉流卡顿等待缓冲中 （仅Chrome）
      }else if(play.event === PLAY_EVENT.PLAYING){
        // 拉流卡顿结束恢复播放 （仅Chrome）
      }
    })





注：1、由于浏览器策略问题，https协议无法正常加载http资源，所以https协议链接的拉流地址必须也是https(如果使用http也同理，拉流地址也需要是http)。

错误码 
---------------------



| 错误码 （errorCode） |      错误信息（message）      |       描述        |
|-----------------|-------------------------|-----------------|
| 10001           | http request error      | 信令请求失败          |
| 10010           | not support webrtc      | 不支持webrtc       |
| 10011           | browser not support     | 不支持此浏览器         |
| 10012           | browser version too low | 浏览器版本过低         |
| 10013           | not support h264        | 不支持H264         |
| 10014           | create offer error      | create offer 失败 |
| 10201           | auto play failed        | 自动播放失败          |



