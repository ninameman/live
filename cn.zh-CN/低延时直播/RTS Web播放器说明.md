RTS Web播放器说明 {#title-yl0-lp5-krn}
=================================

{#shortdesc-yuu-9hj-xsc}

概述 {#title-ywc-12e-nqq}
-----------------------

RTS Web SDK是通过HTML网页加载的JavaScript 库，不包含普通直播Web播放器功能，此SDK只用于RTS低延时直播协议拉流。可以解决在手机浏览器、微信浏览器和PC浏览器上播放音视频流的问题，可以不依赖用户安装 App实现直播播放，本文档适合有一定 Javascript 语言基础的开发人员阅读。SDK视频播放能力本身不是网页代码实现的，而是靠浏览器支持，因此不是所有的浏览器都能有符合预期的表现，其兼容性参考下文建议。

{#p-byc-g2r-qgr}

兼容性说明 {#title-zyt-55m-2jd}
--------------------------

{#p-qg2-rae-i17}{#thead-zcs-z2z-g5q}{#p-b0w-vum-91d}{#p-cde-l3h-f7s}{#p-igg-f3f-lec}{#p-75u-scc-ufg}{#p-svz-g3z-kmn}{#p-o0i-1ix-zci}{#p-kwa-sav-2hy}{#p-ag4-iqv-tiu}{#p-511-pnn-u6d}{#p-6wp-r0b-g6l}{#p-tdn-jbd-hd3}{#tbody-81o-m8z-tzv}

|   平台    |   浏览器   | 最低支持版本 |
|---------|---------|--------|
| Windows | Chrome  | 63     |
|         | Firefox | 62     |
|         | Opera   | 15     |
| Mac     | Chrome  | 63     |
|         | Safari  | 11     |
|         | Firefox | 62     |
|         | Opera   | 15     |
| Android | Chrome  | 63     |
|         | 微信浏览器   | 7.0.9  |
| iOS     | Safari  | 11     |
|         | 微信浏览器   | 7.0.9  |

{#table-z44-861-fzx}

{#p-n6p-ybc-hwq}

使用说明 {#title-v2x-rek-7ek}
-------------------------

接入方法 {#h2-7em-uup-qlv}
----------------------

**1、实例化** {#p-r9j-bu0-tz5}

    var aliRts = new AliRTS()

{#codeblock-8i3-s6f-lrw}

**2、isSupport检测浏览器是否可用** {#p-ly3-l6m-hum}

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

{#codeblock-a2c-xs0-f1b}

**3、RTS开始拉流** {#p-m4i-1cl-8xu}

    /** 
     * rts开始拉流接口 
     * @param {String} pullStreamUrl 拉流地址 
     * @param {HTMLMediaElement|null} mediaElement 播放视频的video标签 
     * @return {Promise}  
     */ 
    aliRts.startLiveStream(pullStreamUrl, mediaElement);

{#codeblock-8yp-14b-zme}

**4、RTS停止播放** {#p-l3k-f3s-bx1}

    /** 
     * 停止rts播放接口 
     */ 
    aliRts.stopLiveStream();

{#codeblock-klb-tu3-0oi}

**5、静音接口** {#p-1es-49c-67k}

    /** 
     * 拉流静音接口 
     * @param {Boolean} muted 是否开启静音 
     */ 
    aliRts.muteLiveStream(muted);

{#codeblock-mde-nzo-xgr}

{#p-7zo-zi8-9jg}

注：1、由于浏览器策略问题，https协议无法正常加载http资源，所以https协议链接的拉流地址必须也是https(如果使用http也同理，拉流地址也需要是http)。{#p-5yr-lxl-lqb}

错误码 {#h2-iy9-qzl-2jn}
---------------------

{#p-q4o-2dk-e6u}{#thead-zxb-rxw-if6}{#p-kte-yj4-vmt}{#p-oyg-3ey-flm}{#p-n3q-i4a-t3n}{#p-euv-o15-cuc}{#p-s5y-z87-rag}{#p-skr-5gv-our}{#p-ppj-ohy-i4a}{#tbody-7sa-epq-dqq}

| 错误码 （errorCode） |      错误信息（message）      |       描述        |
|-----------------|-------------------------|-----------------|
| 10001           | http request error      | 信令请求失败          |
| 10010           | not support webrtc      | 不支持webrtc       |
| 10011           | browser version too low | 浏览器版本过低         |
| 10012           | browser not support     | 不支持此浏览器         |
| 10013           | not support h264        | 不支持H264         |
| 10014           | create offer error      | create offer 失败 |
| 10201           | auto play failed        | 自动播放失败          |

{#table-jgb-wv4-ptt}

