# Demo {#concept_iyh_4vx_pfb .concept}

This topic describes the iOS stream ingest SDK demo.

## Demo architecture {#section_n24_pvx_pfb .section}

The iOS demo uses the Model-View-Controller \(MVC\) architecture. The following figure shows the directory structure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20918/156593802855945_en-US.png)

**Mapping of controllers**

-   Others

    -   AlivcNavigationController: the Navigation base class.

    -   AlivcRootViewController: the home page list.

    -   AlivcCopyrightInfoViewController: the copyright information page.

    -   AlivcQRCodeViewController: the QR code scanning page.

-   AlivcLivePusher \(applicable to stream ingest SDK V3.0\)

    -   AlivcLivePushConfigViewController: the stream ingest parameter setting page.

    -   AlivcLivePusherViewController: the stream ingest page.

-   AlivcLiveSessoin \(applicable to stream ingest SDK V1.3\)

    -   AlivcLiveConfigViewController: the stream ingest parameter setting page.

    -   AlivcLiveViewController: the stream ingest page.


## Demo usage {#section_gkm_tvx_pfb .section}

1.  Open the SDK demo project `AlivcLivePusherDemo.xcodeproj`.
2.  Configure the physical device debugging certificate and select debugging on physical devices.
3.  Change the `AlivcTextPushURL` macro in the `PrefixHeader.pch` file to your test ingest URL.

    **Note:** You must change the ingest URL to your test ingest URL to prevent any stream ingest exceptions that may occur when multiple users use the same ingest URL. Alternatively, you can scan the QR code in the demo to change the ingest URL.

4.  Click Run. A Building Success message appears. Then, you can test the demo on physical devices.

## Streaming URL {#section_kg2_wvx_pfb .section}

Generally, the format of an RTMP-based ingest URL is as follows:

`rtmp://push-#YourCompanyDomainName#/#YourAPPName#/#YourstreamName#`

The corresponding streaming URL is as follows:

`rtmp://pull-#YourCompanyDomainName#/#YourAPPName#/#YourstreamName#`

## Demo description {#section_rwk_dwx_pfb .section}

-   On the ApsaraVideo Live scenario list, you can select an item to jump to the demo page of stream ingest SDK V3.0 or stream ingest SDK V1.3.

-   Stream ingest SDK V3.0 is the latest version. It mainly uses the `AlivcLivePusher` class and relevant methods.

-   Stream ingest SDK V1.3 is an earlier version. It mainly uses the `AlivcLiveSession` class and relevant methods.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20918/156593802855947_en-US.png)


