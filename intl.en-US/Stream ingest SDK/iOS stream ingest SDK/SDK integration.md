# SDK integration {#concept_cbx_ysw_pfb .concept}

This topic describes how to integrate the iOS stream ingest SDK.

## SDK information {#section_d4s_ctw_pfb .section}

To upgrade your SDK, you can download a stream ingest SDK package from the Alibaba Cloud official website. For more information, see [Download SDKs](intl.en-US/SDK Reference/SDK download.md#).

The directory structure of the downloaded SDK package is as follows:

-   **The SDK package with Alibaba Cloud ApsaraVideo Player** contains two stream ingest DLL files `AlivcLibRtmp.framework` and `AlivcLivePusher.framework`, a facial recognition resource file `AlivcLibFaceResource.bundle`, a player DLL file `AliyunPlayerSDK.framework`, and a player resource file `AliyunLanguageSource.bundle`.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592455905_en-US.png)

-   **The SDK package without Alibaba Cloud ApsaraVideo Player** contains two stream ingest DLL files

     `AlivcLibRtmp.framework` 

    and

     `AlivcLivePusher.framework` 

    , and a facial recognition resource file

     `AlivcLibFaceResource.bundle` 

    .

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592455906_en-US.png)

    **Note:** 

    -   The stream ingest SDK provides the background music feature. If you need this feature, you must use the SDK package with Alibaba Cloud ApsaraVideo Player. Otherwise, you can use the SDK package without Alibaba Cloud ApsaraVideo Player.

    -   The **AlivcLibFaceResource.bundle** file contains facial recognition resources. If you need the advanced facial recognition–based face filter, you must import this file into your project.

    -   Each SDK package contains two SDKs: **arm** and **arm&simulator**. You can use **arm** only for debugging on physical devices, and **arm&simulator** for debugging on physical devices and the simulator. You must use **arm** for your project to be published.


## System requirements {#section_dtd_mtw_pfb .section}

-   iOS 8.0 or a later version

-   CPU that supports ARMv7, ARMv7s, and ARM64


## Development environment {#section_b5x_mtw_pfb .section}

-   Xcode 8.0 or a later version

-   OS X 10.10 or a later version


## Import the SDK {#section_svj_3vw_pfb .section}

-   Manually import the SDK

    In the following example, Xcode 9.0 is used.

    1.  Choose **Single View App** \> **DemoPush** to create a demo project.
    2.  Drag the following files into your Xcode project: `AlivcLibRtmp.framework`, `AlivcLivePusher.framework`, `AlivcLibFaceResource.bundle`, `AliyunPlayerSDK.framework`, and `AliyunLanguageSource.bundle`.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592555907_en-US.png)

        If you do not need Alibaba Cloud ApsaraVideo Player, drag the following files into your project: `AlivcLibRtmp.framework`, `AlivcLivePusher.framework`, and `AlivcLibFaceResource.bundle`.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592555909_en-US.png)

        The following example uses the SDK with Alibaba Cloud ApsaraVideo Player.

    3.  Select **Copy items if needed**, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592555910_en-US.png)

    4.  After importing the SDK, choose **Xcode** \> **General** \> **Embedded Binaries** to add SDK dependencies.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592555911_en-US.png)

        The following figure shows the added dependencies.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592655912_en-US.png)

    5.  Choose **Build Phases** \> **Copy Bundle Resources** to add resource file dependencies.

        **Note:** You can use the facial recognition feature only after adding resource files. Otherwise, you cannot call methods related to facial recognition.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592655913_en-US.png)

    6.  Choose **Building Setting** \> **Enable Bitcode** and set the value to **No**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592755915_en-US.png)

    7.  In the **Info.plist** file, add microphone and camera access permissions: `Privacy - Microphone Usage Description` and `Privacy - Camera Usage Description`.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592755916_en-US.png)

    8.  Configure the iOS development certificate, select debugging on physical devices, and click **Run**. When a **Building Success** message appears, you have successfully imported the SDK into your project.
-   Import the SDK through CocoaPods

    1.  Modify the Podfile.
        -   For the SDK with Alibaba Cloud ApsaraVideo Player

            Add the following statement to your **Podfile**.

            ``` {#codeblock_qiu_9ct_uyl}
            pod 'AlivcLivePusherWithPlayer'
            ```

        -   For the SDK without Alibaba Cloud ApsaraVideo Player

            Add the following statement to your **Podfile**.

            ``` {#codeblock_wd2_51x_xsa}
            pod 'AlivcLivePusher'
            ```

    2.  Run a **pod install** command.

        ``` {#codeblock_eww_wme_g1i}
        pod install: Run this command each time after you add, remove, or update your Podfile.
        ```

    3.  Set **Enable Bitcode** to No.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592755918_en-US.png)

    4.  Configure the **Info.plist** file.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40318/156593592855919_en-US.png)


