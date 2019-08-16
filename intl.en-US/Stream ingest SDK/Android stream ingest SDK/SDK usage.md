# SDK usage {#concept_zy5_myx_pfb .concept}

This topic describes how to use the Android stream ingest SDK.

The basic procedure for using the stream ingest SDK is as follows:

1.  Set stream ingest parameters.
2.  Create a stream ingest preview.
3.  Start stream ingest.
4.  Adjust stream ingest parameters in real time as needed.

## Stream ingest parameter settings {#section_fpb_zyx_pfb .section}

You can use the AlivcLivePushConfig class to set stream ingest parameters. Each parameter has a default value. For more information about parameter default values and value ranges, see the API reference or comments. You can modify the values of these parameters as needed. For more information about how to modify these parameters in real time during stream ingest, see the properties and methods provided by the AlivcLivePusher class.

-   Basic configuration

    ``` {#codeblock_an5_5pq_ua5}
    AlivcLivePushConfig mAlivcLivePushConfig = new AlivcLivePushConfig(); // Initialize the AlivcLivePushConfig class.
    mAlivcLivePushConfig.setResolution(AlivcResolutionEnum.RESOLUTION_540P); // Set the resolution to 540p. The maximum resolution is 720p.
    mAlivcLivePushConfig.setFps(AlivcFpsEnum.FPS_20); // We recommend that you set the frame rate to 20 fps.
    mAlivcLivePushConfig.setEnableBitrateControl(true); // Enable bitrate control. The default value is true.
    mAlivcLivePushConfig.setPreviewOrientation(AlivcPreviewOrientationEnum.ORIENTATION_PORTRAIT); // Keep the default value to set the screen orientation to portrait. You can also set the screen orientation to landscape left or landscape right.
    mAlivcLivePushConfig.setAudioProfile(AlivcAudioAACProfileEnum.AlivcAudioAACProfileEnum.AAC_LC); // Set the audio coding mode.
    mAlivcLivePushConfig.setEnableBitrateControl(true); // Enable bitrate control. The default value is true.
    ```

    **Note:** 

    -   All these parameters have default values. We recommend that you use the default values.
    -   Considering the performance of most mobile phones and network bandwidth requirements, we recommend that you set the resolution to 540p. Most mainstream live streaming applications use 540p.
    -   If bitrate control is disabled, the bitrate is fixed to the initial value and cannot be automatically adjusted between the specified target bitrate and minimum bitrate. If the network is unstable, the fixed bitrate may cause video stalling. You need to disable bitrate control with caution.
-   Bitrate control

    The stream ingest SDK provides three bitrate control modes. You can modify the AlivcQualityModeEnum parameter to one of the following values:

    -   **QM\_RESOLUTION\_FIRST**: indicates the resolution-first mode in which the stream ingest SDK sets the bitrate to prioritize the resolution of video streams.

    -   **QM\_FLUENCY\_FIRST**: indicates the fluency-first mode in which the stream ingest SDK sets the bitrate to prioritize the fluency of video streams.

    -   **QM\_CUSTOM**: indicates the custom mode in which the stream ingest SDK sets the bitrate based on your custom bitrate settings.

    The following example shows the sample code for the resolution-first or fluency-first mode.

    ``` {#codeblock_lqs_729_8h1}
    mAlivcLivePushConfig.setQualityMode(AlivcQualityModeEnum.QM_RESOLUTION_FIRST);
    ```

    **Note:** If you set the value to **QM\_RESOLUTION\_FIRST** or **QM\_FLUENCY\_FIRST**, you do not need to set the `targetVideoBitrate`, `minVideoBitrate`, and `initialVideoBitrate` parameters. The stream ingest SDK can automatically set the bitrate based on packet delay variation to give priority to the resolution or fluency of video streams.

    The following example shows the sample code for the custom mode.

    ``` {#codeblock_sds_rej_zqx}
    mAlivcLivePushConfig.setQualityMode(AlivcQualityModeEnum.QM_CUSTOM);
    mAlivcLivePushConfig.setTargetVideoBitrate(1200); // Set the target bitrate to 1200 Kbit/s.
    mAlivcLivePushConfig.setMinVideoBitrate(400); // Set the minimum bitrate to 400 Kbit/s.
    mAlivcLivePushConfig.setInitialVideoBitrate(900); // Set the initial bitrate to 900 Kbit/s.
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

    ``` {#codeblock_gbs_0b2_yu5}
    mAlivcLivePushConfig.setEnableAutoResolution(true); // Enable dynamic resolution. The default value is false.
    ```

    **Note:** Dynamic resolution takes effect only in resolution-first or fluency-first mode. You must set the AlivcQualityModeEnum parameter to QM\_RESOLUTION\_FIRST or QM\_FLUENCY\_FIRST. Dynamic resolution does not take effect in custom mode.

    The stream ingest SDK provides two face filters: basic and advanced. The basic face filter supports skin whitening, skin smoothing, and skin shining. The advanced face filter supports facial recognition–based skin whitening, skin smoothing, skin shining, eye widening, chin slimming, face thinning, and cheek blushing. To use the advanced face filter, you must set the AlivcBeautyLevelEnum parameter to `BEAUTY_Professional` and import facial recognition resources into your project.

    To integrate the face filter feature, you can import a face filter library in either of the following ways:

    1.  Import AAR packages: live-face-beauty\*.aar
    2.  Import JAR packages and SO files:
    Basic face filter: live-beauty.jar + libAliEffectModule.so + liblive-beauty.so

    Advanced face filter: live-beauty.jar + libAliEffectModule.so + liblive-beauty.so + live-face.jar + liblive-face.so + libAliFaceAlignmentModule.so

    In addition, you need to configure callback event notifications in the code.

    ``` {#codeblock_3sl_k88_qdw}
    /**
    * Configure callback event notifications for facial recognition. This configuration is not required if you integrate only the basic face filter.
    **/
    mAlivcLivePusher.setCustomDetect(new AlivcLivePushCustomDetect()
    {
       @Override
      public void customDetectCreate() {
          taoFaceFilter = new TaoFaceFilter(getApplicationContext());
          taoFaceFilter.customDetectCreate();
      }
      @Override
      public long customDetectProcess(long data, int width, int height, int rotation, int format, long extra) {
          if(taoFaceFilter ! = null) {
              return taoFaceFilter.customDetectProcess(data, width, height, rotation, format, extra);
          }
          return 0;
      }
      @Override
      public void customDetectDestroy() {
          if(taoFaceFilter ! = null) {
              taoFaceFilter.customDetectDestroy();
          }
      }
    });
    /**
    * Configure callback event notifications for face filter.
    **/
    mAlivcLivePusher.setCustomFilter(new AlivcLivePushCustomFilter() 
    {
       @Override
      public void customFilterCreate() {
          taoBeautyFilter = new TaoBeautyFilter();
          taoBeautyFilter.customFilterCreate();
      }
      @Override
      public void customFilterUpdateParam(float fSkinSmooth, float fWhiten, float fWholeFacePink, float fThinFaceHorizontal, float fCheekPink, float fShortenFaceVertical, float fBigEye) {
          if (taoBeautyFilter ! = null) {
              taoBeautyFilter.customFilterUpdateParam(fSkinSmooth, fWhiten, fWholeFacePink, fThinFaceHorizontal, fCheekPink, fShortenFaceVertical, fBigEye);
          }
      }
      @Override
      public void customFilterSwitch(boolean on)
      {
          if(taoBeautyFilter ! = null) {
              taoBeautyFilter.customFilterSwitch(on);
          }
      }
      @Override
      public int customFilterProcess(int inputTexture, int textureWidth, int textureHeight, long extra) {
          if (taoBeautyFilter ! = null) {
              return taoBeautyFilter.customFilterProcess(inputTexture, textureWidth, textureHeight, extra);
          }
          return inputTexture;
      }
      @Override
      public void customFilterDestroy() {
          if (taoBeautyFilter ! = null) {
              taoBeautyFilter.customFilterDestroy();
          }
          taoBeautyFilter = null;
      }
    });
    ```

    To use the basic face filter, you do not need to import facial recognition resources. The following example shows the sample code.

    ``` {#codeblock_i6b_9av_93l}
    mAlivcLivePushConfig.setBeautyOn(true); // Enable face filter.
    mAlivcLivePushConfig.setBeautyLevel(AlivcBeautyLevelEnum.BEAUTY_Normal); // Select the basic face filter.
    mAlivcLivePushConfig.setBeautyWhite(70); // Set the intensity of skin whitening in the range of 0 to 100.
    mAlivcLivePushConfig.setBeautyBuffing(40); // Set the intensity of skin smoothing in the range of 0 to 100.
    mAlivcLivePushConfig.setBeautyRuddy(40); // Set the intensity of skin shining in the range of 0 to 100.
    ```

    To use the advanced face filter, you must import facial recognition resources. The following example shows the sample code.

    ``` {#codeblock_pme_e07_ah8}
    mAlivcLivePushConfig.setBeautyOn(true); // Enable face filter.
    mAlivcLivePushConfig.setBeautyLevel(AlivcBeautyLevelEnum.BEAUTY_Professional); // Select the advanced face filter.
    mAlivcLivePushConfig.setBeautyWhite(70); // Set the intensity of skin whitening in the range of 0 to 100.
    mAlivcLivePushConfig.setBeautyBuffing(40); // Set the intensity of skin smoothing in the range of 0 to 100.
    mAlivcLivePushConfig.setBeautyRuddy(40); // Set the intensity of skin shining in the range of 0 to 100.
    mAlivcLivePushConfig.setBeautyThinFace(40); // Set the intensity of face thinning in the range of 0 to 100.
    mAlivcLivePushConfig.setBeautyBigEye(30); // Set the intensity of eye widening in the range of 0 to 100.
    mAlivcLivePushConfig.setBeautyShortenFace(50); // Set the intensity of chin slimming in the range of 0 to 100.
    mAlivcLivePushConfig.setBeautyCheekPink(15); // Set the intensity of cheek blushing in the range of 0 to 100.
    ```

    **Note:** With the help of the Alibaba Cloud user experience design \(UED\) team, we recommend that you try out different parameter settings to find those that best suit your needs.

    The following table lists the optimal face filter parameter settings for your reference.

    |Setting|Skin smoothing|Skin whitening|Skin shining|Eye widening|Face thinning|Chin slimming|Cheek blushing|
    |:------|:-------------|:-------------|:-----------|:-----------|:------------|:------------|:-------------|
    |One|40|35|10|0|0|0|0|
    |Two|60|80|20|0|0|0|0|
    |Three|50|100|20|0|0|0|0|
    |Four|40|70|40|30|40|50|15|
    |Five|70|100|10|30|40|50|0|

    **Note:** If you import a third-party face filter library, you can call the setCustomDetect and setCustomFilter methods to configure callback event notifications. The parameters are described as follows:

    -   When you use the AlivcLivePushCustomDetect class to call the callback function customDetectProcess\(long data, int width, int height, int rotation, int format, long extra\), the data parameter returned indicates the pointer for data collection. The third-party face filter library can identify or process the data that the pointer points to.
    -   When you use the AlivcLivePushCustomFilter class to call the callback function customFilterProcess\(int inputTexture, int textureWidth, int textureHeight, long extra\), the inputTexture parameter returned indicates the image texture. The third-party face filter library can process image texture. If any image texture has been processed, the texture ID is returned. Otherwise, the inputTexture parameter is returned.
-   Image stream ingest

    To improve user experience, the stream ingest SDK supports image stream ingest when your application is moved to the background or detects a low bitrate. When your application is moved to the background, the stream ingest SDK disables video stream ingest and ingests only audio streams by default. In this case, you can specify images to ingest image streams and audio streams. For example, you can display an image to remind users that the caster is away for the moment and will come back soon. The following example shows the sample code.

    ``` {#codeblock_sk2_f5e_g3x}
    mAlivcLivePushConfig.setPausePushImage (Path of the PNG file); // Specify the image for image stream ingest when an application is moved to the background.
    ```

    In addition, you can specify a static image as needed for image stream ingest under poor network conditions. In this case, the stream ingest SDK can enable image stream ingest at a low bitrate to push only this image and avoid video stalling. The following example shows the sample code.

    ``` {#codeblock_cz6_khn_0pf}
    mAlivcLivePushConfig.setNetworkPoorPushImage (Path of the PNG file); // Specify the image for image stream ingest under poor network conditions.
    [DO NOT TRANSLATE]
    ```

-   Watermarks

    The stream ingest SDK allows you to add one or more watermarks, the source of which must be PNG files. The following example shows the sample code.

    ``` {#codeblock_x6a_3vy_ibr}
    mAlivcLivePushConfig.addWaterMark(waterPath, 0.1, 0.2, 0.3); // Add a watermark.
    ```

    **Note:** 

    -   The x, y, and width parameters are set to relative values. For example, `x:0.1` indicates that the x parameter value of the watermark is at the 10% position on the x-axis of the stream ingest screen. Therefore, if the stream ingest resolution is 540 x 960, the x parameter is set to 54.

    -   The height of the watermark is calculated based on the specified width parameter value with an aspect ratio equal to that of the source image.

    -   To add a text watermark, you can convert text into an image, and then call the addWaterMark method to add the image as a watermark.

-   Configuration for Android devices other than Android mobile phones

    For some Android devices such as set-top boxes \(STBs\), the following configuration items are added:

    You can customize camera rotation angles.

    ``` {#codeblock_tne_gb4_401}
    mAlivcLivePushConfig.setPreviewRotation(AlivcPreviewRotationEnum rotation); // Set a rotation angle for camera preview.
    ```

    The stream ingest SDK provides a sensor that can sense motions to facilitate real-time autofocus.

    ``` {#codeblock_i1d_hux_pvt}
    mAlivcLivePushConfig.setFocusBySensor(true);
    ```

    **Note:** These two methods do not apply to Android mobile phones.

-   Preview mode

    ``` {#codeblock_not_x1k_j35}
    mAlivcLivePushConfig.setPreviewDisplayMode(AlivcPreviewDisplayMode.ALIVC_LIVE_PUSHER_PREVIEW_ASPECT_FIT);
    ```

    -   AlivcPreviewDisplayMode.ALIVC\_LIVE\_PUSHER\_PREVIEW\_SCALE\_FILL: indicates that the stream ingest SDK adjusts the video size to fill the screen for a preview. If the aspect ratio of the video is different from that of the preview screen, the preview image is distorted.

    -   AlivcPreviewDisplayMode.ALIVC\_LIVE\_PUSHER\_PREVIEW\_ASPECT\_FIT: indicates that the stream ingest SDK maintains the aspect ratio of the video for a preview. If the aspect ratio of the video is different from that of the preview screen, each blank edge is displayed in black.

    -   AlivcPreviewDisplayMode.ALIVC\_LIVE\_PUSHER\_PREVIEW\_ASPECT\_FILL: indicates that the stream ingest SDK crops the video to fit the screen for a preview. If the aspect ratio of the video is different from that of the preview screen, the video is cropped for the preview.

        **Note:** These preview modes do not affect stream ingest.


## AlivcLivePusher {#section_qsb_zyx_pfb .section}

The AlivcLivePusher class is a core class of the stream ingest SDK. It provides camera preview, stream ingest callback, stream ingest control, parameter adjustment during stream ingest, and other features.

**Note:** 

-   You can add the try…catch syntax to handle exceptions thrown after you call relevant methods.
-   You must follow the specified sequence to call relevant methods to avoid exceptions caused by an incorrect sequence.

-   Initialize an AlivcLivePusher object

    After setting stream ingest parameters, you can call the `init` method provided by the stream ingest SDK to initialize an AlivcLivePusher object. The following example shows the sample code.

    ``` {#codeblock_smm_1lv_h6w}
    AlivcLivePusher mAlivcLivePusher = new AlivcLivePusher();
    mAlivcLivePusher.init(mContext, mAlivcLivePushConfig);
    ```

    **Note:** Currently, the AlivcLivePusher class does not support multiple instances. You must call a destroy method each time after calling an init method.

-   Register stream ingest callback event notifications

    Stream ingest callback event notifications are classified into Info, Error, and Network. Info callback event notifications are used to send messages and detect status. Error callback event notifications are used to notify errors. Network callback event notifications are used to notify the network status. After you register a callback event notification, the corresponding callback function can be triggered if the event occurs. The following example shows the sample code.

    ``` {#codeblock_0tu_pou_wr0}
    /**
      * Configure callback event notifications for stream ingest errors.
      *
      * @param errorListener // The error listener.
      */
    mAlivcLivePusher.setLivePushErrorListener(new AlivcLivePushErrorListener() {
      @Override
      public void onSystemError(AlivcLivePusher livePusher, AlivcLivePushError error) {
          if(error ! = null) {
              // Add a UI message or user-defined error solution.
          }
      }
      @Override
      public void onSDKError(AlivcLivePusher livePusher, AlivcLivePushError error) {
          if(error ! = null) {
              // Add a UI message or user-defined error solution.
          }
      }
    });
    /**
    * Configure callback event notifications for stream ingest.
    *
    * @param infoListener // The notification listener.
    */
    mAlivcLivePusher.setLivePushInfoListener(new AlivcLivePushInfoListener() {
      @Override
      public void onPreviewStarted(AlivcLivePusher pusher) {
          // Indicates that a preview starts.
      }
      @Override
      public void onPreviewStoped(AlivcLivePusher pusher) {
          // Indicates that a preview stops.
      }
      @Override
      public void onPushStarted(AlivcLivePusher pusher) {
          // Indicates that stream ingest starts.
      }
      @Override
      public void onPushPauesed(AlivcLivePusher pusher) {
          // Indicates that stream ingest is disabled.
      }
      @Override
      public void onPushResumed(AlivcLivePusher pusher) {
          // Indicates that stream ingest is enabled.
      }
      @Override
      public void onPushStoped(AlivcLivePusher pusher) {
          // Indicates that stream ingest stops.
      }
      @Override
      public void onPushRestarted(AlivcLivePusher pusher) {
          // Indicates that stream ingest restarts.
      }
      @Override
      public void onFirstFramePreviewed(AlivcLivePusher pusher) {
          // Indicates first-frame rendering.
      }
      @Override
      public void onDropFrame(AlivcLivePusher pusher, int countBef, int countAft) {
          // Indicates that frames are discarded.
      }
      @Override
      public void onAdjustBitRate(AlivcLivePusher pusher, int curBr, int targetBr) {
          // Indicates that the bitrate is adjusted.
      }
      @Override
      public void onAdjustFps(AlivcLivePusher pusher, int curFps, int targetFps) {
          // Indicates that the frame rate is adjusted.
      }
    });
    /**
    * Configure callback event notifications for the network.
    *
    * @param infoListener // The notification listener.
    */
    mAlivcLivePusher.setLivePushNetworkListener(new AlivcLivePushNetworkListener() {
      @Override
      public void onNetworkPoor(AlivcLivePusher pusher) {
          // Indicates poor network conditions.
      }
      @Override
      public void onNetworkRecovery(AlivcLivePusher pusher) {
          // Indicates that the network is recovered.
      }
      @Override
      public void onReconnectStart(AlivcLivePusher pusher) {
          // Indicates that a reconnection starts.
      }
      @Override
      public void onReconnectFail(AlivcLivePusher pusher) {
          // Indicates that a reconnection failed.
      }
      @Override
      public void onReconnectSucceed(AlivcLivePusher pusher) {
          // Indicates that a reconnection is successful.
      }
      @Override
      public void onSendDataTimeout(AlivcLivePusher pusher) {
          // Indicates that data transmission times out.
      }
      @Override
      public void onConnectFail(AlivcLivePusher pusher) {
          // Indicates that a connection failed.
      }
    });
    /**
    * Configure callback event notifications for the playing of background music.
    *
    * @param pushBGMListener // The notification listener.
    */
    mAlivcLivePusher.setLivePushBGMListener(new AlivcLivePushBGMListener() {
      @Override
      public void onStarted() {
          // Indicates that background music starts.
      }
      @Override
      public void onStoped() {
          // Indicates that background music stops.
      }
      @Override
      public void onPaused() {
          // Indicates that background music is paused.
      }
      @Override
      public void onResumed() {
          // Indicates that background music is resumed.
      }
      /**
       * Configure callback event notifications for the playing progress of background music.
       *
       * @param progress // The playing progress.
       */
      @Override
      public void onProgress(final long progress, final long duration) {
      @Override
      public void onCompleted() {
          // Indicates that background music ends.
      }
      @Override
      public void onDownloadTimeout() {
          // Indicates that the player times out. You can enable the player to automatically reconnect to the music file URL and seek the playing position.
      }
      @Override
      public void onOpenFailed() {
          // Indicates that audio streams are invalid. You can remind users that audio streams are inaccessible.
      }
    });
    ```

-   Start a preview

    You can start a preview after you initialize the AlivcLivePusher object. You need to set the SurfaceView parameter for camera preview. The following example shows the sample code.

    ``` {#codeblock_tzm_10e_vcj}
    mAlivcLivePusher.startPreview(mSurfaceView) // Start a preview. You can also call the startPreviewAysnc method to start the preview asynchronously as needed.
    ```

-   Start stream ingest

    The stream ingest SDK can start stream ingest only after a successful preview. Therefore, you need to add the following code when you configure the `onPreviewStarted` event notification:

    ``` {#codeblock_yrd_1l4_4qc}
    mAlivcLivePusher.startPush(mPushUrl);
    ```

    **Note:** 

    -   The stream ingest SDK also provides the `startPushAysnc` method to support asynchronous stream ingest.

    -   The stream ingest SDK supports RTMP-based ingest URLs. For more information about how to obtain an Alibaba Cloud ingest URL, see [Quick Start](../../../../intl.en-US/User Guide (New console)/Quick start.md#).

    -   After starting stream ingest based on a correct ingest URL, you can use a player, such as Alibaba Cloud ApsaraVideo Player, FFplay, or VLC, to run a stream pulling test. For more information about how to obtain a source URL, see [Quick Start](../../../../intl.en-US/User Guide (New console)/Quick start.md#).

-   Control stream ingest

    To control stream ingest, you can start stream ingest, stop stream ingest, stop a preview, restart stream ingest, disable stream ingest, enable stream ingest, and destroy stream ingest. You can add buttons as needed to perform these operations. The following example shows the sample code.

    ``` {#codeblock_lzk_1fa_bf3}
    /* Call this method to disable ongoing stream ingest. Then, the stream ingest SDK pauses the video preview and video stream ingest at the last frame, and continues audio stream ingest. */
    mAlivcLivePusher.pause();
    /* Call this method to enable disabled stream ingest. Then, the stream ingest SDK resumes the audio and video preview and stream ingest. */
    mAlivcLivePusher.resume();
    /* Call this method to stop ongoing stream ingest. Then, the stream ingest SDK stops stream ingest. */
    mAlivcLivePusher.stopPush();
    /* Call this method to stop an ongoing preview. However, you cannot call this method to stop a preview during stream ingest. After you call this method, the stream ingest SDK freezes the preview screen at the last frame. */
    mAlivcLivePusher.stopPreview();
    /* Call this method to restart stream ingest during stream ingest or after you receive any callback event notification related to an error. When such an error occurs, you can only call this method to restart stream ingest, call the reconnectPushAsync method to reconnect to the network, or call the destroy method to destroy stream ingest. After you call this method, the stream ingest SDK restarts stream ingest, and restarts all resources of the AlivcLivePusher object, including preview frames and ingest streams. */
    mAlivcLivePusher.restartPush();
    /* Call this method to reconnect to the network during stream ingest or after you receive any callback event notification related to an error through the AlivcLivePusherNetworkDelegate interface. When such an error occurs, you can only call this method to reconnect to the network, call the restartPush method to restart stream ingest, or call the destroy method to destroy stream ingest. After you call this method, the stream ingest SDK establishes an RTMP connection again. */
    mAlivcLivePusher.reconnectPushAsync();
    /* Call this method to destroy stream ingest. Then, the stream ingest SDK stops the stream ingest and preview, removes the preview screen, and destroys all resources related to the AlivcLivePusher object. */
    mAlivcLivePusher.destroy();
    ```

-   Adjust face filter parameters

    The stream ingest SDK allows you to adjust face filter parameters in real time during stream ingest. You can adjust parameters for the basic and advanced face filters separately. The following example shows the sample code.

    ``` {#codeblock_9du_i39_rgr}
    mAlivcLivePusher.setBeautyOn(true); // Enable or disable face filter.
    /* For the basic face filter, adjust the following parameters: */
    mAlivcLivePusher.setBeautyWhite(70); // Set the intensity of skin whitening in the range of 0 to 100.
    mAlivcLivePusher.setBeautyBuffing(40); // Set the intensity of skin smoothing in the range of 0 to 100.
    mAlivcLivePusher.setBeautyRuddy(40); // Set the intensity of skin shining in the range of 0 to 100.
    /* In addition to parameters for the basic face filter, adjust the following parameters for the advanced face filter: */
    mAlivcLivePusher.setBeautyThinFace(40); // Set the intensity of face thinning in the range of 0 to 100.
    mAlivcLivePusher.setBeautyBigEye(30); // Set the intensity of eye widening in the range of 0 to 100.
    mAlivcLivePusher.setBeautyShortenFace(50); // Set the intensity of chin slimming in the range of 0 to 100.
    mAlivcLivePusher.setBeautyCheekPink(15); // Set the intensity of cheek blushing in the range of 0 to 100.
    ```

-   Control background music

    The stream ingest SDK allows you to play background music and provides the audio mixing, noise reduction, in-ear monitoring, mute, and other features for background music. You can call relevant methods only after starting a preview. The following example shows the sample code.

    ``` {#codeblock_odw_qzl_kin}
    /* Start playing background music. */
    mAlivcLivePusher.startBGMAsync(mPath);
    /* Stop playing background music. To change the current background music, call the startBGMAsync method to start playing the new background music. You do not need to stop the current background music. */
    mAlivcLivePusher.stopBGMAsync();
    /* Pause background music. You can call this method only when the background music is being played. */
    mAlivcLivePusher.pauseBGM();
    /* Resume background music. You can call this method only when the background music is paused. */
    mAlivcLivePusher.resumeBGM();
    /* Start playing a music loop. */
    mAlivcLivePusher.setBGMLoop(true);
    /* Configure noise reduction. If you enable noise reduction, the stream ingest SDK filters out non-vocal parts from collected audio. This feature may slightly reduce the volume of vocals. Therefore, we recommend that you enable this feature as needed. This feature is disabled by default. */
    mAlivcLivePusher.setAudioDenoise(true);
    /* Configure in-ear monitoring. In-ear monitoring mainly applies to KTV scenarios. If you enable in-ear monitoring, you can hear your own voice from your earpieces. If you disable in-ear monitoring, you cannot hear your own voice from your earpieces. This feature does not work without earpieces. */
    mAlivcLivePusher.setBGMEarsBack(true);
    /* Configure audio mixing to adjust the volume of background music and vocals separately. */
    mAlivcLivePusher.setBGMVolume(50); // Adjust the volume of background music.
    mAlivcLivePusher.setCaptureVolume(50); // Adjust the volume of vocals.
    /* Configure mute. If you enable this feature, the stream ingest SDK mutes both music and vocals. To mute music or vocals separately, you can call a method related to audio mixing to adjust the volume of music or vocals separately. */
    mAlivcLivePusher.setMute(true);
    ```

-   Perform camera-related operations

    You can perform camera-related operations only after starting a preview in the following scenarios: during stream ingest, when stream ingest is disabled, or the stream ingest SDK is reconnecting to the network. For example, you can switch between the front camera and rear camera, control the flash, adjust the focal length, configure focus, and configure mirroring. If you have not started a preview, the following methods do not take effect. The following example shows the sample code.

    ``` {#codeblock_57l_p7o_hfz}
    /* Switch between the front camera and rear camera. */
    mAlivcLivePusher.switchCamera();
    /* Turn on or turn off the flash. You cannot turn on the flash for the front camera. */
    mAlivcLivePusher.setFlash(true); 
    /* Adjust the focal length to zoom in and zoom out for collected streams. The zooming ranges from 0 to getMaxZoom(). */
    mAlivcLivePusher.setZoom(5); 
    /* Configure manual focus. You need to set two parameters: point and autoFocus. The point parameter indicates the coordinates of the point to be focused on. The autoFocus parameter indicates whether to enable autofocus and takes effect only for the current focusing operation. Whether autofocus is enabled for subsequent operations depends on the autofocus configuration after you call the setAutoFocus method. */
    mAlivcLivePusher.focusCameraAtAdjustedPoint(x, y, true);
    /* Configure autofocus. */
    mAlivcLivePusher.setAutoFocus(true);
    /* Configure mirroring. You can set the PushMirror or PreviewMirror parameter to configure mirroring. The PushMirror parameter is valid only for the streaming screen, whereas the PreviewMirror parameter is valid only for the preview screen. They are mutually independent. */
    mAlivcLivePusher.setPreviewMirror(false);
    mAlivcLivePusher.setPushMirror(false);
    ```

-   Implement live Q&A

    To implement live Q&A, you can insert SEI into live streams and use a player to parse the SEI. The stream ingest SDK provides a method for you to insert SEI. You can call this method only during stream ingest. The following example shows the sample code.

    ``` {#codeblock_zqq_4eo_9cp}
    /*
    info: the message body of the SEI to be inserted into live streams. We recommend that you use the JSON format. The Alibaba Cloud ApsaraVideo Player SDK can receive and parse this SEI and display the parsed content.
    repeat: the number of frames into which the SEI is inserted. To avoid SEI loss due to frame discard, the same SEI must be inserted into multiple frames. If this parameter is set to 100, the same SEI is inserted into the next 100 frames. The player can remove duplicate SEI.
    delay: the interval for sending frames that contain the SEI, measured in milliseconds.
    isKeyFrame: indicates whether to insert the SEI only into keyframes.
    */
    mAlivcLivePusher.sendMessage("Questions", 100, 0, false)
    ```

-   Configure external audio and video input

    The stream ingest SDK supports external audios and videos for stream ingest, such as an audio and video file, or audio and video data collected by third-party devices. The procedure is as follows:

    1.  Use the AlivcLivePushConfig class to set parameters for the external audio and video input. The following example shows the sample code.

``` {#codeblock_v14_0x9_l07}
/**
* AlivcImageFormat: the format of input video images.
* AlivcSoundFormat: the format of input audio frames.
* Other parameters: To specify the output resolution, the audio sampling rate, and the number of audio channels, you can call the setResolution, setAudioSamepleRate, and setAudioChannels methods.
[DO NOT TRANSLATE]
* Note: To use custom video and audio streams as the input, you need to call the inputStreamVideoData and inputStreamAudioData methods.
*/
mAlivcLivePushConfig.setExternMainStream(true,AlivcImageFormat.IMAGE_FORMAT_YUVNV12, AlivcSoundFormat.SOUND_FORMAT_S16);
```

    2.  Insert external video data. The following example shows the sample code.

        ``` {#codeblock_9pu_dvq_osl}
        /**
        * Use custom video streams as the input.
        *
        * @param data // The byte array of video images.
        * @param width // The width of video images.
        * @param height // The height of video images.
        * @param size // The size of video images.
        * @param pts // The presentation timestamp (PTS) of video images, measured in microseconds.
        * @param rotation // The rotation angle of video images.
        * This method does not control the time sequence. You need to control the time sequence of input video frames.
        * Note: Before calling this method, you need to use the AlivcLivePushConfig class to call the setExternMainStream(true,***) method.
        */
        mAlivcLivePusher.inputStreamVideoData(buffer, 720, 1280, 1280*720*3/2, System.nanoTime()/1000, 0);
        /**
        * Use custom video streams as the input.
        *
        * @param dataptr // The native memory pointer for video images.
        * @param width // The width of video images.
        * @param height // The height of video images.
        * @param size // The size of video images.
        * @param pts // The PTS of video images, measured in microseconds.
        * @param rotation // The rotation angle of video images.
        * This method does not control the time sequence. You need to control the time sequence of input video frames.
        * Note: Before calling this method, you need to use the AlivcLivePushConfig class to call the setExternMainStream(true,***) method.
        */
        mAlivcLivePusher.inputStreamVideoPtr(long dataptr, int width, int height, int size, long pts, int rotation);
        ```

    3.  Insert external audio data. The following example shows the sample code.

        ``` {#codeblock_2ts_coq_le4}
        /**
        * Use custom audio data as the input.
        * @param data // The byte array of audio data.
        * @param size
        * @param pts // The PTS of audio data, measured in microseconds.
        * This method does not control the time sequence. You need to control the time sequence of input audio frames.
        */
        mAlivcLivePusher.inputStreamAudioData(buffer, 2048, System.nanoTime()/1000);
        /**
        * Use custom audio data as the input.
        * @param dataPtr // The native memory pointer for audio data.
        * @param size
        * @param pts // The PTS of audio data, measured in microseconds.
        * This method does not control the time sequence. You need to control the time sequence of input audio frames.
        */
        AlivcLivePusher.inputStreamAudioPtr(long dataPtr, int size, long pts);
        ```

-   Configure animated stickers

    The stream ingest SDK allows you to add animated stickers to live streams so as to add dynamic watermarks.

    -   To prepare an animated sticker, you can modify materials provided in the demo. Prepare sequential images for the animated sticker and open the config.json file to customize relevant parameters.

``` {#codeblock_pon_bf4_8bp}
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

        ``` {#codeblock_e97_yuu_rz4}
        /**
        * Add an animated sticker.
        * @param path // The path of the sticker, which must contain the config.json file.
        * @param x // The start position of the sticker on the x-axis of the screen, in the range of 0f to 1.0f.
        * @param y // The start position of the sticker on the y-axis of the screen, in the range of 0f to 1.0f.
        * @param w // The width of the sticker on the screen, in the range of 0f to 1.0f.
        * @param h // The height of the sticker on the screen, in the range of 0f to 1.0f.
        * @return id // The returned sticker ID, which can be used to delete the specified sticker.
        */
        mAlivcLivePusher.addDynamicsAddons("Path of the sticker", 0.2f, 0.2f, 0.2f, 0.2f);
        ```

    -   Delete an animated sticker. The following example shows the sample code.

        ``` {#codeblock_xcu_ljl_xrj}
        mAlivcLivePusher.removeDynamicsAddons(int id);
        ```

-   Use the debugging tool

    The stream ingest SDK provides a UI-based debugging tool DebugView to help you diagnose problems. DebugView shows a draggable floating window that always appears on top of others on the screen. It provides multiple debugging features for you to view stream ingest logs, monitor the performance parameters of stream ingest in real time, and view a line chart of key stream ingest performance. The following example shows the sample code.

    ``` {#codeblock_vo9_q15_7d1}
    AlivcLivePusher.showDebugView(context); // Show DebugView.
    AlivcLivePusher.hideDebugView(context); // Hide DebugView.
    ```

    **Note:** For your application to be published, you only need to add a button to hide DebugView.

-   Call other methods

    ``` {#codeblock_vca_9cc_ppf}
    /* In custom bitrate control mode, adjust the minimum bitrate and target bitrate in real time. */
    mAlivcLivePusher.setTargetVideoBitrate(800);
    mAlivcLivePusher.setMinVideoBitrate(400);
    /* Configure whether to support autofocus. */
    mAlivcLivePusher.isCameraSupportAutoFocus();
    /* Configure whether to support the flash. */
    mAlivcLivePusher.isCameraSupportFlash();
    /* Obtain the stream ingest status. */
    mAlivcLivePusher.isPushing(); 
    /* Obtain the ingest URL. */
    mAlivcLivePusher.getPushUrl();
    /* Obtain the debugging information about stream ingest performance. For more information about stream ingest performance parameters, see the API reference or comments. */
    mAlivcLivePusher.getLivePushStatsInfo();
    /* Obtain the SDK version number. */
     mAlivcLivePusher.getSDKVersion();
    /* Set a log level to filter debugging information as needed. */
    mAlivcLivePusher.setLogLevel(AlivcLivePushLogLevelAll);
    /* Obtain the status of the stream ingest SDK. */
    AlivcLivePushStats getCurrentStatus();
    /* Obtain the last error code. If no error has occurred, ALIVC_COMMON_RETURN_SUCCESS is returned. */
    AlivcLivePushError getLastError();
    ```


## Screen recording {#section_ovv_2zx_pfb .section}

-   Select a screen recording mode

    The stream ingest SDK provides the following three screen recording modes:

    -   Screen recording with the camera disabled: After receiving the response data of a permission request, use the AlivcLivePushConfig class to call the relevant method with the response data as its parameter to enable screen recording.

    -   Screen recording with the camera enabled: A caster has a camera preview and the audience can view the caster's camera-shot content, which is also recorded during screen recording.

        1.  After receiving the response data of a permission request, use the AlivcLivePushConfig class to call the relevant method with the response data as its parameter to enable screen recording.

        2.  Call the StartCamera method and set the surfaceView parameter.

    -   Screen recording with the camera enabled: A caster does not have a camera preview, but the audience can still view the caster's camera-shot content, which is pushed through stream mixing.

        1.  After receiving the response data of a permission request, use the AlivcLivePushConfig class to call the relevant method with the response data as its parameter to enable screen recording.

        2.  Call the StartCamera method and do not set the surfaceView parameter.

        3.  Call the startCameraMix method and specify the position of the caster's camera-shot content on the audience's screen.

-   Enable screen recording

    The Android stream ingest SDK uses MediaProjection for screen recording. Users need to request a screen recording permission. After receiving response data, you can use the AlivcLivePushConfig class to call the relevant method with the response data as its parameter to enable screen recording. By default, the camera is disabled during screen recording. The following example shows the sample code.

    ``` {#codeblock_v4v_bkg_fva}
    mAlivcLivePushConfig.setMediaProjectionPermissionResultData(resultData)
    ```

-   Configure camera preview

    After enabling screen recording, you can call relevant methods to enable and disable camera preview. The following example shows the sample code.

    ``` {#codeblock_4jb_9oe_ef9}
    mAlivcLivePusher.startCamera(surfaceView); // Enable camera preview.
    mAlivcLivePusher.stopCamera(); // Disable camera preview.
    ```

    **Note:** 

    -   We recommend that you use the surfaceView parameter to set the aspect ratio to 1:1 for camera preview in screen recording mode. In this way, you do not need to adjust the surfaceView parameter value for screen rotation.

    -   If you do not set the aspect ratio to 1:1, you have to adjust the surfaceView parameter value for screen rotation, call the stopCamera method to disable camera preview, and then call the startCamera method to enable camera preview again.

    -   If a caster does not need camera preview, set the surfaceView parameter to null.

-   Configure camera stream mixing

    During game live streaming, a caster can disable camera preview to remove the preview screen from the game screen. However, if the audience need to view the caster's camera-shot content, stream mixing can be enabled. The following example shows the sample code.

    ``` {#codeblock_56c_d4c_hh7}
    /**
    * @param x // The start position of the caster's camera-shot content on the x-axis of the audience's screen, in the range of 0f to 1.0f.
    * @param y // The start position of the caster's camera-shot content on the y-axis of the audience's screen, in the range of 0f to 1.0f.
    * @param w // The width of the caster's camera-shot content on the audience's screen, in the range of 0f to 1.0f.
    * @param h // The height of the caster's camera-shot content on the audience's screen, in the range of 0f to 1.0f.
    * @return
    */
    mAlivcLivePusher.startCameraMix(x, y, w, h); // Enable camera stream mixing.
    mAlivcLivePusher.stopCameraMix(); // Disable camera stream mixing.
    ```

-   Set the screen orientation

    In screen recording mode, you can enable the stream ingest SDK to sense the screen rotation between the portrait mode and landscape mode. The following example shows the sample code.

    ``` {#codeblock_je2_05j_ntc}
    mAlivcLivePusher.setScreenOrientation(0);
    ```

    **Note:** If the screen is rotated, the stream ingest SDK needs to receive a callback event notification through the OrientationEventListener interface at the application layer and use the obtained screen orientation as the parameter of this method.

-   Configure privacy protection

    You can configure privacy protection for casters. To enter a password or perform other private operations during screen recording, a caster can enable privacy protection. After performing relevant operations, the caster can also disable this feature. The following example shows the sample code.

    ``` {#codeblock_vkr_lj0_jai}
    mAlivcLivePusher.pauseScreenCapture(); // Enable privacy protection.
    mAlivcLivePusher.resumeScreenCapture(); // Disable privacy protection.
    ```

    **Note:** If you have used the AlivcLivePushConfig class to call the setPausePushImage method, the specified image appears on the audience's screen after screen recording is paused. If you have not called this method, the audience's screen is paused at the last frame after screen recording is paused.


## Handle exceptions and special scenarios {#section_wcv_gzx_pfb .section}

-   Handle callback event notifications received through the AlivcLivePushErrorListener interface

    -   If you receive an onSystemError event notification, a system error has occurred. You need to stop stream ingest.

    -   If you receive an onSDKError event notification, an SDK error has occurred. You need to destroy the current stream ingest and then restart stream ingest, or call the `restartPush or restartPushAsync` method to restart the `AlivcLivePusher` object.

    -   If you receive any callback event notifications containing the following error code, your application failed to obtain permission to access a microphone or camera: The `ALIVC_PUSHER_ERROR_SDK_CAPTURE_MIC_OPEN_FAILED` error code indicates that your application failed to obtain permission to access a microphone. The `ALIVC_PUSHER_ERROR_SDK_CAPTURE_CAMERA_OPEN_FAILED` error code indicates that your application failed to obtain permission to access a camera.

-   Handle callback event notifications received through the AlivcLivePushNetworkListener interface

    -   If you receive an `onNetworkPoor` event notification, poor network conditions cannot support smooth stream ingest. However, the stream ingest is still in progress and is not disabled. If you receive an `onNetworkRecovery` event notification, the network has recovered. You can add a solution according to your business logic. For example, you can display a message on the UI to remind users.

    -   If you receive an `onConnectFail`, `onReconnectError`, or `onSendDataTimeout` event notification, a network error has occurred. You need to destroy the current stream ingest and then restart stream ingest, or call the `reconnectAsync` method to reconnect to the network. We recommend that you test the network and ingest URL before you reconnect the stream ingest SDK to the network.

    -   If you receive an `onReconnectStart` event notification, the stream ingest SDK has automatically started to reconnect to the network or you have called the `reconnectAsync` method to reconnect to the network. Each time the stream ingest SDK reconnects to the network, it establishes an RTMP connection.

        **Note:** After the RTMP connection has been established, you can receive an `onReconnectSuccess` event notification. However, this does not mean that stream ingest can be successful. If stream ingest still fails due to network or other errors, the SDK can continue to try reconnecting to the network.

    -   If you receive an `onPushURLAuthenticationOverdue` event notification, your ingest URL is about to expire. If you have enabled stream ingest authentication to carry an auth\_key in an ingest URL, this ingest URL needs to be verified. You can receive this callback event notification about one minute before the ingest URL expires. After you receive it, you must return a new ingest URL. By doing so, you can ensure that stream ingest is not interrupted due to the expiration of an ingest URL. The following example shows the sample code.

        ``` {#codeblock_jo5_az3_gij}
        String onPushURLAuthenticationOverdue(AlivcLivePusher pusher) {
        return "New ingest URL rtmp://";
        }
        ```

-   Handle callback event notifications related to background music errors received through the **AlivcLivePusherBGMListener** interface
    -   If you receive an `onOpenFailed` event notification, background music failed to start. You need to check the music file and its path, and then call the `startBGMAsync` method to start playing the music again.

    -   If you receive an `onDownloadTimeout` event notification, background music timed out. This error usually occurs when the music file path is a URL. You need to remind the caster to check network conditions, and then call the `startBGMAsync` method to start playing the music again.

-   Handle network disconnection
    -   Short period of network disconnection or network switchover: Generally, if the network disconnection duration and the number of reconnection attempts are within the ranges as specified through the **AlivcLivePushConfig** class, the stream ingest SDK automatically reconnects to the network. After the reconnection is successful, the stream ingest SDK enables stream ingest. If you use Alibaba Cloud ApsaraVideo Player, we recommend that you reconnect the player to the network 5s after you receive a timeout notification.

    -   Long period of network disconnection: If the network disconnection duration and the number of reconnection attempts exceed the ranges as specified through the **AlivcLivePushConfig** class, the stream ingest SDK fails to automatically reconnect to the network. In this case, you receive an `onReconnectError` event notification. After the network is recovered, you can call the `reconnectAsync` method to reconnect to the network. You also need to reconnect Alibaba Cloud ApsaraVideo Player to the network.

        -   We recommend that you monitor the network outside the stream ingest SDK.

        -   A caster and the audience cannot directly communicate with each other on clients, but need to communicate through a server. For example, if the network of the caster's client is disconnected and stream ingest is interrupted, the server receives a callback event notification related to stream ingest interruption from CDN. The server then pushes this event notification to the audience's clients, which can take relevant action. If stream ingest is enabled, the server uses the same method to notify the audience's clients.

        -   To reconnect Alibaba Cloud ApsaraVideo Player to the network, you need to stop and then restart its playing. Call relevant methods in the following sequence: stop \> prepareAndPlay.

            ``` {#codeblock_6sa_zn8_g7o}
            mPlayer.stop();
            mPlayer.prepareAndPlay(mUrl);
            ```

            **Note:** For more information about the player, see [Basic player \(Live Q&A\)](https://help.aliyun.com/document_detail/61431.html?spm=a2c4g.11186623.2.35.6284161cvDZvBu).

-   Move to the background and lock the screen
    -   When your application is moved to the background or the screen is locked, you can use the AlivcLivePusher class to call the pause\(\) or resume\(\) method to disable or enable stream ingest.

    -   For audio and video calls in an application, the stream ingest SDK collects and ingests audio streams. When your application is moved to the background or the screen is locked, you can call the mAlivcLivePusher.setMute\(true/false\) method to specify whether to collect audio streams in the background as needed.

-   Set the bitrate

    The stream ingest SDK supports a dynamic bitrate. You can use the **AlivcLivePushConfig** class to modify default bitrate settings. Based on the video resolution and fluency requirements of different products, you can set a different value range for the bitrate according to the following rules:

    -   Video resolution: A higher stream ingest bitrate improves the resolution of video streams. Therefore, you can set a high bitrate to guarantee the resolution of video streams.

    -   Video fluency: A higher stream ingest bitrate occupies more network bandwidth. Therefore, if you set a high bitrate under poor network conditions, the fluency of video streams may be affected.


## Important notes {#section_ttp_fdl_nfb .section}

-   Obfuscation check: You need to keep relevant SDK package names to ensure that they are not obfuscated.

    ``` {#codeblock_at8_974_yry}
    -keep class com.alibaba.livecloud.** { *;}
    -keep class com.alivc. ** { *;}
    ```

-   Method calls
    -   You can call both synchronous and asynchronous methods. However, we recommend that you use asynchronous methods to minimize resources consumed on the main thread.

    -   APIs of the stream ingest SDK throw exceptions when an error occurs or you call methods in an incorrect sequence. You can add the try…catch syntax to handle exceptions and avoid an application crash.

    -   You need to pay attention to the sequence of method calls.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40382/156593462355892_en-US.png)

-   Package size
    -   The size of an SDK package is 11.7 MB for arm64-v8a and 9 MB for armeabi-v7a.

    -   After you integrate the stream ingest SDK, the size of the Android package \(APK\) increases by about 3.6 MB.

-   Constraints
    -   You can set the screen orientation only before stream ingest. You cannot change the screen orientation in real time during stream ingest.

    -   You must disable screen auto-rotation for stream ingest in landscape mode.

    -   In hardcoding mode, the output resolution must be multiples of 16 in consideration of the encoder compatibility. For example, if you set the resolution to 540p, the output resolution is 544 x 960. You need to scale the screen size of the player according to the output resolution to prevent black edges.

-   Version upgrades
    -   For more information about how to upgrade the stream ingest SDK from V1.3 to V3.0.0–3.3.3 and upgrade the joint stream SDK to stream ingest SDK V3.0.0–3.3.3, see [SDK upgrade documents](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/45265/cn_zh/1511187112732/updateDoc_android_20171120.zip?spm=a2c4g.11186623.2.37.6284161cvDZvBu&file=updateDoc_android_20171120.zip).

    -   Stream ingest SDK V3.3.4 and later versions are no longer compatible with stream ingest SDK V1.3. We recommend that you remove the earlier version and install the latest SDK version.

    -   To upgrade the stream ingest SDK to V3.1.0, you must integrate the Alibaba Cloud ApsaraVideo Player SDK, which is included in the stream ingest SDK package.

    -   Stream ingest SDK V3.2.0 and later versions provide two types of SDK packages. One includes the Alibaba Cloud ApsaraVideo Player SDK and the other does not. The Alibaba Cloud ApsaraVideo Player SDK is required only if you need to play background music.


