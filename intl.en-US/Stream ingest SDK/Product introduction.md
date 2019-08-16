# Product introduction {#concept_izr_r4k_nfb .concept}

This chapter briefly introduces the Alibaba Cloud stream ingest SDK and describes its features, core benefits, and scenarios.

## Overview {#section_grc_snk_nfb .section}

The Alibaba Cloud stream ingest SDK is a stream ingest development tool for ApsaraVideo Live clients. It was developed based on the powerful Content Delivery Network \(CDN\) and audio-video real-time communication technologies of Alibaba Cloud. It provides you with easy-to-use OpenAPIs, smooth and network-adaptive experience, multi-node low-latency optimization methods, amazing real-time face filters, and other audio-video live streaming technology services. The stream ingest SDK is available free of charge. It helps you save the effort in complex architectural design and reduce maintenance costs, allowing you to focus on improving your business logic and user experience.

The stream ingest SDK provides an advanced facial recognition–based face filter for free, which offers face thinning, chin slimming, eye widening, cheek blushing, facial recognition–based skin whitening, and other features.

**Experience the ApsaraVideo Live demo**

Scan either of the following QR codes to experience the client-cloud integrated demo of Alibaba Cloud ApsaraVideo Live.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20911/156592055413962_en-US.png)

**Note:** The download is not well supported by WeChat and QQ. Use the QR code scanning tool of [DingTalk](https://itunes.apple.com/cn/app/%E9%92%89%E9%92%89/id930368978?spm=a2c4g.11186623.2.16.63da78d6yo1pIQ&mt=8) or other third-party software apart from WeChat and QQ to scan a QR code and download the ApsaraVideo Live demo.

## Features {#section_rc2_j4k_nfb .section}

|Feature|Description|
|:------|:----------|
|Real-Time Messaging Protocol \(RTMP\) stream ingest|Supports low-latency RTMP-based live stream ingest and the RTMP, flash video \(FLV\), and HTTP Live Streaming \(HLS\) live stream pulling protocols. Supports the resolution in the range of 180p to 720p. We recommend that you use 540p.|
|Live screencast|Supports ReplayKit for iOS and camera stream mixing for Android to record and share the screen content.|
|Live Q&A|Inserts supplemental enhancement information \(SEI\) into live streams and uses a player to parse the SEI to support live Q&A.|
|Dynamic watermarks|Inserts or removes watermarks with animation effects in real time during live streaming.|
|External audio and video stream ingest|Supports live streaming of external audios and videos.|
|Background image stream ingest|Supports image stream ingest when an application is moved to the background. Replaces audio and video stream ingest with image stream ingest under poor network conditions.|
|Audio and video coding|Supports H.264 video coding \(softcoding and hardcoding\) and Advanced Audio Coding \(AAC\) \(softcoding and hardcoding\).|
|Real-time face filter|Supports an advanced facial recognition–based face filter, which offers skin smoothing, skin whitening, skin shining, face thinning, chin slimming, eye widening, cheek blushing, and other features.|
|Dynamic bitrate|Automatically adjusts the stream ingest bitrate based on network conditions. Supports multiple modes to provide you with smooth live streaming experience.|
|Dynamic resolution|Automatically adjusts the stream ingest resolution based on network conditions \(applicable only in resolution-first and fluency-first modes\).|
|Background stream ingest|Continues to collect video streams when an application is moved to the background, and enables stream ingest after the application returns to the foreground.|
|Stereo stream ingest|Supports stereo stream ingest in either mono or binaural mode.|
|Multiple watermarks|Supports up to three watermarks and customizable watermark positions and sizes.|
|Screen orientation|Supports stream ingest in portrait, landscape left, and landscape right modes.|
|Stream collection parameter settings|Supports multiple stream collection parameters, such as the resolution, frame rate, audio sampling rate, GOP \(keyframe interval\), and bitrate, to meet stream collection requirements in different scenarios.|
|Stream ingest mirroring|Separates the settings of camera mirroring and stream ingest mirroring \(applicable only to front cameras with the mirroring feature enabled by default\).|
|Audio stream ingest|Collects only audio streams and starts audio stream ingest to reduce the occupied bandwidth and consumed traffic in audio scenarios.|
|Muted stream ingest|Mutes the microphone during stream ingest and pushes only video images.|
|Autofocus|Supports both autofocus and manual focus.|
|Zooming|Zooms in and zooms out for collected streams at the maximum zoom ratio supported by a camera.|
|Camera switchover and flash control|Switches between the front camera and rear camera. Turns on or turns off the flash only for the rear camera.|
|Background music|Plays background music. Allows you to start, stop, pause, and resume background music, play a music loop, and perform other operations.|
|Audio mixing|Mixes music with vocals and adjusts the volume of music and vocals separately.|
|In-ear monitoring|Supports the in-ear monitoring feature. For example, when you sing a song wearing your earpieces, you can hear your own voice from the earpieces in real time. This meets the requirements in KTV scenarios.|
|Noise reduction|Reduce noise caused by ambient sounds and mobile phone interference.|

## Core benefits {#section_ahm_n4k_nfb .section}

-   **Easy to use and integrate**

    Provides uniform APIs and error codes for Android and iOS, synchronous and asynchronous methods to meet the requirements of different development architectures, and comprehensive API reference and demos for your information.

-   **All-in-one solution**

    Offers an ApsaraVideo Live solution that integrates video stream collection, rendering, stream ingest, encoding, distribution, and live streaming. Streamlines adaptive-bitrate stream ingest on clients, narrowband HD encoding in the cloud, and initial instant loading on clients to provide you with one-stop quality services.

-   **High performance and low latency**

    Leads the industry in the stalling rate, CPU and memory usage, power consumption, and heat dissipation of stream ingest. Owns more than 1,000 live streaming nodes around the world to effectively guarantee low latency in various regions.

-   **Data-based operational support**

    Boosts your business development based on comprehensive statistics, sophisticated data security measures, multi-dimensional analysis, and user profiling.


## Scenarios {#section_psl_44k_nfb .section}

**Scenario 1: Live Q&A** 

-   **Scenario description**: Users log on to a specified channel at the specified time and answer questions online following the instructions of a caster. Those who have correctly answered 12 questions are entitled to share the total prize for each live Q&A session. Since early 2018, many Internet companies in China have organized or sponsored such Q&A activities to attract attention from and interact with their existing and potential users. You can also use this feature to promote your own business. For more information, see Live Q&A scheme.
-   **Instructions**: Enable ApsaraVideo Live and submit a ticket to apply for the SEI insertion service. Use the custom Open Broadcaster Software \(OBS\) or an Alibaba Cloud API to insert SEI into live streams. After a user's player receives and parses the SEI, it sends a callback event notification to the user's application. Then, the user can receive and answer questions to participate in the live Q&A. For more information about the player, see [Basic player \(Live Q&A\)](https://www.alibabacloud.com/help/zh/doc-detail/61431.htm?spm=a2c63.l28256.b99.199.43757ad7LSTU8H).

 **Scenario 2: Educational live streaming** 

-   **Scenario description**: Educational live streaming focuses on the interaction between students and teachers. After logging on to a live classroom, students and teachers can type or talk to interact with each other in real time based on the Alibaba Cloud stream ingest SDK and Alibaba Cloud Message Service. The stream ingest SDK enables teachers to answer questions raised by students anytime and anywhere in a timely and effective manner. Based on the cloud-based recording and encoding features, students can play back lessons at any time to review learnt knowledge points and enhance learning effects.

-   **Instructions**: Enable Alibaba Cloud ApsaraVideo Live and enable the recording and encoding features. Integrate the Alibaba Cloud stream ingest SDK and Alibaba Cloud Message Service SDK to implement the live classroom or mentoring service. After integrating the Alibaba Cloud ApsaraVideo Player SDK, users can watch the live streaming or playback of video lessons on clients to enjoy the low-latency and highly interactive educational live streaming.


 **Scenario 3: Entertainment live streaming** 

-   **Scenario description**: With the convenience of mobile phones, entertainment live streaming leads a live streaming trend among users. Casters highly rely on face filters and interact with the audience through the real-time chatting, liking, and rewarding activities to improve their popularity and program playability. However, because entertainment live streaming is easily accessible on mobile phones, the content must be strictly regulated to detect pornography or terrorism. In this case, you can use the pornography detection feature to reduce review costs.

-   **Instructions**: Enable Alibaba Cloud ApsaraVideo Live and enable the recording and pornography detection features. Integrate the Alibaba Cloud stream ingest SDK and enable the face filter feature to implement video stream ingest. In addition, integrate Alibaba Cloud Message Service with your interactive chat scenarios to allow the audience to send text, voice messages, emoticons, and images on the chat panel during live streaming. You can also build a gift system based on payment through an instant messaging system. After integrating the Alibaba Cloud ApsaraVideo Player SDK, users can watch the live streaming or playback on clients.


 **Scenario 4: Game live streaming** 

-   **Scenario description**: Mobile game live streaming uses the screen recording technology to combine the game screen with the camera-shot content and starts stream ingest through the stream ingest SDK. In this case, the stream ingest SDK must support the screen recording feature. Similar to entertainment live streaming, casters in game live streaming scenarios can also interact with the audience through the real-time chatting, liking, and rewarding activities based on the Alibaba Cloud Message Service SDK. To play back game highlights, you can use the live streaming recording and playback features.

-   **Instructions**: Enable Alibaba Cloud ApsaraVideo Live and enable the live streaming recording feature. Integrate the Alibaba Cloud stream ingest SDK and enable the live screencast feature. In addition, integrate Alibaba Cloud Message Service with your interactive chat scenarios to allow the audience to send text, voice messages, emoticons, and images on the chat panel during live streaming. You can also build a gift system based on payment through an instant messaging system. After integrating the Alibaba Cloud ApsaraVideo Player SDK to enable instant loading and dynamic frame acceleration, users can watch the live streaming or playback on clients.


