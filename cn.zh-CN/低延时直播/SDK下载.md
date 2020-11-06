SDK下载 
==========================



本文提供低延时直播RTS拉流端网络SDK（Android、iOS、Web）的下载。

移动端RTS 网络SDK下载 
-----------------------------------




|  版本   |                                       发布说明                                        |                                                                                                                                                                                                                                                                                                                          下载地址                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                              阿里云播放器的版本要求                                                                                                                                                              |
|-------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1.4.0 | 1、特定场景的卡顿优化 2、支持纯音频/纯视频 拉流 3、支持外部调整缓存Buffer       | [iOS完整版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/iOS_rts_sdk_version1.4.0_data11.05.zip) [Android完整版本]( https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/Android_rts_sdk_version1.4.0_data11.05.zip) [iOS裁剪版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/iOS_rts_sdk_version1.4.0_extsslcurl_data11.05.zip) [Android裁剪版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/Android_rts_sdk_version1.4.0_extsslcurl_data11.05.zip) | 5.2.1 及以上版本 (其中Android 的[AlivcArtc](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/AlivcArtc-5.2.1p.aar)和iOS 的[artcSource](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/artcSource-5.2.1p.framework.zip)需要使用5.2.1p版本。同样支持maven和pod依赖） |
| 1.3.0 | 1、独立发版 2、实时状态回调 3、错误码整理 4、修复稳定性问题 | [iOS完整版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/iOS_rts_sdk_version1.3.0_data9.29.zip) [Android完整版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/Android_rts_sdk_version1.3.0_data9.29.zip) [iOS裁剪版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/iOS_rts_sdk_version1.3.0_extsslcurl_data10.14.zip) [Android裁剪版本](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/Android_rts_sdk_version1.3.0_extsslcurl_data10.14.zip)    | 5.2.1 及以上版本                                                                                                                                                                                                                                                                                                                           |



注：

1、裁剪版本是需要依赖外部的openssl和curl库的，这样可以有效减少包体积，但是不能配合阿里云播放器sdk使用。更多版本信息请通过提工单咨询。

2、支持maven 和 pod 依赖，集成方法参看[移动端集成文档](/cn.zh-CN/低延时直播/移动端集成文档.md)。

3、RtsSDK配合阿里云播放器sdk使用更加方便，需要符合版本对应关系。[播放器SDK产品说明](https://help.aliyun.com/document_detail/125579.html)。Web端RTS播放器单独提供，请参考下面说明文档。

移动端 播放器SDK 发布历史 
------------------------------------



|   客户端   |                                          发布历史                                           |
|---------|-----------------------------------------------------------------------------------------|
| iOS     | [iOS播放器SDK发布历史](https://help.aliyun.com/document_detail/94428.html)     |
| Android | [Android播放器SDK发布历史](https://help.aliyun.com/document_detail/94328.html) |



Web 播放器SDK 发布历史 
------------------------------------



|     日期     |  版本   |                    修改内容                    |                                                                           下载链接                                                                            |
|------------|-------|--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| 2020-10-10 | 1.2.2 | 修复npm引入失败问题                                | [1.2.2，](https://g.alicdn.com/AliRTC/H5RTSSdk/1.2.2/aliyun-rts-sdk.js)[npm](https://www.npmjs.com/package/aliyun-rts-sdk) |
| 2020-09-09 | 1.2.1 | 增加ios端钉钉浏览器支持，修复错误码抛出错误的问题，增加onPlayEvent回调 | [1.2.1，](https://g.alicdn.com/AliRTC/H5RTSSdk/1.2.1/aliyun-rts-sdk.js)[npm](https://www.npmjs.com/package/aliyun-rts-sdk) |
| 2020-08-05 | 1.1.0 | RTS Web播放器初版，具备RTS低延时直播协议拉流的能力             | [1.1.0，](https://g.alicdn.com/AliRTC/H5RTSSdk/1.1.0/aliyun-rts-sdk.js)[npm](https://www.npmjs.com/package/aliyun-rts-sdk) |


