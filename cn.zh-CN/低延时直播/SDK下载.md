SDK下载 
==========================



本文提供低延时直播RTS拉流端网络SDK（Android、iOS、Web）的下载。

移动端RTS 网络SDK下载 
-----------------------------------



|   平台    |  版本号  |                                                                 完整版下载地址                                                                 |                                                                       裁剪版下载地址                                                                       |
|---------|-------|-----------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| iOS     | 1.3.0 | [点击下载](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/iOS_rts_sdk_version1.3.0_data9.29.zip)     | [点击下载](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/Android_rts_sdk_version1.3.0_extsslcurl_data10.14.zip) |
| Android | 1.3.0 | [点击下载](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/Android_rts_sdk_version1.3.0_data9.29.zip) | [点击下载](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/iOS_rts_sdk_version1.3.0_extsslcurl_data10.14.zip)     |



注：

1、裁剪版本是需要依赖外部的openssl和curl库的，这样可以有效减少包体积，但是不能配合阿里云播放器sdk使用。更多版本信息请通过提工单咨询。

2、支持maven 和 pod 依赖，集成方法参看[移动端集成文档](/cn.zh-CN/低延时直播/移动端集成文档.md)。

移动端RTS 网络SDK发布历史 
-------------------------------------



|  版本   |     日期     |                                         说明                                          |
|-------|------------|-------------------------------------------------------------------------------------|
| 1.3.0 | 2020.09.29 | 1、独立发版 2、实时状态回调 3、错误码整理 4、修复部分稳定性问题 |





直播移动端RTS播放器已和点播播放器合并，您可以直接参考点播播放器文档。[播放器SDK产品说明](https://help.aliyun.com/document_detail/125579.html)。Web端RTS播放器单独提供，请参考下面说明文档。

客户端播放器SDK下载 
--------------------------------



|    客户端    |                                     说明文档                                      |                                                                           下载地址                                                                            |
|-----------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| iOS下载     | [集成ARTC](https://help.aliyun.com/document_detail/134720.html) | [5.1.5](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/playVideo/5.1.5/ApsaraVideo_videoPlay_v5.1.5_iOS_20200721.zip)        |
| Android下载 | [集成ARTC](https://help.aliyun.com/document_detail/134721.html) | [5.1.5](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/playVideo/5.1.5/ApsaraVideo_videoPlay_v5.1.5_Android_20200722.zip)    |
| Web下载     | [集成ARTC](https://help.aliyun.com/document_detail/177370.html) | [1.2.2，](https://g.alicdn.com/AliRTC/H5RTSSdk/1.2.2/aliyun-rts-sdk.js)[npm](https://www.npmjs.com/package/aliyun-rts-sdk) |



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


