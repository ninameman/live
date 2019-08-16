# SDK usage {#concept_wx4_lvw_pfb .concept}

This topic describes how to use the iOS stream ingest SDK.

The basic procedure for using the stream ingest SDK is as follows:

1.  Set stream ingest parameters.
2.  Create a stream ingest preview.
3.  Start stream ingest.
4.  Adjust stream ingest parameters in real time as needed.

## Stream ingest parameter settings {#section_hm1_xlx_pfb .section}

You can use the **AlivcLivePushConfig** class to set stream ingest parameters. Each parameter has a default value. For more information about parameter default values and value ranges, see the API reference or comments. You can modify the values of these parameters as needed. For more information about how to modify these parameters in real time during stream ingest, see the properties and methods provided by the **AlivcLivePusher** class.

-   Basic configuration

    Import a header file into your **ViewController**: **\#import <AlivcLivePusher/AlivcLivePusherHeader.h\>**. The following example shows the sample code.

    ``` {#codeblock_dma_4cq_luv}
    AlivcLivePushConfig *config = [[AlivcLivePushConfig alloc] init]; // Initialize the AlivcLivePushConfig class. You can also call the initWithResolution method.
    config.resolution = AlivcLivePushResolution540P; // Keep the default value to set the resolution to 540p. The maximum resolution is 720p.
    config.fps = AlivcLivePushFPS20; // We recommend that you set the frame rate to 20 fps.
    config.enableAutoBitrate = true; // Enable bitrate control. The default value is true.
    config.videoEncodeGop = AlivcLivePushVideoEncodeGOP_2; // Keep the default value to set the keyframe interval to 2. A greater interval between keyframes indicates higher latency. We recommend that you set this value in the range of 1 to 2.
    config.connectRetryInterval = 2000; // Keep the default value (2000 in units of milliseconds) to set the reconnection interval to 2s. You cannot set a reconnection interval shorter than 1s. We recommend that you use the default value.
    config.previewMirror = false; // Keep the default value to disable preview mirroring. We recommend that you use the default value.
    config.orientation = AlivcLivePushOrientationPortrait; // Keep the default value to set the screen orientation to portrait. You can also set the screen orientation to landscape left or landscape right.
    ```

    **Note:** 

    -   All these parameters have default values. We recommend that you use the default values.
    -   Considering the performance of most mobile phones and network bandwidth requirements, we recommend that you set the resolution to 540p. Most mainstream live streaming applications use 540p.
    -   If bitrate control is disabled, the bitrate is fixed to the initial value and cannot be automatically adjusted between the specified target bitrate and minimum bitrate. If the network is unstable, the fixed bitrate may cause video stalling. You need to disable bitrate control with caution.
-   Bitrate control

    The stream ingest SDK provides three bitrate control modes. You can modify the qualityMode parameter to one of the following values:

    -   ******AlivcLivePushQualityModeResolutionFirst**: indicates the resolution-first mode in which the stream ingest SDK sets the bitrate to prioritize the resolution of video streams.
    -   ******AlivcLivePushQualityModeFluencyFirst**: indicates the fluency-first mode in which the stream ingest SDK sets the bitrate to prioritize the fluency of video streams.
    -   ******AlivcLivePushQualityModeCustom**: indicates the custom mode in which the stream ingest SDK sets the bitrate based on your custom bitrate settings.
    The following example shows the sample code for the resolution-first or fluency-first mode.

    ``` {#codeblock_gld_h8u_3qa}
    config.qualityMode = AlivcLivePushQualityModeResolutionFirst; // Keep the default value to set the bitrate control mode to resolution-first. You can change this mode to fluency-first or custom mode.
    ```

    **Note:** If you set the value to **AlivcLivePushQualityModeResolutionFirst** or **AlivcLivePushQualityModeFluencyFirst**, you do not need to set the **targetVideoBitrate**, **minVideoBitrate**, and **initialVideoBitrate** parameters. The stream ingest SDK can automatically set the bitrate based on packet delay variation to give priority to the resolution or fluency of video streams.

    The following example shows the sample code for the custom mode.

    ``` {#codeblock_3ln_xjm_b71}
    config.qualityMode = AlivcLivePushQualityModeCustom // Set the bitrate control mode to custom mode.
    config.targetVideoBitrate = 1200; // Set the target bitrate to 1200 Kbit/s.
    config.minVideoBitrate = 400; // Set the minimum bitrate to 400 Kbit/s.
    config.initialVideoBitrate = 900; // Set the initial bitrate to 900 Kbit/s.
    ```

    If you select the custom mode, you need to set the target bitrate, minimum bitrate, and initial bitrate. The initial bitrate is the bitrate when live streaming starts. Under poor network conditions, the stream ingest SDK gradually decreases the bitrate to the minimum bitrate to minimize video stalling. Under good network conditions, the stream ingest SDK gradually increases the bitrate to the target bitrate to improve the resolution of video streams.

    The following table lists the recommended parameter values in custom mode.

    |Resolution|targetVideoBitrate|minVideoBitrate|initialVideoBitrate|
    |:---------|:-----------------|:--------------|:------------------|
    |360p|800|200|600|
    |480p|1000|300|700|
    |540p|1200|400|900|
    |720p|1500|600|1200|

-   Dynamic resolution

    If dynamic resolution is enabled, the stream ingest SDK can automatically decrease the resolution to maximize the fluency and resolution of video streams under poor network conditions. Some media players may not support dynamic resolution, which has been supported by Alibaba Cloud ApsaraVideo Player. If dynamic resolution is enabled, we recommend that you use Alibaba Cloud ApsaraVideo Player.

    ``` {#codeblock_ges_7ru_oil}
    config.enableAutoResolution = YES; // Enable dynamic resolution. The default value is NO.
    ```

    **Note:** Dynamic resolution takes effect only in resolution-first or fluency-first mode. You must set the qualityMode parameter to AlivcLivePushQualityModeResolutionFirst or AlivcLivePushQualityModeFluencyFirst. Dynamic resolution does not take effect in custom mode.

-   Face filter

    The stream ingest SDK provides two face filters: basic and advanced. The basic face filter supports skin whitening, skin smoothing, and skin shining. The advanced face filter supports facial recognition–based skin whitening, skin smoothing, skin shining, eye widening, chin slimming, face thinning, and cheek blushing. To use the advanced face filter, you must set the beautyMode parameter to **AlivcLivePushBeautyModeProfessional** and import the facial recognition resource file **AlivcLibFaceResource.bundle** into your project.

    To use the basic face filter, you must import the face filter DLL file **AlivcLibBeauty.framework** and configure all callback event notifications related to the **AlivcLivePusherCustomFilterDelegate** class.

    The following example shows the sample code.

    Face filter configuration

    ``` {#codeblock_59d_r58_np3}
    config.beautyOn = true; // Enable face filter.
    config.beautyMode = AlivcLivePushBeautyModeNormal; // Select the basic face filter.
    config.beautyWhite = 70; // Set the intensity of skin whitening in the range of 0 to 100.
    config.beautyBuffing = 40; // Set the intensity of skin smoothing in the range of 0 to 100.
    config.beautyRuddy = 40; // Set the intensity of skin shining in the range of 0 to 100.
    ```

    Face filter callback event notification configuration

    ``` {#codeblock_ln6_t49_prw}
    /**
     Configure the callback event notification for creating an external face filter.
     */
    - (void)onCreate:(AlivcLivePusher *)pusher context:(void*)context
    {
        [[AlivcLibBeautyManager shareManager] create:context];
    }
    ```

    ``` {#codeblock_l4r_s8z_rk2}
    /**
     Configure the callback event notification for updating parameters of an external face filter.
     */
    - (void)updateParam:(AlivcLivePusher *)pusher buffing:(float)buffing whiten:(float)whiten pink:(float)pink cheekpink:(float)cheekpink thinface:(float)thinface shortenface:(float)shortenface bigeye:(float)bigeye
    {
        [[AlivcLibBeautyManager shareManager] setParam:buffing whiten:whiten pink:pink cheekpink:cheekpink thinface:thinface shortenface:shortenface bigeye:bigeye];
    }
    ```

    ``` {#codeblock_d7g_jib_1qc}
    /**
     Configure the callback event notification for enabling an external face filter.
     */
    - (void)switchOn:(AlivcLivePusher *)pusher on:(bool)on
    {
        [[AlivcLibBeautyManager shareManager] switchOn:on];
    }
    ```

    ``` {#codeblock_jnp_6eh_6ci}
    /**
     Configure the callback event notification for the processing by an external face filter.
     */
    - (int)onProcess:(AlivcLivePusher *)pusher texture:(int)texture textureWidth:(int)width textureHeight:(int)height extra:(long)extra
    {
        return [[AlivcLibBeautyManager shareManager] process:texture width:width height:height extra:extra];
    }
    ```

    ``` {#codeblock_ym4_nic_prz}
    /**
     Configure the callback event notification for destroying an external face filter.
     */
    - (void)onDestory:(AlivcLivePusher *)pusher
    {
        [[AlivcLibBeautyManager shareManager] destroy];
    }
    ```

    To use the advanced face filter, you must import the external face filter DLL file **AlivcLibFace.framework** and the facial recognition resource file **AlivcLibFaceResource.bundle**. The following example shows the sample code.

    Advanced face filter configuration

    ``` {#codeblock_670_zrg_yve}
    config.beautyOn = true; // Enable face filter.
    config.beautyMode = AlivcLivePushBeautyModeProfessional; // Select the advanced face filter.
    config.beautyWhite = 70; // Set the intensity of skin whitening in the range of 0 to 100.
    config.beautyBuffing = 40; // Set the intensity of skin smoothing in the range of 0 to 100.
    config.beautyRuddy = 40; // Set the intensity of skin shining in the range of 0 to 100.
    config.beautyBigEye = 30; // Set the intensity of eye widening in the range of 0 to 100.
    config.beautyThinFace = 40; // Set the intensity of face thinning in the range of 0 to 100.
    config.beautyShortenFace = 50; // Set the intensity of chin slimming in the range of 0 to 100.
    config.beautyCheekPink = 15; // Set the intensity of cheek blushing in the range of 0 to 100.
    ```

    Facial detection filter callback event notification configuration

    ``` {#codeblock_b2q_us5_8k6}
    /**
     Configure the callback event notification for creating an external facial detection filter.
     */
    - (void)onCreateDetector:(AlivcLivePusher *)pusher
    {
        [[AlivcLibFaceManager shareManager] create];
    }
    ```

    ``` {#codeblock_o58_f1s_ree}
    /**
     Configure the callback event notification for the processing by an external facial detection filter.
     */
    - (long)onDetectorProcess:(AlivcLivePusher *)pusher data:(long)data w:(int)w h:(int)h rotation:(int)rotation format:(int)format extra:(long)extra
    {
         return [[AlivcLibFaceManager shareManager] process:data width:w height:h rotation:rotation format:format extra:extra];
    }
    ```

    ``` {#codeblock_fjw_i7c_slf}
    /**
     Configure the callback event notification for destroying an external facial detection filter.
     */
    - (void)onDestoryDetector:(AlivcLivePusher *)pusher
    {
        [[AlivcLibFaceManager shareManager] destroy];
    }
    ```

    To use third-party face filters and facial detection filters, you can follow the preceding procedures and call relevant methods.

    **Note:** With the help of the Alibaba Cloud UED team, we recommend that you try out different parameter settings to find those that best suit your needs.

    The following table lists the optimal face filter parameter settings for your reference.

    |Setting|Skin smoothing|Skin whitening|Skin shining|Eye widening|Face thinning|Chin slimming|Cheek blushing|
    |:------|:-------------|:-------------|:-----------|:-----------|:------------|:------------|:-------------|
    |One|40|35|10|0|0|0|0|
    |Two|60|80|20|0|0|0|0|
    |Three|50|100|20|0|0|0|0|
    |Four|40|70|40|30|40|50|15|
    |Five|70|100|10|30|40|50|0|

-   Image stream ingest

    To improve user experience, the stream ingest SDK supports image stream ingest when your application is moved to the background or detects a low bitrate. When your application is moved to the background, the stream ingest SDK disables video stream ingest and ingests only audio streams by default. In this case, you can specify images to ingest image streams and audio streams. For example, you can display an image to remind users that the caster is away for the moment and will come back soon. The following example shows the sample code.

    ``` {#codeblock_9l4_hxk_v74}
    config.pauseImg = [UIImage imageNamed:@"Image.png"]; // Specify the image for image stream ingest when an application is moved to the background.
    ```

    In addition, you can specify a static image as needed for image stream ingest under poor network conditions. In this case, the stream ingest SDK can enable image stream ingest at a low bitrate to push only this image and avoid video stalling. The following example shows the sample code.

    ``` {#codeblock_hoo_lp4_w58}
    config.networkPoorImg = [UIImage imageNamed:@"Image.png"]; // Specify the image for image stream ingest under poor network conditions.
    ```

-   Watermarks

    The stream ingest SDK allows you to add one or more watermarks, the source of which must be PNG files. The following example shows the sample code.

    ``` {#codeblock_21g_zvd_39l}
    NSString *watermarkBundlePath = [[NSBundle mainBundle] pathForResource:    [NSString stringWithFormat:@"watermark"] ofType:@"png"]; // Specify the path of the source image.
    [config addWatermarkWithPath: watermarkBundlePath
          watermarkCoordX:0.1
          watermarkCoordY:0.1
          watermarkWidth:0.3]; // Add a watermark.
    ```

    **Note:** 

    -   The coordX, coordY, and width parameters are set to relative values. For example, `watermarkCoordX:0.1` indicates that the coordX parameter value of the watermark is at the 10% position on the x-axis of the stream ingest screen. Therefore, if the stream ingest resolution is 540 x 960, the coordX parameter is set to 54.
    -   The height of the watermark is calculated based on the specified width parameter value with an aspect ratio equal to that of the source image.
    -   To add a text watermark, you can convert text into an image, and then call the addWatermarkWithPath method to add the image as a watermark.
    -   To ensure the resolution and smooth edges of the watermark, we recommend that you use a source image that has the same size as the displayed watermark. If the output resolution of a video is 544 x 940 and the watermark width is 0.1f, we recommend that you use a source image with a width of about 544 x 0.1f = 54.4.
-   Preview mode

    The stream ingest SDK supports the following three preview modes:

    -   ALIVC\_LIVE\_PUSHER\_PREVIEW\_SCALE\_FILL // Indicates that the stream ingest SDK adjusts the video size to fill the screen for a preview. If the aspect ratio of the video is different from that of the preview screen, the preview image is distorted.
    -   ALIVC\_LIVE\_PUSHER\_PREVIEW\_ASPECT\_FIT // Indicates that the stream ingest SDK maintains the aspect ratio of the video for a preview. If the aspect ratio of the video is different from that of the preview screen, each blank edge is displayed in black. This preview mode is the default mode.
    -   ALIVC\_LIVE\_PUSHER\_PREVIEW\_ASPECT\_FILL // Indicates that the stream ingest SDK crops the video to fit the screen for a preview. If the aspect ratio of the video is different from that of the preview screen, the video is cropped for the preview.
    You can use the AlivcLivePushConfig class to set the preview mode or call the setpreviewDisplayMode method to set the preview mode during a preview or stream ingest.

    **Note:** This configuration takes effect only for a preview. The resolution of ingested video streams is specified through the AlivcLivePushConfig class and does not change even if you change the preview mode. You can select a preview mode as needed to adapt to mobile phones that have difference screen sizes.


## AlivcLivePusher {#section_l1b_5qx_pfb .section}

The **AlivcLivePusher** class is a core class of the stream ingest SDK. It provides camera preview, stream ingest callback, stream ingest control, parameter adjustment during stream ingest, and other features.

-   Initialize an AlivcLivePusher object

    After setting stream ingest parameters, you can call the **initWithConfig** method provided by the stream ingest SDK to initialize an AlivcLivePusher object. The following example shows the sample code.

    ``` {#codeblock_4yp_lsd_xt9}
    self.livePusher = [[AlivcLivePusher alloc] initWithConfig:config];
    ```

    **Note:** Currently, the **AlivcLivePusher** class does not support multiple instances. You must call a destroy method each time after calling an init method.

-   Register stream ingest callback event notifications

    Stream ingest callback event notifications are classified into Info, Error, and Network. Info callback event notifications are used to send messages and detect status. Error callback event notifications are used to notify errors. Network callback event notifications are used to notify the network status. You can call relevant delegate methods to register and receive callback event notifications.

    ``` {#codeblock_qqa_tpr_1v0}
    [self.livePusher setInfoDelegate:self];
    [self.livePusher setErrorDelegate:self];
    [self.livePusher setNetworkDelegate:self];
    ```

-   Start a preview

    You can start a preview after you initialize the AlivcLivePusher object. You need to create a view object in the UIView class to start the preview. The following example shows the sample code.

    ``` {#codeblock_b4z_xw1_7us}
    [self.livePusher startPreview:self.view];
    ```

-   Start stream ingest

    The stream ingest SDK can start stream ingest only after a successful preview. Therefore, you need to add the following code when you configure the `onPreviewStarted` event notification to be received through the `AlivcLivePusherInfoDelegate` interface:

    ``` {#codeblock_dza_6ng_q5u}
    [self.livePusher startPushWithURL:@"Test ingest URL (rtmp://......)"] ;
    ```

    **Note:** 

    -   The stream ingest SDK also provides the `startPushWithURLAsync` method to support asynchronous stream ingest.
    -   The stream ingest SDK supports RTMP-based ingest URLs. For more information about how to obtain an Alibaba Cloud ingest URL, see Quick Start.
    -   After starting stream ingest based on a correct ingest URL, you can use a player, such as Alibaba Cloud ApsaraVideo Player, FFplay, or VLC, to run a stream pulling test. For more information about how to obtain a source URL, see Quick Start.
-   Control stream ingest

    To control stream ingest, you can start stream ingest, stop stream ingest, stop a preview, restart stream ingest, disable stream ingest, enable stream ingest, and destroy stream ingest. You can add buttons as needed to perform these operations. The following example shows the sample code.

    ``` {#codeblock_6ng_og0_h1j}
    /* Call this method to disable ongoing stream ingest. Then, the stream ingest SDK pauses the video preview and video stream ingest at the last frame, and continues audio stream ingest. */
    [self.livePusher pause];
    /* Call this method to enable disabled stream ingest. Then, the stream ingest SDK resumes the audio and video preview and stream ingest. */
    [self.livePusher resume];
    /* Call this method to stop ongoing stream ingest. Then, the stream ingest SDK stops stream ingest. */
    [self.livePusher stopPush];
    /* Call this method to stop an ongoing preview. However, you cannot call this method to stop a preview during stream ingest. After you call this method, the stream ingest SDK freezes the preview screen at the last frame. */
    [self.livePusher stopPreview];
    /* Call this method to restart stream ingest during stream ingest or after you receive any callback event notification related to an error. When such an error occurs, you can only call this method to restart stream ingest, call the reconnectPushAsync method to reconnect to the network, or call the destroy method to destroy stream ingest. After you call this method, the stream ingest SDK restarts stream ingest, and restarts all resources of the AlivcLivePusher object, including preview frames and ingest streams. */
    [self.livePusher restartPush];
    /* Call this method to reconnect to the network during stream ingest or after you receive any callback event notification related to an error through the AlivcLivePusherNetworkDelegate interface. When such an error occurs, you can only call this method to reconnect to the network, call the restartPush method to restart stream ingest, or call the destroy method to destroy stream ingest. After you call this method, the stream ingest SDK establishes an RTMP connection again. */
    [self.livePusher reconnectPushAsync];
    /* Call this method to destroy stream ingest. Then, the stream ingest SDK stops the stream ingest and preview, removes the preview screen, and destroys all resources related to the AlivcLivePusher object. */
    [self.livePusher destory];
    self.livePusher = nil;
    /* Obtain the stream ingest status. */
    AlivcLivePushStatus status = [self.livePusher getLiveStatus];
    ```

-   Adjust face filter parameters

    The stream ingest SDK allows you to adjust face filter parameters in real time during stream ingest. You can adjust parameters for the basic and advanced face filters separately. The following example shows the sample code.

    ``` {#codeblock_iur_5xh_kiy}
    [self.livePusher setBeautyOn:true]; // Enable or disable face filter.
    /* For the basic face filter, adjust the following parameters: */
    self.livePusher.beautyWhite = 70; // Set the intensity of skin whitening in the range of 0 to 100.
    self.livePusher.beautyBuffing = 40; // Set the intensity of skin smoothing in the range of 0 to 100.
    self.livePusher.beautyRuddy = 40; // Set the intensity of skin shining in the range of 0 to 100.
    /* In addition to parameters for the basic face filter, adjust the following parameters for the advanced face filter: */
    self.livePusher.beautyBigEye = 30; // Set the intensity of eye widening in the range of 0 to 100.
    self.livePusher.beautyThinFace = 40; // Set the intensity of face thinning in the range of 0 to 100.
    self.livePusher.beautyShortenFace = 50; // Set the intensity of chin slimming in the range of 0 to 100.
    self.livePusher.beautyCheekPink = 15; // Set the intensity of cheek blushing in the range of 0 to 100.
    ```

-   Control background music

    The stream ingest SDK allows you to play background music and provides the audio mixing, noise reduction, in-ear monitoring, mute, and other features for background music. You can call relevant methods only after starting a preview. The following example shows the sample code.

    ``` {#codeblock_qnr_gf9_095}
    /* Start playing background music. */
    [self.livePusher startBGMWithMusicPathAsync:musicPath];
    /* Stop playing background music. To change the current background music, call the startBGMWithMusicPathAsync method to start playing the new background music. You do not need to stop the current background music. */
    [self.livePusher stopBGMAsync];
    /* Pause background music. You can call this method only when the background music is being played. */
    [self.livePusher pauseBGM];
    /* Resume background music. You can call this method only when the background music is paused. */
    [self.livePusher resumeBGM];
    /* Start playing a music loop. */
    [self.livePusher setBGMLoop:true];
    /* Configure noise reduction. If you enable noise reduction, the stream ingest SDK filters out non-vocal parts from collected audio. This feature may slightly reduce the volume of vocals. Therefore, we recommend that you enable this feature as needed. This feature is disabled by default. */
    [self.livePusher setAudioDenoise:true];
    /* Configure in-ear monitoring. In-ear monitoring mainly applies to KTV scenarios. If you enable in-ear monitoring, you can hear your own voice from your earpieces. If you disable in-ear monitoring, you cannot hear your own voice from your earpieces. This feature does not work without earpieces. */
    [self.livePusher setBGMEarsBack:true];
    /* Configure audio mixing to adjust the volume of background music and vocals separately. */
    [self.livePusher setBGMVolume:50]; // Adjust the volume of background music.
    [self.livePusher setCaptureVolume:50]; // Adjust the volume of vocals.
    /* Configure mute. If you enable this feature, the stream ingest SDK mutes both music and vocals. To mute music or vocals separately, you can call a method related to audio mixing to adjust the volume of music or vocals separately. */
    [self.livePusher setMute:isMute? true:false];
    ```

-   Perform camera-related operations

    You can perform camera-related operations only after starting a preview in the following scenarios: during stream ingest, when stream ingest is disabled, or the stream ingest SDK is reconnecting to the network. For example, you can switch between the front camera and rear camera, control the flash, adjust the focal length, configure focus, and configure mirroring. If you have not started a preview, the following methods do not take effect. The following example shows the sample code.

    ``` {#codeblock_aty_y8n_fo9}
    /* Switch between the front camera and rear camera. */
    [self.livePusher switchCamera];
    /* Turn on or turn off the flash. You cannot turn on the flash for the front camera. */
    [self.livePusher setFlash:false]; 
    /* Adjust the focal length to zoom in and zoom out for collected streams. If you set a positive parameter value, the stream ingest SDK increases the focal length. If you set a negative parameter value, the stream ingest SDK decreases the focal length. */
    CGFloat max = [_livePusher getMaxZoom];
    [self.livePusher setZoom:MIN(1.0, max)]; 
    /* Configure manual focus. You need to set two parameters: point and autoFocus. The point parameter indicates the coordinates of the point to be focused on. The autoFocus parameter indicates whether to enable autofocus and takes effect only for the current focusing operation. Whether autofocus is enabled for subsequent operations depends on the autofocus configuration after you call the setAutoFocus method. */
    [self.livePusher focusCameraAtAdjustedPoint:CGPointMake(50, 50)  autoFocus:true]; 
    /* Configure autofocus. */
    [self.livePusher setAutoFocus:false];
    /* Configure mirroring. You can set the PushMirror or PreviewMirror parameter to configure mirroring. The PushMirror parameter is valid only for the streaming screen, whereas the PreviewMirror parameter is valid only for the preview screen. They are mutually independent. */
    [self.livePusher setPushMirror:false];
    [self.livePusher setPreviewMirror:false];
    ```

-   Implement live Q&A

    To implement live Q&A, you can insert SEI into live streams and use a player to parse the SEI. The stream ingest SDK provides a method for you to insert SEI. You can call this method only during stream ingest. The following example shows the sample code.

    ``` {#codeblock_d3w_nty_tv8}
    /*
    msg: the message body of the SEI to be inserted into live streams. We recommend that you use the JSON format. The Alibaba Cloud ApsaraVideo Player SDK can receive and parse this SEI and display the parsed content.
    repeatCount: the number of frames into which the SEI is inserted. To avoid SEI loss due to frame discard, the same SEI must be inserted into multiple frames. If this parameter is set to 100, the same SEI is inserted into the next 100 frames. The player can remove duplicate SEI.
    delayTime: the interval for sending frames that contain the SEI, measured in milliseconds.
    KeyFrameOnly: indicates whether to insert the SEI only into keyframes.
    */
    [self.livePusher sendMessage:@"Questions" repeatCount:100 delayTime:0 KeyFrameOnly:false];
    ```

-   Configure external audio and video input

    The stream ingest SDK supports external audios and videos for stream ingest, such as an audio and video file, or audio and video data collected by third-party devices. The procedure is as follows:

    1.  Use the AlivcLivePushConfig class to set parameters for the external audio and video input. The following example shows the sample code.

        ``` {#codeblock_4x9_7wz_bq7}
        config.externMainStream = true; // Enable external stream input.
        config.externVideoFormat = AlivcLivePushVideoFormatYUVNV21; // Specify the color format for video data, which is set to YUVNV21 in this example. You can use other formats as needed.
        config.externMainStream = AlivcLivePushAudioFormatS16; // Specify the bit depth format for audio data, which is set to S16 in this example. You can use other formats as needed.
        ```

    2.  Insert external video data. The following example shows the sample code.

        ``` {#codeblock_dal_ujr_gus}
        /* For circular buffer data in YUV or RGB format, you can call the sendVideoData method to specify the buffer, length, width, height, timestamp, and rotation angle of video data. */
        [self.livePusher sendVideoData:yuvData width:720 height:1280 size:dataSize pts:nowTime rotation:0];
        /* For CMSampleBufferRef data, you need to call the sendVideoSampleBuffer method. */
        [self.livePusher sendVideoSampleBuffer:sampleBuffer]
        /* You can also convert CMSampleBufferRef into a circular buffer, and then call the sendVideoData method. The following example shows the sample code. */
        // Obtain the length of the sample buffer.
        - (int) getVideoSampleBufferSize:(CMSampleBufferRef)sampleBuffer {
        if(! sampleBuffer) {
            return 0;
        }
        int size = 0;
        CVPixelBufferRef pixelBuffer = CMSampleBufferGetImageBuffer(sampleBuffer);
        CVPixelBufferLockBaseAddress(pixelBuffer, 0);
        if(CVPixelBufferIsPlanar(pixelBuffer)) {
           int count = (int)CVPixelBufferGetPlaneCount(pixelBuffer);
           for(int i=0; i<count; i++) {
               int height = (int)CVPixelBufferGetHeightOfPlane(pixelBuffer,i);
               int stride =  (int)CVPixelBufferGetBytesPerRowOfPlane(pixelBuffer,i); 
               size += stride*height;
           }
        }else {
           int height = (int)CVPixelBufferGetHeight(pixelBuffer);
           int stride = (int)CVPixelBufferGetBytesPerRow(pixelBuffer);
           size += stride*height;
        }
        CVPixelBufferUnlockBaseAddress(pixelBuffer, 0);
        return size;
        }
        // Convert the sample buffer into a circular buffer.
        - (int) convertVideoSampleBuffer:(CMSampleBufferRef)sampleBuffer toNativeBuffer:(void*)nativeBuffer {
        if(! sampleBuffer || ! nativeBuffer) {
           return -1;
        }
        CVPixelBufferRef pixelBuffer = CMSampleBufferGetImageBuffer(sampleBuffer);
        CVPixelBufferLockBaseAddress(pixelBuffer, 0);
        int size = 0;
        if(CVPixelBufferIsPlanar(pixelBuffer)) {
           int count = (int)CVPixelBufferGetPlaneCount(pixelBuffer);
           for(int i=0; i<count; i++) { 
               int height = (int)CVPixelBufferGetHeightOfPlane(pixelBuffer,i);
               int stride = (int)CVPixelBufferGetBytesPerRowOfPlane(pixelBuffer,i);
               void *buffer = CVPixelBufferGetBaseAddressOfPlane(pixelBuffer, i);
               int8_t *dstPos = (int8_t*)nativeBuffer + size;
               memcpy(dstPos, buffer, stride*height);
               size += stride*height;
           }
        }else {
           int height = (int)CVPixelBufferGetHeight(pixelBuffer);
           int stride = (int)CVPixelBufferGetBytesPerRow(pixelBuffer);
           void *buffer = CVPixelBufferGetBaseAddress(pixelBuffer);
           size += stride*height;
           memcpy(nativeBuffer, buffer, size);
        }
        CVPixelBufferUnlockBaseAddress(pixelBuffer, 0);
        return 0;
        }
        ```

    3.  Insert external audio data. The following example shows the sample code.

        ``` {#codeblock_vni_45l_5jb}
        /* For circular buffer data in PCM format, you can call the sendPCMData method to specify the buffer, length, and timestamp of audio data. */
        [self.livePusher sendPCMData:pcmData size:size pts:nowTime];
        ```

-   Configure animated stickers

    The stream ingest SDK allows you to add animated stickers to live streams so as to add dynamic watermarks.

    -   To prepare an animated sticker, you can modify materials provided in the demo. Prepare sequential images for the animated sticker and open the config.json file to customize relevant parameters.

        ``` {#codeblock_l5v_qym_46l}
        "du": 2.04, // The duration for playing the animation once.
        "n": "qizi", // The name of the animation. Name the folder of the animation after the animation name, and name each image the animation name followed by the sequence number, such as qizi0.
        "c": 68.0, // The number of frames, which is the number of images, included in the animation.
        "kerneframe": 51, // The keyframe, which specifies an image as a keyframe. For example, this parameter specifies the fifty-first frame, which must exist, as the keyframe in the demo.
        "frameArry": [
                     {"time":0,"pic":0},
                     {"time":0.03,"pic":1},
                     {"time":0.06,"pic":2},
                     ],
        // The preceding animation parameter settings indicate that the first frame qizi0 appears at second 0, the second frame qizi1 appears after 0.03 seconds, and so forth. Follow this rule to specify all frames for the animation.
        ```

        **Note:** You can directly use the settings of other parameters in the config.json file provided in the demo.

    -   Add an animated sticker. The following example shows the sample code.

        ``` {#codeblock_t68_y50_1dt}
        /*
        waterMarkDirPath: the path of the sticker, which must contain the config.json file.
        x,y: the position of the sticker on the x-axis and y-axis of the screen, in the range of 0f to 1.0f.
        w,h: the width and height of the sticker on the screen, in the range of 0f to 1.0f.
        return: returns the sticker ID (specified by the vid parameter), which can be used to delete the specified sticker.
        */
        int vid = [self.livePusher addDynamicWaterMarkImageDataWithPath:path x:x y:y w:w h:h];
        ```

    -   Delete an animated sticker. The following example shows the sample code.

        ``` {#codeblock_45z_u7q_fws}
        [self.livePusher removeDynamicWaterMark:vid];
        ```

-   Use the debugging tool

    The stream ingest SDK provides a UI-based debugging tool DebugView to help you diagnose problems. DebugView shows a draggable floating window that always appears on top of others on the screen. It provides multiple debugging features for you to view stream ingest logs, monitor the performance parameters of stream ingest in real time, and view a line chart of key stream ingest performance. The following example shows the sample code.

    ``` {#codeblock_lb7_osn_jzl}
    [AlivcLivePusher showDebugView]; // Show DebugView.
    ```

    **Note:** For your application to be published, you only need to add a button to hide DebugView.

-   Call other methods

    ``` {#codeblock_hlp_ft2_73u}
    /* In custom bitrate control mode, adjust the minimum bitrate and target bitrate in real time. */
    [self.livePusher setTargetVideoBitrate:800];
    [self.livePusher setMinVideoBitrate:200]
    /* Obtain the stream ingest status. */
    BOOL isPushing = [self.livePusher isPushing]; 
    /* Obtain the ingest URL. */
    NSString *pushURLString = [self.livePusher getPushURL];
    /* Obtain the debugging information about stream ingest performance. For more information about stream ingest performance parameters, see the API reference or comments. */
    AlivcLivePushStatsInfo *info = [self.livePusher getLivePushStatusInfo];
    /* Obtain the SDK version number. */
    NSString *sdkVersion = [self.livePusher getSDKVersion];
    /* Set a log level to filter debugging information as needed. */
    [self.livePusher setLogLevel:(AlivcLivePushLogLevelDebug)];
    ```


## Use ReplayKit {#section_bnr_5sx_pfb .section}

ReplayKit is a framework introduced in iOS 9 to support screen recording. In iOS 10, you can use third-party application extensions to share the screen content. The Alibaba Cloud ApsaraVideo Live SDK can be used in conjunction with application extensions to support live screencast in iOS 10 and later versions.

-   Create a live streaming application extension

    ReplayKit uses application extensions to implement screen recording. Different from an application, an application extension cannot be published independently. It must be built in a normal application, which is called a container application. However, this application extension is completely independent of its container application. The application extension is started by and communicates with its container application.

    The Alibaba Cloud ApsaraVideo Live demo has provided two application extensions that support live screencast: AlivcLiveBroadcast and AlivcLiveBroadcastSetupUI. To create a live streaming application extension in an application, follow these steps:

    Choose **New** \> **Target…** in your project. In the dialog box that appears, click **Broadcast Upload Extension**, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/156593636855924_en-US.png)

    Modify **Product Name**, select **Include UI Extension**, and then click **Finish** to create a live streaming application extension and live streaming UI, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/156593636855925_en-US.png)

    Configure the live streaming application extension in the **Info.plist** file, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/156593636955926_en-US.png)

    After creating the live streaming application extension, run the container application to automatically install both applications on a mobile phone. After the installation, open an application that supports ReplayKit, such as Tower Dash, and click the live streaming button. Then, available live streaming extensions appear, including the newly created live streaming application extension, as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/156593636955928_en-US.png)

-   Integrate the ApsaraVideo Live SDK
    1.  Add dependencies on the **AlivcLivePusher.framework** and **AlivcLibRtmp.framework** files to the live streaming application extension.
    2.  Modify parameters of the live streaming UI as needed, such as the streaming URL, resolution, and screen orientation, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/156593636955929_en-US.png)

    3.  Use the AlivcLivePusher class to implement live streaming. In iOS, the SampleHandle class provides all methods for live screencast with ReplayKit. You can use the **AlivcLivePusher** class in the Alibaba Cloud ApsaraVideo Live SDK to call relevant methods.
        -   Start stream ingest

            Call the **broadcastStartedWithSetupInfo** method to set stream ingest parameters and start stream ingest. The following example shows the sample code.

            ``` {#codeblock_g26_vm7_k9d}
            - (void)broadcastStartedWithSetupInfo:(NSDictionary<NSString *,NSObject *> *)setupInfo { 
            self.pushConfig = [[AlivcLivePushConfig alloc] init];
            self.livePusher = [[AlivcLivePusher alloc];
            self.pushConfig.externMainStream = true;
            [self.livePusher initWithConfig:self.pushConfig];
            [self.livePusher startPushWithURL:pushUrl];
            }
            ```

        -   Disable stream ingest

            Call the **broadcastPaused** method to disable stream ingest. The following example shows the sample code.

            ``` {#codeblock_ijr_tyn_ov2}
            - (void)broadcastPaused {
            [self.livePusher pause];
            }
            ```

        -   Enable stream ingest

            Call the **broadcastResumed** method to enable stream ingest. The following example shows the sample code.

            ``` {#codeblock_ojx_39c_9w4}
            - (void)broadcastResumed {
            [self.livePusher resume];
            }
            ```

        -   Stop stream ingest

            You can call the **broadcastFinished** method to stop stream ingest. The following example shows the sample code.

            ``` {#codeblock_aod_sly_zck}
            - (void)broadcastFinished {
            [self.livePusher stopPush];
            [self.livePusher destory];
            self.livePusher = nil;
            }
            ```

        -   Send audio and video data

            ``` {#codeblock_h7n_k1w_0jm}
            - (void)processSampleBuffer:(CMSampleBufferRef)sampleBuffer withType:(RPSampleBufferType)sampleBufferType {
            switch (sampleBufferType) {
             case RPSampleBufferTypeVideo:
                 // Handle video sample buffer.
                 [self.livePusher processVideoSampleBuffer:sampleBuffer];
                 break;
             case RPSampleBufferTypeAudioApp:
                 // Handle audio sample buffer for application audio.
                  [self.livePusher processAudioSampleBuffer:sampleBuffer withType:sampleBufferType];
                 break;
             case RPSampleBufferTypeAudioMic:
                 // Handle audio sample buffer for microphone audio.
                 [self.livePusher processAudioSampleBuffer:sampleBuffer withType:sampleBufferType];
                 break;
             default:
                 break;
             }
            }
            ```


## Handle exceptions and special scenarios {#section_yz2_b5x_pfb .section}

-   Handle callback event notifications received through the **AlivcLivePusherErrorDelegate** interface

    -   If you receive an onSystemError event notification, a system error has occurred. You need to stop stream ingest.

    -   If you receive an onSDKError event notification, an SDK error has occurred. You need to destroy the current stream ingest and then restart stream ingest, or call the `restartPush or restartPushAsync` method to restart the `AlivcLivePusher` object.

    -   If you receive any callback event notifications containing the following error code, your application failed to obtain permission to access a microphone or camera: The error code 268455940 indicates that your application failed to obtain permission to access a microphone. The error code 268455939 indicates that your application failed to obtain permission to access a camera.

-   Handle callback event notifications received through the **AlivcLivePusherNetworkDelegate** interface

    -   If you receive an onNetworkPoor event notification, poor network conditions cannot support smooth stream ingest. However, the stream ingest is still in progress and is not disabled. If you receive an `onNetworkRecovery` event notification, the network has recovered. You can add a solution according to your business logic. For example, you can display a message on the UI to remind users.

    -   If you receive an `onConnectFail`, `onReconnectError`, or `onSendDataTimeout` event notification, a network error has occurred. You need to destroy the current stream ingest and then restart stream ingest, or call the `reconnectAsync` method to reconnect to the network. We recommend that you test the network and ingest URL before you reconnect the stream ingest SDK to the network.

    -   If you receive an `onReconnectStart` event notification, the stream ingest SDK has automatically started to reconnect to the network or you have called the `reconnectAsync` method to reconnect to the network. Each time the stream ingest SDK reconnects to the network, it establishes an RTMP connection.

        **Note:** After the RTMP connection has been established, you can receive an onReconnectSuccess event notification. However, this does not mean that stream ingest can be successful. If stream ingest still fails due to network or other errors, the SDK can continue to try reconnecting to the network.

    -   If you receive an `onPushURLAuthenticationOverdue` event notification, your ingest URL is about to expire. If you have enabled stream ingest authentication to carry an auth\_key in an ingest URL, this ingest URL needs to be verified. You can receive this callback event notification about one minute before the ingest URL expires. After you receive it, you must return a new ingest URL. By doing so, you can ensure that stream ingest is not interrupted due to the expiration of an ingest URL. The following example shows the sample code.

``` {#codeblock_hx7_urc_d03}
- (NSString *)onPushURLAuthenticationOverdue:(AlivcLivePusher     *)pusher { 
return @"New ingest URL rtmp://";
}
```

-   Handle callback event notifications related to background music errors received through the **AlivcLivePusherBGMDelegate** interface
    -   If you receive an onOpenFailed event notification, background music failed to start. You need to check the music file and its path, and then call the `startBGMWithMusicPathAsync` method to start playing the music again.

    -   If you receive an `onDownloadTimeout` event notification, background music timed out. This error usually occurs when the music file path is a URL. You need to remind the caster to check network conditions, and then call the `startBGMWithMusicPathAsync` method to start playing the music again.

-   Handle network disconnection

-   Short period of network disconnection or network switchover: Generally, if the network disconnection duration and the number of reconnection attempts are within the ranges as specified through the AlivcLivePushConfig class, the stream ingest SDK automatically reconnects to the network. After the reconnection is successful, the stream ingest SDK enables stream ingest. If you use Alibaba Cloud ApsaraVideo Player, we recommend that you reconnect the player to the network 5s after you receive the `AliVcMediaPlayerPlaybackDidFinishNotification` message.

-   Long period of network disconnection: If the network disconnection duration and the number of reconnection attempts exceed the ranges as specified through the AlivcLivePushConfig class, the stream ingest SDK fails to automatically reconnect to the network. In this case, you receive an `onReconnectError:error:` event notification. After the network is recovered, you can call the `reconnectAsync` method to reconnect to the network. You also need to reconnect Alibaba Cloud ApsaraVideo Player to the network.

    -   We recommend that you monitor the network outside the stream ingest SDK.

    -   A caster and the audience cannot directly communicate with each other on clients, but need to communicate through a server. For example, if the network of the caster's client is disconnected and stream ingest is interrupted, the server receives a callback event notification related to stream ingest interruption from CDN. The server then pushes this event notification to the audience's clients, which can take relevant action. If stream ingest is enabled, the server uses the same method to notify the audience's clients.

    -   To reconnect Alibaba Cloud ApsaraVideo Player to the network, you need to stop and then restart its playing. Call relevant methods in the following sequence: stop \> prepare \> play. The following example shows the sample code.

``` {#codeblock_762_ihe_mw9}
[self.mediaPlayer stop];
AliVcMovieErrorCode err = [self.mediaPlayer prepareToPlay:[NSURL     URLWithString:@"Streaming URL"]];
if(err ! = ALIVC_SUCCESS) {
  NSLog(@"play failed,error code is %d",(int)err);
  return;
}
[self.mediaPlayer play];
```

        **Note:** For more information about the player, see [Basic player \(Live Q&A\)](https://help.aliyun.com/document_detail/61431.html?spm=a2c4g.11186623.2.42.310b592cgeNmuo).

-   Move to the background and answer phone calls

    The stream ingest SDK has configured default solutions when your application is moved to the background. By default, the stream ingest SDK continues audio stream ingest and pauses video stream ingest at the last frame. You need to choose **Capabilities** \> **Background Modes** and select **Audio**, **AirPlay, and Picture in Picture**, as shown in the following figure. This ensures that the stream ingest SDK can continue to collect audio streams after your application is moved to the background. \[DO NOT TRANSLATE\]

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40320/156593637055930_en-US.png)

    To disable stream ingest when your application is moved to the background and enable stream ingest after your application returns to the foreground, you can use either of the following methods:

    -   Mute the audio when your application is moved to the background. You can call the `setMute` method, which is recommended.
    -   Call the `stopPush` method to disable stream ingest when your application is moved to the background. Call the `startPushWithURL` or `startPushWithURLAsync` method to enable stream ingest after your application returns to the foreground.

        **Note:** If you use this method, you must enable the stream ingest SDK to receive the **UIApplicationWillResignActiveNotification** and **UIApplicationDidBecomeActiveNotification** messages. To prevent risks, do not use other methods.

    The following example shows the sample code.

    ``` {#codeblock_3xc_5gj_kkc}
    - (void)addNotifications {
         [[NSNotificationCenter defaultCenter] addObserver:self
                                                  selector:@selector(applicationWillResignActive:)
                                                      name:UIApplicationWillResignActiveNotification
                                               object:nil];
       [[NSNotificationCenter defaultCenter] addObserver:self
                                                     selector:@selector(applicationDidBecomeActive:)
                                                       name:UIApplicationDidBecomeActiveNotification
                                               object:nil]; 
    }
        - (void)applicationWillResignActive:(NSNotification *)notification {
        [self.livePusher stopPush];
    }
       - (void)applicationDidBecomeActive:(NSNotification *)notification {
          [self.livePusher startPushWithURLAsync:pushURL];
    }
    ```

-   Play external audio

    The stream ingest SDK is currently incompatible with the `AudioServicesPlaySystemSound` method of iOS. To play audio on a stream ingest page, we recommend that you use the `AVAudioPlayer` class and update the `AVAudioSession` settings after playing the audio. The following example shows the sample code for AVAudioPlayer.

    ``` {#codeblock_d84_ano_0oi}
    - (void)setupAudioPlayer {
       NSString *filePath = [[NSBundle mainBundle] pathForResource:@"sound" ofType:@"wav"];
       NSURL *fileUrl = [NSURL URLWithString:filePath];
      self.player = [[AVAudioPlayer alloc] initWithContentsOfURL:fileUrl error:nil];
      self.player.volume = 1.0;
      [self.player prepareToPlay];
    }
      - (void)playAudio {
        self.player.volume = 1.0;
        [self.player play];
        // Configure AVAudioSession.
        AVAudioSession *session = [AVAudioSession sharedInstance];
        [session setMode:AVAudioSessionModeVideoChat error:nil];
        [session overrideOutputAudioPort:AVAudioSessionPortOverrideSpeaker error:nil];
        [session setCategory:AVAudioSessionCategoryPlayAndRecord withOptions:AVAudioSessionCategoryOptionDefaultToSpeaker|AVAudioSessionCategoryOptionAllowBluetooth | AVAudioSessionCategoryOptionMixWithOthers error:nil];
        [session setActive:YES error:nil];
    }
    ```

-   Change the size of the view during stream ingest

    Traverse all view objects of the UIView class that you have created when you call the `startPreview` or `startPreviewAsync` method. Modify the value of the frame property for all subviews of the view object. The following example shows the sample code.

    ``` {#codeblock_rpj_82j_pn7}
    [self.livePusher startPreviewAsync:self.previewView];
    for (UIView *subView in [self.previewView subviews]) {
      // ...
    }
    ```

-   Configure the compatibility with iPhone X

    Generally, if you set the frame property of the view object to full screen, the preview can be properly displayed in full screen mode on mobile phones. However, due to the special aspect ratio of the iPhone X screen, the preview screen is distorted when it is displayed in full screen mode on the iPhone X screen. We do not recommend that you display the preview in full screen mode on an iPhone X.

-   Set the bitrate

    The stream ingest SDK supports a dynamic bitrate. You can use the AlivcLivePushConfig class to modify default bitrate settings. Based on the video resolution and fluency requirements of different products, you can set a different value range for the bitrate according to the following rules:

    -   Video resolution: A higher stream ingest bitrate improves the resolution of video streams. Therefore, you can set a high bitrate to guarantee the resolution of video streams.

    -   Video fluency: A higher stream ingest bitrate occupies more network bandwidth. Therefore, if you set a high bitrate under poor network conditions, the fluency of video streams may be affected.


## Important notes {#section_n2s_lvx_pfb .section}

-   Package size
    -   The size of an SDK package is 10.7 MB.

    -   After you integrate the stream ingest SDK, the size of the IPA package increases by about 2.8 MB.

-   Compatible iPhone models
    -   iPhone 5s and later versions, with iOS 8.0 or later versions
-   Constraints
    -   You can set the screen orientation only before stream ingest. You cannot change the screen orientation in real time during stream ingest.

    -   In hardcoding mode, the output resolution must be multiples of 16 in consideration of the encoder compatibility. For example, if you set the resolution to 540p, the output resolution is 544 x 960. You need to scale the screen size of the player according to the output resolution to prevent black edges.

-   Version upgrades
    -   For more information about how to upgrade the stream ingest SDK from V1.3 to V3.0 and upgrade the joint stream SDK to stream ingest SDK V3.0 or a later version, see [SDK upgrade documents](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/45263/cn_zh/1511185890720/updateDoc_i0S_20171120.zip?spm=a2c4g.11186623.2.44.310b592cgeNmuo&file=updateDoc_i0S_20171120.zip).

    -   Stream ingest SDK V3.3.4 and later versions are no longer compatible with stream ingest SDK V1.3. We recommend that you remove the earlier version and install the latest SDK version.


