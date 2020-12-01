SDK download 
=================================

This topic provides links for you to download Real-Time Streaming (RTS) SDKs for Android, iOS, and web.

Notes 
--------------------------

* RTS SDKs support Maven and pod dependencies. For more information about how to integrate RTS SDKs, see [Integrate RTS SDKs for mobile clients]().

  

* RTS SDKs for mobile clients support a variety of players on mobile clients. When you use an RTS SDK for mobile clients, we recommend that you use ApsaraVideo Player of a version that matches the RTS SDK. For more information, see [ApsaraVideo Player SDK](https://help.aliyun.com/document_detail/125579.html).

  

* RTS SDKs for mobile clients do not support web browsers. RTS provides a dedicated RTS player SDK for web. For more information, see the ["Download RTS player SDK for web"](#section-mgw-9so-1zb) section of this topic.

  




Download RTS SDKs for mobile clients 
---------------------------------------------------------



| Release date | Version |                                                                                                                                                                Description                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       Download link                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                        Supported ApsaraVideo Player version                                                                                                                                                                                                                        |
|--------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 2020-11-05   | V1.4.0  | * Freezing is reduced in specific scenarios.   * Pure audio or video streams can be pulled.   * The buffer size can be adjusted by using the API.                                                                      | * [Complete RTS SDK for iOS](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/iOS_rts_sdk_version1.4.0_data11.05.zip)   * [Complete RTS SDK for Android]( https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/Android_rts_sdk_version1.4.0_data11.05.zip)   * [Tailored RTS SDK for iOS](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/iOS_rts_sdk_version1.4.0_extsslcurl_data11.05.zip)   * [Tailored RTS SDK for Android](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/Android_rts_sdk_version1.4.0_extsslcurl_data11.05.zip)    **Note** Tailored RTS SDKs depend on external OpenSSL and cURL libraries to reduce the package size. However, tailored RTS SDKs do not support ApsaraVideo Player SDKs. To obtain the latest information about versions, submit a ticket. | V5.2.1 and later Limits: * For Android, you must use AlivcArtc [V5.2.1p](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/AlivcArtc-5.2.1p.aar).   * For iOS, you must use artcSource [V5.2.1p](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.4.0/artcSource-5.2.1p.framework.zip).    |
| 2020-09-29   | V1.3.0  | * This version is separately released.   * Callbacks of real-time status are supported.   * Comprehensive and unified error codes are provided.   * Stability issues are resolved.    | * [Complete RTS SDK for iOS](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/iOS_rts_sdk_version1.3.0_data9.29.zip)   * [Complete RTS SDK for Android](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/Android_rts_sdk_version1.3.0_data9.29.zip)   * [Tailored RTS SDK for iOS](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/iOS_rts_sdk_version1.3.0_extsslcurl_data10.14.zip)   * [Tailored RTS SDK for Android](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/1.3.0/Android_rts_sdk_version1.3.0_extsslcurl_data10.14.zip)                                                                                                                                                                                                                                                 | V5.2.1 and later                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |



Download ApsaraVideo Player SDK for mobile clients 
-----------------------------------------------------------------------



| Client  |                                                                   Release notes                                                                   |                               Download link                               |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|
| iOS     | [Release notes of ApsaraVideo Player SDK for iOS](/intl.en-US/SDK Downloads/player-sdk-new-history/Player SDK for iOS.md)         | [SDK download](/intl.en-US/SDK Downloads/SDK download.md) |
| Android | [Release notes of ApsaraVideo Player SDK for Android](/intl.en-US/SDK Downloads/player-sdk-new-history/Player SDK for Android.md) | [SDK download](/intl.en-US/SDK Downloads/SDK download.md) |



Download RTS player SDK for web 
----------------------------------------------------



| Release date | Version |                                                             Update                                                             |                                     Download link                                      |                                 npm                                 |
|--------------|---------|--------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| 2020-11-17   | V1.2.3  | Parameter settings are supported to pull audio-only or video-only streams.                                                     | [V1.2.3](https://g.alicdn.com/AliRTC/H5RTSSdk/1.2.3/aliyun-rts-sdk.js) | [npm](https://www.npmjs.com/package/aliyun-rts-sdk) |
| 2020-10-10   | V1.2.2  | Failures of importing npm packages are fixed.                                                                                  | [V1.2.2](https://g.alicdn.com/AliRTC/H5RTSSdk/1.2.2/aliyun-rts-sdk.js) | -                                                                   |
| 2020-09-09   | V1.2.1  | DingTalk browser for iOS is supported. Failures of returning correct error codes are fixed. The onPlayEvent callback is added. | [V1.2.1](https://g.alicdn.com/AliRTC/H5RTSSdk/1.2.1/aliyun-rts-sdk.js) | -                                                                   |
| 2020-08-05   | V1.1.0  | The first version of RTS player SDK for web is provided with the feature of RTS-based stream pulling.                          | [V1.1.0](https://g.alicdn.com/AliRTC/H5RTSSdk/1.1.0/aliyun-rts-sdk.js) | -                                                                   |


