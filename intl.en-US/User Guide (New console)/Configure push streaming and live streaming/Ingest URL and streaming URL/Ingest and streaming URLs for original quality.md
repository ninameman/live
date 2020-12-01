# Ingest and streaming URLs for original quality

ApsaraVideo Live allows you to ingest and play streams on demand without the need to create resources in advance. After you add an ingest domain and a streaming domain that have Internet Content Provider \(ICP\) filings and perform the required operations such as domain resolution and URL signing, you can construct the ingest URL and streaming URL based on the concatenating rules. This topic describes how to construct an ingest URL and a streaming URL for a live stream that does not require transcoding.

**Note:**

-   This topic shows you how to manually construct ingest and streaming URLs. You can also use the ApsaraVideo Live console to obtain the URLs. For more information, see [Configure edge ingestion](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Configure edge ingestion.md).
-   To batch create live streams, you can construct multiple ingest and streaming URLs at a time. For more information, see [Batch create live activities](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Create multiple live activities.md).
-   You can also construct an ingest and a streaming URL for a live stream that requires transcoding. For more information, see [Ingest and streaming URLs \(for encoding\)](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Encoding).md).
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

    By default, URL signing is enabled. We recommend that you keep this feature enabled to prevent illegal recording and distribution. To disable URL signing, contact your business manager or submit a ticket. You can use the default URL signing or custom URL signing. For more information, see [Configuration authentication](/intl.en-US/User Guide (New console)/Domain names management/Access control/Configuration authentication.md).

    **Note:** If you are unable to enable URL signing for ingest URLs, submit a ticket. For more information about how to obtain an unsigned ingest URL and streaming URL, see [Ingest and streaming URLs for original quality](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL (Not authenticated)/Ingest URL and streaming URL (Original).md) and [Ingest and streaming URLs for transcoding](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL (Not authenticated)/Ingest URL and streaming URL (Encoding).md).


## Construct an ingest URL

-   Concatenating rules of ingest URLs

    Only streams in the Real-Time Messaging Protocol \(RTMP\) format can be ingested.

    The format of ingest URLs is `RTMP://Ingest domain/AppName/StreamName? Access token`

-   For example, the ingest domain is `push.aliyunlive.com`, AppName is app, StreamName is stream, and the cryptographic key is 123. Then, the ingest URL is `RTMP://push.aliyunlive.com/app/stream? auth_key=timestamp-rand-uid-md5hash`

## Construct a streaming URL

-   Concatenating rules of streaming URLs

    Streaming URLs support the RTMP, Flash Video \(FLV\), HTTP Live Streaming \(HLS\), and User Datagram Protocol \(UDP\) formats. The UDP format is used for streaming URLs for real-time streaming \(RTS\). To use the UDP format, you must enable the RTS feature in advance. Formats:

    -   `RTMP:rtmp://Streaming domain/AppName/StreamName? Access token`
    -   `FLV:http://Streaming domain/AppName/StreamName.flv?Access token`
    -   `HLS:http://Streaming domain/AppName/StreamName.m3u8?Access token`
    -   `UDP:artc://Streaming domain/AppName/StreamName? Access token`
-   Example

    For example, the streaming domain is `play.aliyunlive.com`, AppName is app, StreamName is stream, and the cryptographic key is 456. Then, the following streaming URLs are supported:

    -   `RTMP:rtmp://play.aliyunlive.com/app/stream? auth_key=timestamp-rand-uid-md5hash`
    -   `FLV:http://play.aliyunlive.com/app/stream.flv?auth_key=timestamp-rand-uid-md5hash`
    -   `HLS:http://play.aliyunlive.com/app/stream.m3u8?auth_key=timestamp-rand-uid-md5hash`
    -   `UDP:artc://play.aliyunlive.com/app/stream? auth_key=timestamp-rand-uid-md5hash`

