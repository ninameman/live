Integrate RTS SDKs for mobile clients 
==========================================================

This topic describes how to integrate Real-Time Streaming (RTS) SDKs for mobile clients with players. You can integrate RTS SDKs for mobile clients with the following types of players: ApsaraVideo Player, third-party players that depend on FFmpeg, and third-party players that do not depend on FFmpeg.

1. Integration methods 
-------------------------------------------



| Operating system |      Integration method       |                                                                                                                     Remarks                                                                                                                     |
|------------------|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Android          | maven                         | This method supports only ApsaraVideo Player.                                                                                                                                                                                                   |
| Android          | SO libraries and header files | If you use this method, you must develop artc Demuxer by yourself. If FFmpeg is used, you can develop artc Demuxer based on rtsdec.c.                                                                                                           |
| -                | rtsdec.c                      | The AVInputFormat plug-in for FFmpeg.                                                                                                                                                                                                           |
| IOS              | pod                           | This method supports both ApsaraVideo Player and third-party players. If you use a third-party player, you must develop artc Demuxer by yourself. If the third-party player depends on FFmpeg, you can develop your software based on rtsdec.c. |
| IOS              | Dynamic frameworks            | This method supports both ApsaraVideo Player and third-party players. If you use a third-party player, you must develop artc Demuxer by yourself. If the third-party player depends on FFmpeg, you can develop your software based on rtsdec.c. |



2. Overview 
--------------------------------

To use the RTS feature, you must have a player. Three types of players are supported, including ApsaraVideo Player, third-party players that depend on FFmpeg, and third-party players that do not depend on FFmpeg.

The operations that are required to integrate RTS SDK with the three types of players are different:

* ApsaraVideo Player:

  1. Integrate RTS SDK as a plug-in into ApsaraVideo Player SDK.

     
  
  2. Integrate ApsaraVideo Player SDK and RTS SDK in a project.

     
  
  3. Call the API of ApsaraVideo Player to use the RTS feature.

     
  

  

* Set a function pointer to AVInputFormat if streaming URLs start with artc://.

  1. Use FFmpeg to integrate RTS SDK as a plug-in into an FFmpeg-based third-party player.

     
  
  2. Integrate a player in a project.

     
  
  3. Call the player API to use the RTS feature.

     
  

  

* Third-party players that do not depend on FFmpeg:

  1. Integrate RTS SDK as a plug-in into a third-party player.

     
  
  2. Integrate a player in a project.

     
  
  3. Call the player API to use the RTS feature.

     
  

  



**Note**

Perform the integration operations based on the player that you use.

3. Sample code 
-----------------------------------

In the `ijkplayer-RTS` demo, a player is developed based on the open source player ijkplayer to support RTS. You can refer to this demo to extend self-developed players.


|   Demo name   |                                                             Download link                                                             |
|---------------|---------------------------------------------------------------------------------------------------------------------------------------|
| ijkplayer-RTS | [Download](https://alivc-demo-cms.alicdn.com/versionProduct/sourceCode/rts/ijkDemo/ijkplayer-RTS-v1.4.1-20.11.19.zip) |



4. Integration for Android 
-----------------------------------------------

4.1 Use RTS SDK with ApsaraVideo Player 
------------------------------------------------------------

If you use ApsaraVideo Player, the integration is simple. This is because the plug-in that is used to integrate RTS SDK into ApsaraVideo Player is built in ApsaraVideo Player SDK. You only need to configure dependencies so that you can use the Advanced Real-Time Communication (ARTC) protocol in the same way as Real-Time Messaging Protocol (RTMP).

**Step 1: Integrate RTS SDK as a plug-in into ApsaraVideo Player SDK** 

Add the `ArtcDemuxer.aar` dependency of ApsaraVideo Player SDK and `RtsSDK.aar` to your application project. Both Maven and local dependencies are supported. After you add `ArtcDemuxer.aar` to your project, ApsaraVideo Player SDK automatically loads RTS SDK as a plug-in.

* Maven dependencies

  

  |    Name    | Version |                                       Code                                        |
  |------------|---------|-----------------------------------------------------------------------------------|
  | AliyunARTC | 5.2.0   | implementation 'com.aliyun.sdk.android:AliyunArtc:5.2.0'  |
  | RTSSDK     | 1.3.0   | implementation 'com.aliyun.rts.android:RtsSDK:+'          |

  

* Local dependencies

  To use local dependencies, obtain them from the SDK download page.
  






**Step 2: Integrate ApsaraVideo Player SDK and RTS SDK in a project** 

If you have integrated ApsaraVideo SDK, you only need to update the version of ApsaraVideo SDK. You can integrate ApsaraVideo Player SDK by using Maven or local dependencies.

* Maven dependencies

  

  |            Name             | Version |                                           Code                                           |
  |-----------------------------|---------|------------------------------------------------------------------------------------------|
  | AliyunPlayer:Version number | 5.2.0   | implementation 'com.aliyun.sdk.android:AliyunPlayer:5.2.0-full'  |
  | AlivcConan                  | 1.3.0   | implementation 'com.alivc.conan:AlivcConan:1.0.4'                |

  

* Local dependencies

  To use local dependencies, obtain them from the ZIP package that ApsaraVideo provides in the [Player SDK for Android](https://help.aliyun.com/document_detail/94328.html?spm=a2c4g.11186623.6.1034.f9cc11f9sA21xA) topic. For more information about the integration of ApsaraVideo Player SDK, see [Integration](/intl.en-US/New Player SDK/ApsaraVideo Player SDK for Android/Integration.md).
  




Procedure:

1. Determine the dependency method before you start the integration.

   

2. Create a project.![Create a project 2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9282086061/p169000.png)

   

3. View the project structure after you create the project.![Project structure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9282086061/p169003.png)

   

4. Add the following code to `build.gradle` in the root directory, as shown in the following figure.![gradle](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169004.png)

       // The URL of the Maven repository for MPChart. If you do not need MPChart, you can delete this line of code.
       maven { url 'https://jitpack.io' }
       // The URL of the Maven repository for Alibaba Cloud SDK. If you use ijkplayer, you can delete this line of code.
       maven { url "http://maven.aliyun.com/nexus/content/repositories/releases" }
       // The URL of the Maven repository for RTS SDK. If you use ijkplayer, you can delete this line of code. This is because the demo of RTS SDK includes the dynamic framework of ijkplayer.
       maven { url 'http://mvnrepo.alibaba-inc.com/nexus/content/groups/public' }

   

   

       ext {
           compileSdkVersion = 25
           buildToolsVersion = "25.0.3"
           minSdkVersion = 21
           targetSdkVersion = 25
       
           versionCode = 800800
           versionName = "0.8.8"
           appVersionCode = 1
           appVersionName = "1.0"
       
           externalRecyclerView = 'com.android.support:recyclerview-v7:25.4.0'
           externalMPAndroidChart = 'com.github.PhilJay:MPAndroidChart:v3.1.0'
           externalSupportAppCompat = 'com.android.support:appcompat-v7:25.4.0'
       
           // The player for ARTC-based live streaming.
           externalAlivcConan = 'com.alivc.conan:AlivcConan:1.0.4'
           externalAliyunARTCNet = 'com.aliyun.rts.android:RtsSDK:+'
           externalAliyunARTC = 'com.aliyun.sdk.android:AliyunArtc:5.2.0'
           externalAliyunPlayer = 'com.aliyun.sdk.android:AliyunPlayer:5.2.0-full'
       
           //required, enough for most devices.
       //    implementation 'tv.danmaku.ijk.media:ijkplayer-java:0.8.8'
       //    implementation 'tv.danmaku.ijk.media:ijkplayer-armv7a:0.8.8'
       }

   

   




**Step 3: Call the API of ApsaraVideo Player to use the RTS feature** 

After you complete the preceding configuration, ApsaraVideo Player SDK supports live streams of which the URLs start with `artc://`.

1. Create a player.

   Use the AliPlayerFactory class to create a player. You can create two types of players, which are AliPlayer and AliListPlayer. If you want to play only one stream, use AliPlayer.

   You can call the following method to create AliPlayer:

       AliPlayer aliyunVodPlayer;
       .....
       aliyunVodPlayer = AliPlayerFactory.createAliPlayer(getApplicationContext());

   

2. Set player listeners.

   ApsaraVideo Player provides a variety of listeners, such as onPrepared and onCompletion.

   You can call the following methods to set listeners:

       aliyunVodPlayer.setOnCompletionListener(new IPlayer.OnCompletionListener() {
           @Override
           public void onCompletion() {
               // The completion of playback.
           }
       });
       aliyunVodPlayer.setOnErrorListener(new IPlayer.OnErrorListener() {
           @Override
           public void onError(ErrorInfo errorInfo) {
               // The occurrence of errors.
           }
       });
       aliyunVodPlayer.setOnPreparedListener(new IPlayer.OnPreparedListener() {
           @Override
           public void onPrepared() {
               // Successful preparation.
           }
       });
       aliyunVodPlayer.setOnVideoSizeChangedListener(new IPlayer.OnVideoSizeChangedListener() {
           @Override
           public void onVideoSizeChanged(int width, int height) {
               // The change of the video resolution.
           }
       });
       aliyunVodPlayer.setOnRenderingStartListener(new IPlayer.OnRenderingStartListener() {
           @Override
           public void onRenderingStart() {
               // The appearance of the first frame.
           }
       });
       aliyunVodPlayer.setOnInfoListener(new IPlayer.OnInfoListener() {
           @Override
           public void onInfo(int type, long extra) {
               // Other events and information, such as the start of loop playback, buffer position, current playback position, and the start of autoplay.
           }
       });
       aliyunVodPlayer.setOnLoadingStatusListener(new IPlayer.OnLoadingStatusListener() {
           @Override
           public void onLoadingBegin() {
               // The start of buffering.
           }
           @Override
           public void onLoadingProgress(int percent, float kbps) {
               // The buffering progress.
           }
           @Override
           public void onLoadingEnd() {
               // The completion of buffering.
           }
       });
       aliyunVodPlayer.setOnSeekCompleteListener(new IPlayer.OnSeekCompleteListener() {
           @Override
           public void onSeekComplete() {
               // The completion of seeking.
           }
       });
       aliyunVodPlayer.setOnSubtitleDisplayListener(new IPlayer.OnSubtitleDisplayListener() {
           @Override
           public void onSubtitleShow(long id, String data) {
               // The display of subtitles.
           }
           @Override
           public void onSubtitleHide(long id) {
               // The hiding of subtitles.
           }
       });
       aliyunVodPlayer.setOnTrackChangedListener(new IPlayer.OnTrackChangedListener() {
           @Override
           public void onChangedSuccess(TrackInfo trackInfo) {
               // The success of switching between audio and video streams or between resolutions.
           }
           @Override
           public void onChangedFail(TrackInfo trackInfo, ErrorInfo errorInfo) {
               // The failure of switching between audio and video streams or between resolutions.
           }
       });
       aliyunVodPlayer.setOnStateChangedListener(new IPlayer.OnStateChangedListener() {
           @Override
           public void onStateChanged(int newState) {
               // The change of the player status.
           }
       });
       aliyunVodPlayer.setOnSnapShotListener(new IPlayer.OnSnapShotListener() {
           @Override
           public void onSnapShot(Bitmap bm, int with, int height) {
               // The capture of snapshots.
           }
       });

   

3. Set the playback source and prepare for playback.

   ApsaraVideo Player supports four types of playback sources, which are VidSts, VidAuth, VidMps, and UrlSource. UrlSource is used for URL-based playback. If you use UrlSource, you can set URLs to start with `artc://` to use the RTS feature.

       UrlSource urlSource = new UrlSource();
       urlSource.setUri("artc://xxxx");
       aliyunVodPlayer.setDataSource(urlSource);

   

4. Set the UI view.

   If the playback source contains video images, set the UI view to display the video images. SurfaceView and TextureView are supported.

   In the following code, SurfaceView is used as an example:

       surfaceView = (SurfaceView) findViewById(R.id.playview);
       surfaceView.getHolder().addCallback(new SurfaceHolder.Callback() {
           @Override
           public void surfaceCreated(SurfaceHolder holder) {
               aliyunVodPlayer.setDisplay(holder);
           }
           @Override
           public void surfaceChanged(SurfaceHolder holder, int format, int width, int height) {
               aliyunVodPlayer.redraw();
           }
           @Override
           public void surfaceDestroyed(SurfaceHolder holder) {
               aliyunVodPlayer.setDisplay(null);
           }
       });

   

5. Set playback control.

   You can create playback control buttons and associate click events with playback control methods to implement playback control. The basic control features include play, stop, pause, and seek. The seek feature is valid only for ApsaraVideo VOD. If you pause a live stream, the live stream stops at the current position. After you resume the playback of the live stream, the live stream starts from the current position.

   Sample code:

       // Start the playback.
       aliyunVodPlayer.start();
       // Pause the playback.
       aliyunVodPlayer.pause();
       // Stop the playback.
       aliyunVodPlayer.stop();
       // Seek. This operation may not direct the video to the precise time point.
       aliyunVodPlayer.seekTo(long position);
       // Reset the player.
       aliyunVodPlayer.reset();
       // Release the player. The player cannot be used after it is released.
       aliyunVodPlayer.release();

   

   For more information about the features of ApsaraVideo Player SDK, see [API](/intl.en-US/New Player SDK/ApsaraVideo Player SDK for Android/API.md) and [Features and usage](/intl.en-US/New Player SDK/ApsaraVideo Player SDK for Android/Features and usage.md).
   

6. Set parameters.

   We recommend that you set the following parameters to take full advantage of RTS:

       // Query the configuration.
       PlayerConfig config = mAliyunVodPlayer.getConfig();
       // Set the maximum latency to 1 second. The ARTC protocol controls the latency.
       config.mMaxDelayTime = 1000;
       // Set the buffer period to 10 ms. The ARTC protocol controls the buffer period.
       config.mHighBufferDuration = 10;
       config.mStartBufferDuration = 10;
       .... // Other settings.
       // Specify the settings for the player.
       mAliyunVodPlayer.setConfig(config);

   

7. loadlibrary

   Add `System.loadLibrary("RtsSDK")` to the required activity.

       static {
           System.loadLibrary("RtsSDK");
       }

   




4.2 Use RTS SDK with a third-party player ijkplayer that depends on FFmpeg 
-----------------------------------------------------------------------------------------------

If you use a third-party player, you must integrate RTS SDK as a plug-in into the player to support the ARTC protocol. This incurs extra development work. RTS provides the source code file rtsdec.c for you to integrate RTS SDK as the demuxer plug-in into a player that depends on FFmpeg, which is a common player engine. This helps you reduce the development costs. The following section describes the integration procedure.

**Step 1: Integrate RTS SDK as a plug-in into ijkplayer** 

You can use one of the following integration methods.


|            Integration method             |                                            Benefit                                             |               Shortcoming               |
|-------------------------------------------|------------------------------------------------------------------------------------------------|-----------------------------------------|
| Extend FFmpeg by adding a demuxer plug-in | This method is easy to use and frees you from developing extra logic code for ARTC-based URLs. | You must compile FFmpeg.                |
| Extend ijkplayer by adding AVInputFormat  | This method frees you from compiling FFmpeg.                                                   | You must add logic code to ff_player.c. |


**Notice**

1. RTS SDK for Android provides dynamic frameworks only for ARM64 and ARMv7-A.

   

2. Read [ijkplayer](https://github.com/Bilibili/ijkplayer) at GitHub and compile ijkplayer first.

   

3. The following procedure is based on ijkplayer tag k:0.8.8.

   




**Extend FFmpeg:** 

1. Modify `pull_fork` in the `ijkplayer/init-android.sh` script to delete architectures except for ARMv7-A and ARM64. Then, run the modified script.

   **Note**

   This is because RTS provides dynamic frameworks only for ARMv7-A and ARM64.

   ![ijk-Figure 1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169013.png)
   

2. Modify `FF_ACT_ARCHS_64` in the `ijkplayer/Android/contrib/compile-ffmpeg.sh` script to delete architectures except for ARMv7-A and ARM64.![c2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169014.png)

   

3. Copy `rtsdec.c` that RTS provides to the `ijkplayer/android/contrib/ffmpeg-arm64/libavformat` and `ijkplayer/android/contrib/ffmpeg-armv7a/libavformat` directories.

   

4. Modify the Makefile files to compile rtsdec.c.

   Modify the Makefile files in the `ijkplayer/android/contrib/ffmpeg-arm64/libavformat/` and `ijkplayer/android/contrib/ffmpeg-arm64/libavformat/` directories, as shown in the following figure.![1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p183914.png)
   

5. Modify the allformat.c files to support the ARTC protocol.

   Modify the allformats.c files in the `ijkplayer/android/contrib/ffmpeg-arm64/libavformat/` and `ijkplayer/android/contrib/ffmpeg-arm64/libavformat/` directories, as shown in the following figure.![c6](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169016.png)

           extern AVInputFormat ff_rtc_demuxer;
           av_register_input_format(&ff_rtc_demuxer);

   

6. Modify the compilation script of FFmpeg to support pulse-code modulation (PCM) decoding. This is because RTS SDK exports PCM data. Add the following code to the module-lite.sh script in the /config directory:

       # aliyun rts
       export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16be_planar"
       export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16le"
       export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16le_planar"

   

7. Compile FFmpeg.

   Add the ANDROID_NDK environment variable. In this example, ANDROID_NDK is set to android-ndk-r12b. Run the `./compile-ffmpeg.sh all` command in the `ijkplayer/android/contrib/` directory.
   

8. Check the result of FFmpeg compilation.

   Check whether an output file of FFmpeg compilation exists in the `ijkplayer/android/contrib/build` directory.
   

9. 

   Modify ACT_ABI_64 in the `ijkplayer/Android/compile-ijk.sh` script to delete architectures except for ARMv7-A and ARM64, as shown in the following figure.![c7](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169017.png)
   

10. Add the dynamic frameworks of RTS.

    Add the dynamic frameworks of RTS to `ijkplayer/android/contrib/build/ffmpeg-arm64/output` and ijkplayer/android/contrib/build/ffmpeg-armv7a/output based on the architecture. Then, copy the `rts_api.h` and `rts_messages.h` header files to `ijkplayer/android/contrib/build/ffmpeg-arm64/output/include` and `ijkplayer/android/contrib/build/ffmpeg-armv7a/output/include`.
    

11. Import the dynamic frameworks of RTS.

    Modify `ijkplayer/android/ijkplayer/ijkplayer-armv7a/src/main/jni/ffmpeg/Android.mk` and `ijkplayer/android/ijkplayer/ijkplayer-arm64/src/main/jni/ffmpeg/Android.mk`, as shown in the following figure.![c8](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169018.png)

        include $(CLEAR_VARS)
        LOCAL_MODULE := rtssdk
        LOCAL_SRC_FILES := $(MY_APP_FFMPEG_OUTPUT_PATH)/libRtsSDK.so
        include $(PREBUILT_SHARED_LIBRARY)

    

12. Add the dynamic frameworks of RTS as dependencies to ijkplayer.

    Modify `ijkplayer/ijkmedia/ijkplayer/Android.mk`, as shown in the following figure.![c9](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169019.png)
    

13. Add the logic code of RTS to ff_fflay.c.

    Set a function pointer to AVInputFormat if streaming URLs start with artc://. Modify `ijkplayer/ijkmedia/ijkplayer/ff_ffplay.c`, as shown in the following figure.![c10](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169021.png)

    

            extern AVInputFormat ff_rtc_demuxer;
            extern int artc_reload(AVFormatContext *ctx);
            extern void av_set_rts_demuxer_funcs(const struct rts_glue_funcs *funcs);
            extern void artc_set_rts_param(char* key, char* value);
            extern long long artc_get_state(AVFormatContext *ctx, int key);
        
            int version = 2;
            const struct rts_glue_funcs* rts_funcs = get_rts_funcs(version);
            // set to ffmpeg plugin
            av_set_rts_demuxer_funcs(rts_funcs);
            artc_set_rts_param((char*)"AutoReconnect", (char*)"false");

    

14. Compile ijkplayer.

    Run the `./compile-ijk.sh all` command in the `ijkplayer/android` directory.

    




**Extend ijkplayer based on the sample code:** 

1. Compile FFmpeg.

   Modify the compilation script of FFmpeg to support PCM decoding. This is because RTS SDK exports PCM data. Add the following code to the module-lite.sh script in the /config directory:

       # aliyun rts
       export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16be_planar"
       export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16le"
       export COMMON_FF_CFG_FLAGS="$COMMON_FF_CFG_FLAGS --enable-decoder=pcm_s16le_planar"

   

   Then, compile FFmpeg. In this case, you do not need to add RTS SDK dependencies. For more information, see the procedure that is used to compile ijkplayer.
   

2. Add RTS dependencies to ijkplayer.

   Add the dynamic frameworks of RTS SDK to the project and modify the Android.mk files. You can refer to related operations in the method of expending FFmpeg.
   

3. Add the logic code of RTS to ff_fflay.c.

   Call the AVInputFormat function if streaming URLs start with artc://, as shown in the following figure.![c11](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169053.png)

       if(strncmp(is->filename, "artc://", 7) == 0) {
               extern AVInputFormat ff_rtc_demuxer;
               extern int artc_reload(AVFormatContext *ctx);
               extern void av_set_rts_demuxer_funcs(const struct rts_glue_funcs *funcs);
               extern void artc_set_rts_param(char* key, char* value);
               extern long long artc_get_state(AVFormatContext *ctx, int key);
       
               int version = 2;
               const struct rts_glue_funcs* rts_funcs = get_rts_funcs(version);
               // set to ffmpeg plugin
               av_set_rts_demuxer_funcs(rts_funcs);
               artc_set_rts_param((char*)"AutoReconnect", (char*)"false");
               is->iformat = &ff_rtc_demuxer;
           }
           else {
               if(ffp->iformat_name)
                   is->iformat = av_find_input_format(ffp->iformat_name);
           }

   

4. Copy rtsdec.c to the `ijkplayer/ijkmedia/ijkplayer` directory. Modify the android.mk file in the directory to add the rtsdec.c file.

       LOCAL_SRC_FILES += rtsdec.c

   




After you complete the preceding procedure, RTS SDK is added as a plug-in to the player. Then, integrate the player.



**Step 2: Integrate ijkplayer in a project** 

Import modules.

You must import the following modules: ijkplayer-arm64, ijkplayer-armv7a, and ijkplayer-java.

The following figure shows how to create a project.![j1](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/0382086061/p169060.png)

**Step 3: Call the API of ijkplayer** 

1. Create ijkplayer.

       mIjkPlayer = new IjkMediaPlayer();

   

2. Set callbacks.

       mIjkPlayer.setOnPreparedListener(new IMediaPlayer.OnPreparedListener() {
           @Override
           public void onPrepared(IMediaPlayer iMediaPlayer) {
               
           }
       });
       
       mIjkPlayer.setOnInfoListener(new IMediaPlayer.OnInfoListener() {
           @Override
           public boolean onInfo(IMediaPlayer iMediaPlayer, int arg1, int arg2) {
               
       });
       
       mIjkPlayer.setOnVideoSizeChangedListener(new IMediaPlayer.OnVideoSizeChangedListener() {
           @Override
           public void onVideoSizeChanged(IMediaPlayer iMediaPlayer, int width, int height, int sarNum, int sarDen) {
              
           }
       });
       
       mIjkPlayer.setOnErrorListener(new IMediaPlayer.OnErrorListener() {
           @Override
           public boolean onError(IMediaPlayer iMediaPlayer, int framework_err, int impl_err) {
               
               return false;
           }
       });

   

3. Set the UI view.

       mIjkPlayer.setSurface(surface);

   

4. Set the playback source.

       mIjkPlayer.setDataSource("artc://xxx");

   

5. Set playback control.

       public void prepare() {
           if(mIjkPlayer ! = null){
               mIjkPlayer.prepareAsync();
           }
       }
       
       @Override
       public void start() {
           if(mIjkPlayer ! = null){
               mIjkPlayer.start();
           }
       }
       
       public void pause() {
           if(mIjkPlayer ! = null){
               mIjkPlayer.pause();
           }
       }
       
       public void stop() {
           if(mIjkPlayer ! = null){
               mIjkPlayer.stop();
           }
       }
       public void release() {
           if(mIjkPlayer ! = null){
               mIjkPlayer.release();
           }
       }

   




4.3 Use RTS SDK with a third-party player that does not depend on FFmpeg 
---------------------------------------------------------------------------------------------

This method applies to users who use a self-developed player. You can refer to the manual of RTS SDK to add dynamic frameworks and header files to your project. You can also refer to rtsdec.c to develop the demuxer plug-in.

5. Integration for iOS 
-------------------------------------------

5.1 Use RTS SDK with ApsaraVideo Player 
------------------------------------------------------------

**Step 1: Integrate RTS SDK as a plug-in into ApsaraVideo Player SDK** 

In addition to ApsaraVideo Player SDK, your application must also depend on RTS SDK and AliPlayerSDK_iOS_ARTC. ApsaraVideo Player SDK automatically loads RTS SDK as a plug-in.

* Pod dependencies of the latest versions

  

  |         Name          | Version |                         Code                         |
  |-----------------------|---------|------------------------------------------------------|
  | AliPlayerSDK_iOS_ARTC | 5.2.1   | pod 'AliPlayerSDK_iOS_ARTC'  |
  | RtsSDK                | 1.3.0   | pod 'RtsSDK'                 |

  




<!-- -->

* Local dependencies

  To use local dependencies, obtain the required frameworks from the SDK download page.
  






**Step 2: Integrate ApsaraVideo Player SDK and RTS SDK in a project** 

* Pod dependency (ApsaraVideo Player SDK of the latest version)

  

  |       Name       | Version |                      Code                       |
  |------------------|---------|-------------------------------------------------|
  | AliPlayerSDK_iOS | 5.2.1   | pod 'AliPlayerSDK_iOS'  |

  

* Local dependencies

  To use local dependencies, obtain them from the ZIP package that ApsaraVideo provides in the [Player SDK for Android](https://help.aliyun.com/document_detail/94328.html?spm=a2c4g.11186623.6.1034.f9cc11f9sA21xA) topic. For more information about the integration of ApsaraVideo Player SDK, see [Integration](/intl.en-US/New Player SDK/ApsaraVideo Player SDK for Android/Integration.md).
  




Determine the dependency method before you start the integration.

* If you use the **pod** mode, open a command line interface (CLI) on a terminal. Go to the root directory of your project and run the `pod init` command. In the Podfile that is generated, enter the following code. If you need to use a specific version, specify the version in the code. Run the `pod install` command. If you have not installed CocoaPods, install it first.

       pod 'RtsSDK'
       pod 'AliPlayerSDK_iOS'
       pod 'AliPlayerSDK_iOS_ARTC'
       ```

  

  

* If you use **local dependencies** , drag the library files in the following figure to your project. Then, select Embed \& Sign for frameworks on the **General** tab of your project.

  ![j2](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1382086061/p169248.png)![j3](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1382086061/p169250.png)
  






**Step 3: Call the API of ApsaraVideo Player** 

1. Initialize AliPlayer.

       - (AliPlayer *)aliPlayer{
           if (! _aliPlayer) {
               _aliPlayer = [[AliPlayer alloc] init];
               _aliPlayer.scalingMode =  AVP_SCALINGMODE_SCALEASPECTFIT;
               _aliPlayer.rate = 1;
           // To use AVPDelegate, add the following line of code.
               _aliPlayer.delegate = self;
           // Set the UI view and apply the UI view to AliPlayer.
               _aliPlayer.playerView = self.basePlayerView.playerView;
               _aliPlayer.autoPlay = YES;
           }
           return _aliPlayer;
       }

   

2. Set playback URLs.

       AVPUrlSource *source = [[AVPUrlSource alloc] urlWithString:_url];
       [self.aliPlayer setUrlSource:source];

   

3. Set player parameters.
   If you use ApsaraVideo Player to play ARTC-based live streams, we recommend that you use the following settings:
   

   **Notice**

   Set player parameters before you call the prepare method. Otherwise, the player parameters do not take effect.

       AVPConfig *config = self.aliPlayer.getConfig;
       // The maximum latency of live streaming.
       [config setMaxDelayTime:1000];
       // The buffer period.
       [config setHighBufferDuration:10];
       // The maximum startup loading duration.
       [config setStartBufferDuration:10];
       // The retry times.
       [config setNetworkRetryCount:2];
       // The retry interval.  
       [config setNetworkTimeout:15000];
        [_aliPlayer setConfig:config];
       // By default, hard decoding is enabled. If hard decoding failed during the preparation of the player, hard decoding is switched to soft decoding.
        _aliPlayer.enableHardwareDecoder = YES;

   

4. Enable logging.

       [AliPlayer setEnableLog:YES];
       [AliPlayer setLogCallbackInfo:LOG_LEVEL_DEBUG callbackBlock:nil];

   

5. Set playback control.

       [self.aliPlayer prepare];
       [self.aliPlayer stop];
       [self.aliPlayer destroy];
       [self.aliPlayer reload];

   




5.2 Use RTS SDK with a third-party player ijkplayer that depends on FFmpeg 
-----------------------------------------------------------------------------------------------

If you use a third-party player, you must integrate RTS SDK as a plug-in into the player to support the ARTC protocol. This incurs extra development work. RTS provides the source code file rtsdec.c for you to integrate RTS SDK as the demuxer plug-in into a player that depends on FFmpeg, which is a common player engine. This helps you reduce the development costs. The following section describes the integration procedure.

**Step 1: Integrate RTS SDK as a plug-in into ijkplayer** 

You can use one of the following integration methods.


|              Integration method               |                                            Benefit                                             |               Shortcoming               |
|-----------------------------------------------|------------------------------------------------------------------------------------------------|-----------------------------------------|
| **Extend FFmpeg** by adding a demuxer plug-in | This method is easy to use and frees you from developing extra logic code for ARTC-based URLs. | You must compile FFmpeg.                |
| **Extend ijkplayer** by adding AVInputFormat  | This method frees you from compiling FFmpeg.                                                   | You must add logic code to ff_player.c. |


**Notice**

1. Read [ijkplayer](https://github.com/Bilibili/ijkplayer) at GitHub and compile ijkplayer first.

   

2. The following procedure is based on ijkplayer tag k:0.8.8.

   




**Extend FFmpeg:** 

1. Run the `init-ios.sh` command in the `ijkplayer` directory.

   

2. Go to the `ijkplayer/ios` directory. Copy `rtsdec.c` to the `ffmpeg-$arch/libavformat` directory. Then, modify `libavformat/Makefile` and `allformat.c`. For more information, see method 1 in the "Integration for Android" section.

   

3. Compile FFmpeg.

   Run the `./compile-ffmpeg.sh all` command in the `ijkplayer/ios` directory.
   

4. Check the result of FFmpeg compilation.

   Check whether an output file of FFmpeg compilation exists in the `ijkplayer/ios/build/universal/` directory.
   

5. Add `RtsSDK.framework` to the `ijkplayer//ios/IJKMediaDemo/IJKMediaDemo` directory.

   

6. Open `ios/IJKMediaDemo/IJKMediaDemo.xcodeproj` in Xcode.

   

7. Add `RtsSDK.framework` as a dependency to `IJKMediaPlayer.xcodeproj`.![j4](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1382086061/p169264.png)

   

8. Add the logic code of RTS to `ff_fflay.c`. For more information, see the method of extending FFmpeg in the "Integration for Android" section.

   




**Extend ijkplayer:** 

1. Compile FFmpeg.

   Compile FFmpeg based on the official guide that ijkplayer provides. In this case, you do not need to use RTS SDK to extend FFmpeg.
   

2. Add RTS dependencies to ijkplayer.

   For more information, see the method of extending FFmpeg in the "Integration for iOS" section.
   

3. Drag rtsdec.c to your project.![j5](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1382086061/p169270.png)

   

4. Modify the code in `ff_ffplay.c`. For more information, see the method of extending ijkplayer in the "Integration for Android" section.

   






**Step 2: Integrate ijkplayer and RTS SDK in a project** 

Drag the frameworks of ijkplayer and the frameworks of RTS SDK to your project.

![j6](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4600746061/p169273.png)



**Step 3. Call the API of ijkplayer** 

1. Create ijkplayer.

       _ijkPlayer = [[IJKFFMoviePlayerController alloc] initWithContentURL:[NSURL URLWithString:_url] withOptions:options];
       _ijkPlayer.view.autoresizingMask = UIViewAutoresizingFlexibleWidth|UIViewAutoresizingFlexibleHeight;
       _ijkPlayer.view.frame = self.basePlayerView.playerView.bounds;
       _ijkPlayer.scalingMode = IJKMPMovieScalingModeAspectFit; // Set the scaling mode.
       _ijkPlayer.shouldAutoplay = YES; // Enable autoplay.

   

2. Set playback control.

       - (void)prepareToPlay;
       - (void)play;
       - (void)pause;
       - (void)stop;

   




5.3 Use RTS SDK with a third-party player that does not depend on FFmpeg 
---------------------------------------------------------------------------------------------

This method applies to users who use a self-developed player. You can refer to the manual of RTS SDK to add dynamic frameworks and header files to your project. You can also refer to rtsdec.c to develop the demuxer plug-in.

6. FAQ 
---------------------------

* Q: Why does a timeout error occur when the player plays a stream of which the URL starts with `artc://`?

  A: A common cause is that the RTS feature is disabled. To troubleshoot this issue, use an HTML5 player to check the stream.
  

* Q: I have integrated ApsaraVideo Player SDK by following the preceding operations. Why do I receive an error message indicating that ARTC is not supported when I use the integrated ApsaraVideo Player?

  A: A common cause is that your project does not contain AlivcArtc.aar or RtsSDK.aar.
  

* Q: Why does freezing occur during the playback of a stream?

  1. Check whether the Audio-Video Interleaved (AVI) format of the stream is valid. To troubleshoot this issue, use command lines to save the RTMP-based stream in FFmpeg. Then, use ffprobe to check packet interleaving.

     
  
  2. Check whether the network works well. To troubleshoot this issue, use RTMP to play the stream.

     
  
  3. Check whether the player SDK parameters are correct. To troubleshoot this issue, check the parameters based on the documentation of ApsaraVideo Player.

     
  

  

* Q: Why does the player mute the audio when I use a third-party player to pull a stream?

  A: Check whether FFmpeg supports PCM decoding. To troubleshoot this issue, check whether the audio decoder is created.
  




