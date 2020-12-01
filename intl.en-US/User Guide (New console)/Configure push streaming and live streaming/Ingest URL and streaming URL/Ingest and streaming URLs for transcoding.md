# Ingest and streaming URLs for transcoding

ApsaraVideo Live allows you to ingest and play streams on demand without the need to create resources in advance. After you add an ingest domain and a streaming domain that have Internet Content Provider \(ICP\) filings and perform the required operations such as domain resolution and URL signing, you can construct the ingest URL and streaming URL based on the concatenating rules. This topic describes how to construct an ingest URL and a streaming URL for a live stream that requires transcoding.

**Note:**

-   This topic shows you how to manually construct ingest and streaming URLs. You can also use the ApsaraVideo Live console to obtain the URLs. For more information, see [Configure edge ingestion](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md).
-   To batch create live streams, you can construct multiple ingest and streaming URLs at a time. For more information, see [Batch create live activities](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Create multiple live activities.md).
-   You can also construct an ingest URL and a streaming URL for a live stream that does not require transcoding. For more information, see [Ingest and streaming URLs for original quality](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest and streaming URLs for original quality.md).
-   The ingest and streaming URLs in this topic are for reference only. You must use your ingest domain, streaming domain, AppName, StreamName, and access token to construct URLs based on the concatenating rules. The access token can be obtained based on the cryptographic key.

## Prerequisites

To obtain the signed ingest URL and streaming URL, the following operations must be performed:

-   Add domains

    You must add an ingest domain and a streaming domain that have ICP filings first. For more information, see [Add a domain name](/intl.en-US/User Guide (New console)/Domain names management/Manage a domain name/Add a domain name.md).

-   Resolve the domains

    After you add the domains, you must resolve the domains so that you can use the domains. For more information, see [Add a CNAME record](/intl.en-US/User Guide (New console)/Domain names management/Configure CNAME.md).

-   Bind the domains

    After you add the domains, you must bind the ingest domain to the streaming domain so that you can ingest and play streams. For more information, see [Associate domain names](/intl.en-US/User Guide (New console)/Domain names management/Manage a domain name/Associate domain names.md).

-   Configure URL signing

    By default, URL signing is enabled. We recommend that you keep this feature enabled to prevent illegal recording and distribution. To disable URL signing, contact your business manager or submit a ticket. You can use the default URL signing or custom URL signing. For more information, see [Configure URL authentication](/intl.en-US/User Guide (New console)/Domain names management/Access control/Configuration authentication.md).

    **Note:** If you are unable to enable URL signing for ingest URLs, submit a ticket. For more information about how to obtain an unsigned ingest URL and streaming URL, see [Ingest and streaming URLs for original quality](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL (Not authenticated)/Ingest URL and streaming URL (Original).md) and [Ingest and streaming URLs for transcoding](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL (Not authenticated)/Ingest URL and streaming URL (Encoding).md).


## Construct an ingest URL for transcoding

-   Concatenating rules of ingest URLs

    Only streams in the Real-Time Messaging Protocol \(RTMP\) format can be ingested.

    The format of ingest URLs is `RTMP://Ingest domain/AppName/StreamName? Access token`

-   Example

    For example, the ingest domain is `push.aliyunlive.com`, AppName is app, StreamName is stream, and the cryptographic key is 123. Then, the ingest URL is `RTMP://push.aliyunlive.com/app/stream? auth_key=timestamp-rand-uid-md5hash`


## Construct a streaming URL for transcoding

You must configure transcoding first. ApsaraVideo Live supports default transcoding, custom transcoding, and real-time streaming \(RTS\) transcoding. Only after you configure transcoding and obtain the template ID, you can construct a streaming URL for a live stream that requires transcoding based on the concatenating rules.

1.  Configure a transcoding template
    -   Configure default transcoding
        1.  Log on to the [ApsaraVideo Live console](https://live.console.aliyun.com/?spm=5176.2020520001.aliyun_sidebar.aliyun_sidebar_live.22e14bd3E4Wfgc#/overview).
        2.  Click **Domains**.
        3.  Find the required streaming domain and click **Domain Settings**.
        4.  On the **Transcoding Settings** page, click **Default** and then **Add**.

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7006976061/p32853.png)

        5.  Set the parameters of the transcoding template. You can select a template ID based on the configuration.

            Narrowband HD™ template

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/64903/154806368532864_en-US.png)

            **Note:** For more information about transcoding configuration, see [Default encoding](/intl.en-US/User Guide (New console)/Transcoding management/Universal Transcoding.md)

    -   Configure custom transcoding
        1.  Log on to the ApsaraVideo Live console.
        2.  Click **Domains**.
        3.  Find the required streaming domain and click **Domain Settings**.
        4.  On the **Transcoding Settings** page, click **Custom** and then **Add**.

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/23686/154806375537640_en-US.png)

        5.  Set the parameters of the transcoding template. You can select a template ID based on the configuration.

            Narrowband HD™ template

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/64903/154806368532865_en-US.png)

            **Note:** For more information about custom transcoding configuration, see [Custom encoding](/intl.en-US/User Guide (New console)/Transcoding management/Custom transcoding.md).

2.  Obtain the template ID.
    -   Log on to the ApsaraVideo Live console to obtain the template ID.

        You can follow the preceding steps to obtain the template ID.

    -   You can also obtain the template ID by calling an API operation.

        You can call the `DescribeLiveStreamTranscodeInfo` operation to query the template ID. For more information, see [DescribeLiveStreamTranscodeInfo](/intl.en-US/API Reference/Transcoding/DescribeLiveStreamTranscodeInfo.md).

        You can also add custom templates by setting the required parameters. For more information about how to obtain the ID of a custom template, see [AddCustomLiveStreamTranscode](/intl.en-US/API Reference/Transcoding/AddCustomLiveStreamTranscode.md).

3.  Construct the streaming URL

    -   Streaming URLs support the RTMP, Flash Video \(FLV\), HTTP Live Streaming \(HLS\), and User Datagram Protocol \(UDP\) formats. The UDP format is used for the streaming URL of RTS. To use the UDP format, you must enable the RTS feature in advance. To transcode a stream, you must append the `_template ID` to the `StreamName`.
        -   RTMP format: `rtmp://Streaming domain/AppName/StreamName{_template ID}? Access token`
        -   FLV format: `http://Streaming domain/AppName/StreamName{_template ID}.flv?Access token`
        -   HLS format: `http://Streaming domain/AppName/StreamName{_template ID}.m3u8?Access token`
        -   UDP format: `artc:// Streaming domain/AppName/StreamName{_template ID}? Access token`
    -   Example

        For example, the streaming domain is `play.aliyunlive.com`, AppName is app, StreamName is stream, the cryptographic key is 456, and the standard definition \(SD\) template is used. Then, the following streaming URLs are supported.

        -   RTMP format: `rtmp://play.aliyunlive.com/app/stream_sd? auth_key=timestamp-rand-uid-md5hash`
        -   FLV format: `http://play.aliyunlive.com/app/stream_sd.flv?auth_key=timestamp-rand-uid-md5hash`
        -   HLS format: `http://play.aliyunlive.com/app/stream_sd.m3u8?auth_key=timestamp-rand-uid-md5hash`
        -   UDP format: `artc:// play.aliyunlive.com/app/stream_sd? auth_key=timestamp-rand-uid-md5hash`
    The following table describes the parameters of an access token. For more information, see [Sample authentication code](/intl.en-US/Best Practices/Live video security/Authentication code example.md).

    |Parameter|Description|
    |:--------|:----------|
    |timestamp|The expiration time of the signing. The value is a 10-bit positive integer, which indicates the interval between the time when a signed URL becomes invalid and 00:00:00 on January 1, 1970. For example, the validity period of a signed URL is 1,800s.|
    |rand|A random number. We recommend that you use a universally unique identifier \(UUID\), which cannot contain hyphens \(-\). Example: 477b3bbc253f467b8def6711128c7bec.|
    |uid|This parameter is not in use. Set this parameter to 0.|
    |md5hash|The MD5 hash that is calculated based on the MD5 algorithm. The value is a combination of digits and lowercase letters with a fixed length of 32 characters.|


