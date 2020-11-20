SDK下载 
==========================

本文提供低延时直播RTS SDK（Android、iOS、Web）的下载。

RTS SDK说明 
------------------------------

* RTS SDK支持maven和pod依赖，集成方法请参见[移动端集成文档](/cn.zh-CN/低延时直播/移动端集成文档.md)。

  

* 对于移动端，移动端RTS SDK支持配合多种播放器使用，推荐配合阿里云播放器使用，需要符合版本对应关系。更多信息，请参见[播放器SDK产品说明](https://help.aliyun.com/document_detail/125579.html)。

  

* 对于Web端，不支持移动端RTS SDK，低延时直播单独提供了RTS Web播放器SDK，请参见[RTS Web播放器SDK下载](#section-mgw-9so-1zb)。

  




移动端RTS SDK下载 
---------------------------------



|     日期     |   版本   |                                                                                              发布说明                                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                                             下载地址                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                                                                                                                                                                              阿里云播放器版本要求                                                                                                                                                                                                               |
|------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 2020-11-05 | V1.4.0 | * 特定场景的卡顿优化   * 支持纯音频/纯视频拉流   * 支持外部调整缓存Buffer                              | * [iOS完整版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/iOS_rts_sdk_version1.4.0_data11.05.zip)   * [Android完整版本]( https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/Android_rts_sdk_version1.4.0_data11.05.zip)   * [iOS裁剪版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/iOS_rts_sdk_version1.4.0_extsslcurl_data11.05.zip)   * [Android裁剪版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/Android_rts_sdk_version1.4.0_extsslcurl_data11.05.zip)    **说明** 裁剪版本是需要依赖外部的openssl和curl库的，这样可以有效减少包体积，但是不能配合阿里云播放器SDK使用。更多版本信息请通过提工单咨询。 | V5.2.1及以上版本 其中要求： * Android的AlivcArtc：[V5.2.1p](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/AlivcArtc-5.2.1p.aar)   * iOS的artcSource：[V5.2.1p](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/artcSource-5.2.1p.framework.zip)    |
| 2020-09-29 | V1.3.0 | * 独立发版   * 实时状态回调   * 错误码整理   * 修复稳定性问题    | * [iOS完整版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/iOS_rts_sdk_version1.3.0_data9.29.zip)   * [Android完整版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/Android_rts_sdk_version1.3.0_data9.29.zip)   * [iOS裁剪版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/iOS_rts_sdk_version1.3.0_extsslcurl_data10.14.zip)   * [Android裁剪版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/Android_rts_sdk_version1.3.0_extsslcurl_data10.14.zip)                                                                                       | V5.2.1及以上版本                                                                                                                                                                                                                                                                                                                                                                                                                           |



移动端 播放器SDK下载 
---------------------------------



|   客户端   |                                       发布历史                                       |                       下载地址                        |
|---------|----------------------------------------------------------------------------------|---------------------------------------------------|
| iOS     | [iOS播放器SDK发布历史](/cn.zh-CN/SDK下载/播放器SDK发布历史/iOS播放器SDK.md)         | [SDK下载](/cn.zh-CN/SDK下载/SDK下载.md) |
| Android | [Android播放器SDK发布历史](/cn.zh-CN/SDK下载/播放器SDK发布历史/Android播放器SDK.md) | [SDK下载](/cn.zh-CN/SDK下载/SDK下载.md) |



RTS Web播放器SDK下载 
------------------------------------



|     日期     |   版本   |                    修改内容                    |                                          下载链接                                          |                                 npm                                 |
|------------|--------|--------------------------------------------|----------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| 2020-11-17 | V1.2.3 | 支持参数设置拉纯音频或纯视频流                            | [V1.2.3](https://g.alicdn.com/AliRTC/H5RTSSdk/1.2.3/aliyun-rts-sdk.js) | [npm](https://www.npmjs.com/package/aliyun-rts-sdk) |
| 2020-10-10 | V1.2.2 | 修复npm引入失败问题                                | [V1.2.2](https://g.alicdn.com/AliRTC/H5RTSSdk/1.2.2/aliyun-rts-sdk.js) | -                                                                   |
| 2020-09-09 | V1.2.1 | 增加ios端钉钉浏览器支持，修复错误码抛出错误的问题，增加onPlayEvent回调 | [V1.2.1](https://g.alicdn.com/AliRTC/H5RTSSdk/1.2.1/aliyun-rts-sdk.js) | -                                                                   |
| 2020-08-05 | V1.1.0 | RTS Web播放器初版，具备RTS低延时直播协议拉流的能力             | [V1.1.0](https://g.alicdn.com/AliRTC/H5RTSSdk/1.1.0/aliyun-rts-sdk.js) | -                                                                   |


