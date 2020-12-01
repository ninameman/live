Overview 
=============================

Real-Time Streaming (RTS) is a value-added feature of ApsaraVideo Live. This feature provides easy-to-access live streaming services of audio and videos with a low latency of milliseconds, high concurrency, high definition, and smooth playback. This topic introduces the RTS feature and describes the architecture, scenarios, and pricing of the RTS feature. This topic also shows you how to use the RTS feature.

Introduction 
---------------------------------

The RTS feature is developed based on ApsaraVideo Live. This feature monitors the latency during the complete live streaming process, reconstructs the Content Delivery Network (CDN) protocol, and optimizes underlying technologies such as User Datagram Protocol (UDP). RTS SDKs are integrated with the player SDKs of ApsaraVideo Live. Compared with conventional live streaming that has a latency of 3 to 6 seconds, RTS supports **the playback of tens of millions of concurrent streams with millisecond-level latency** . You can use RTS to reduce the latency and freezing, and ensure instant loading and smooth playback for live streaming.

Architecture 
---------------------------------

To use the RTS feature, you only need to add an RTS streaming domain to your ApsaraVideo Live service. This way, you can pull streams based on a variety of protocols. The following figure shows the architecture of RTS.

![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4533276061/p134331.png)

* Stream ingest: Streams are ingested based on Real-Time Messaging Protocol (RTMP).

  

* Stream pulling:

  * The source URLs of streams that are pulled based on RTMP start with `rtmp://`. The source URLs of streams that are pulled based on Flash Video (FLV) and HTTP Live Streaming (HLS) start with `http://`.

    
  
  * The source URLs of streams that are pulled based on UDP for RTS start with `artc://`.

    
  

  




Scenarios 
------------------------------

* Education live streaming

  RTS supports large-size classes, where a large number of students can communicate with teachers online at the same time with low latency.
  

* E-commerce live streaming

  RTS allows sellers to communicate with buyers, answer questions of buyers, and exchange product information with buyers in real time.
  

* Sports live streaming

  RTS can be used to broadcast events such as sports and e-sports in real time.
  

* Interactive entertainment

  RTS enables casters to provide real-time feedback when audience send gifts. This improves the interaction between casters and audience.
  




Pricing 
----------------------------

RTS is charged at a price different from that of ApsaraVideo Live. For more information about the pricing and billing methods of RTS, see [Pricing](https://www.alibabacloud.com/product/apsaravideo-for-live/pricing?spm=a2796.132647.1341869000.1.193b474d0iXruV).
**Note**



* Streams that are pulled by using RTS are charged based on the billing items of RTS rather than those of ApsaraVideo Live. No streams are charged twice.

  

* The billing method of RTS is the same as that of your ApsaraVideo Live service. For example, if you select the pay-by-data-transfer or pay-by-bandwidth billing method for ApsaraVideo Live, the same billing method applies to RTS.

  

* When you change the billing method of your ApsaraVideo Live service, the billing method of RTS changes accordingly.

  




Procedure 
------------------------------

1. Enable the RTS feature.

   You cannot enable the RTS feature in the ApsaraVideo Live console. To use the RTS feature, add an RTS streaming domain in the [ApsaraVideo Live console](https://live.console.aliyun.com/#/domain/add/input/) and contact the sales staff or submit a ticket.
   **Notice**

   RTS cannot share a streaming domain with live streaming based on RTMP, FLV, or HLS. You must configure a separate streaming domain for RTS.

   When you apply to enable the RTS feature, you must provide relevant domain information.
   * To launch new business, you must provide a new ingest domain and a new RTS streaming domain that are bound to each other. For more information about how to bind domains, see [Bind an ingest domain to a streaming domain]().

     
   
   * To reuse existing business, you must provide an existing ingest domain, an existing streaming domain, and a new RTS streaming domain. Make sure that the existing streaming domain is bound to the existing ingest domain, and that the new RTS streaming domain is bound as a sub-streaming domain to the existing streaming domain. For more information about how to bind a main streaming domain and a sub-streaming domain, see [Bind a main streaming domain and a sub-streaming domain](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Bind a sub-streaming domain to a main streaming domain.md).

     
   

   

2. Ingest streams.

   For more information, see [Ingest and play streams on PCs]().

   To use RTS to ingest streams, make sure that the source streams do not contain B-frames and are not encoded in the H.265 format. The size of the group of pictures (GOP) of the source streams cannot exceed 3 seconds. If a source stream does not meet the preceding requirements, use the [RTS transcoding]() feature to transcode the source stream. If you transcode the source stream, the latency may increase by hundreds of milliseconds.
   

3. Play streams.

   For more information, see [Ingest and play streams on PCs]().
   * Player: RTS is based on UDP and has special requirements on players. If you use RTS SDKs for mobile clients with ApsaraVideo Player, make sure that the version of ApsaraVideo Player is `5.1.5` or later. If you use RTS SDK for HTML5 with ApsaraVideo Player, make sure that the version of ApsaraVideo Player is `1.1.0` or later.

     
   
   * RTS streaming URL:

     * The method for concatenating RTS streaming URLs is the same as that for concatenating common streaming URLs, except that RTS streaming URLs start with `artc://`.

       For example, you can concatenate RTS streaming URLs in the format of `artc://Streaming domain/AppName/StreamName? Access token`. For more information, see [Ingest and streaming URLs (for original quality)](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Original).md).
       
     
     * RTS SDK for HTML5 does not support Advanced Audio Coding (AAC). To use RTS SDK for HTML5, you must transcode streams to the Opus format. This limit does not apply to RTS SDKs for mobile clients. When you use RTS SDK for HTML5, you must use a transcoding streaming URL.

       For example, you can concatenate RTS streaming URLs for transcoding in the format of `artc://Streaming domain/AppName/StreamName{_Transcoding template ID}? Access token`. For more information, see [Ingest and streaming URLs (for encoding)](/intl.en-US/User Guide (New console)/Configure push streaming and live streaming/Ingest URL and streaming URL/Ingest URL and streaming URL (Encoding).md).
       
     

     
   

   

4. Record live streams.

   The configuration method for recording RTS live streams is the same as that for recording common live streams. After the configuration is completed, recording files are automatically stored in Object Storage Service (OSS) or ApsaraVideo VOD. For more information, see [Save live recordings to OSS](/intl.en-US/User Guide (New console)/Recording management/Save live recordings to OSS/Store live recordings to OSS.md) and [Save live recordings to ApsaraVideo VOD]().
   



