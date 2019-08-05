# Detailed implementation procedure {#concept_66083_zh .concept}

This topic guides beginners through the procedure for creating a live Q&A service. You can learn how to use ApsaraVideo Live to ingest streams and deliver questions and how the application and application server interact with each other to complete live Q&A.

![](images/34364_en-US.png)

## Step 1: Prepare for live Q&A. {#section_dtx_hvb_dfb .section}

1.  Activate [ApsaraVideo Live](https://www.alibabacloud.com/zh/product/apsaravideo-for-live?spm=a2796.7919406.1097650.dznavproductsj1.1aff2d23uJYsMi) of Alibaba Cloud.
2.  Log on to the ApsaraVideo Live console and choose **Domain Management** \> **Management** to obtain the ingest URL and stream pulling URL. For more information, see [Stream ingest](../../../../intl.en-US/User Guide (New console)/Ingest and view streams/Configure edge ingestion.md#).

    ![](images/34371_en-US.png)

3.  Submit a ticket to apply for enabling the feature of inserting SEI signals into ingest streams. Enter your live domain names and application name in the ticket.

    **Note:** The authentication feature is enabled by default. To prevent the risk of hotlinking, you must use a signed URL to ingest streams. For more information, see [Stream authentication](../../../../intl.en-US/User Guide (New console)/Domain names/Access control/URL authentication.md#).


## Step 2: Start stream ingest. {#section_t25_2wb_dfb .section}

**Note:** 

-   If you want to insert SEI signals into live streams on ApsaraVideo Live, you must add `wm=1` to the ingest URL.
-   After the stream ingest starts, an ingest URL that contains the \_sei-copy string appears on the stream management page in addition to the target ingest URL. You can directly ignore the ingest URL. You only need to obtain the stream pulling URL based on your specified ingest URL.

## Step 3: Integrate and use ApsaraVideo Player SDK. {#section_xff_4wb_dfb .section}

ApsaraVideo Player SDK can parse SEI signals. You can directly integrate and use ApsaraVideo Player SDK. For more information about the download link, see SDK download.

-   **Android**
    -   Supported operating system versions

        ApsaraVideo Player SDK supports Android 4.0 or later. The mobile phone chip must use the ARMv7 or ARM64 architecture.

    -   Runtime environment

        We recommend that you use Android Studio as the development tool. This topic is written based on the Android Studio development environment.

    -   How to import ApsaraVideo Player SDK
        1.  Add the .aar files shown in the following figure to the libs folder.

            ![](images/34372_en-US.png)

        2.  Add a reference to the .aar files in the Gradle of the application.

            ![](images/34373_en-US.png)

    -   How to use the player

        Add the following methods to the activity that needs to use ApsaraVideo Player SDK:

        ```language-text
        // Initialize the player. (You only need to call this method once. We recommend that you initialize the player in the application.)
        AliVcMediaPlayer.init(getApplicationContext());
        
        // Create a player instance.
        mPlayer = new AliVcMediaPlayer(this, mSurfaceView);
        mPlayer.setSEIDataListener(new MediaPlayer.MediaPlayerSEIDataListener() {
        @Override
        public void onSEI_userUnregisteredData(String data) {
        // Parse the received user data in the live stream. For more information, see Step 5: The player parses the SEI.
               parserData(data);
        }
        });
        mPlayer.setMaxBufferDuration(3 * 1000);
        mPlayer.prepareAndPlay(liveUrl);// Prepare and play the live stream.
        
        ```

        For more information about how to use the Android player, see [ApsaraVideo Player Basic](). For more information about the features and APIs of the Android player, see [API Reference]().

-   
-   **iOS**
    -   Supported operating system versions

        ApsaraVideo Player SDK supports iOS 8.0 or later.

    -   Runtime environment

        We recommend that you use Xcode 8.0 or later for code compiling.

    -   How to import ApsaraVideo Player SDK

        ApsaraVideo Player SDK supports both normal import and CocoaPods-based import methods. You can choose one method as needed.

        1.  Normal import

            ```language-text
            Import AliyunPlayerSDK.framework and AliyunLanguageSource.bundle to the project.
            
            ```

            Open the project, select the target, and choose **General** \> **Embedded Binaries**. Click the plus sign \(**+**\), and then select **Add Other...**. For ApsaraVideo Player Basic, you only need to import the downloaded AliyunPlayerSDK.framework to the project and select the copy option.

            ![](images/34374_en-US.png)

            Import the header file.

            ![](images/34375_en-US.png)

            Choose **Build Settings** \> **Build Options** and set **Enable Bitcode** to **No**.

            ![](images/34376_en-US.png)

        2.  CocoaPods-based import

            Add the following statement to your Podfile:

            ```language-text
            pod 'AliyunPlayer_iOS/AliyunPlayerSDK'
            
            ```

            ![](images/34377_en-US.png)

            Run the pod install or pod update command to integrate the SDK into the project.

            ```language-text
            Run the pod install command each time you add, delete, or update your Podfile.
            
            ```

            Run the `project name.xcworkspace` file to open the project.

    -   How to use the player

        ```language-text
        -(Alivcmediaplayer *) mediaplayer {
        if (! _mediaPlayer) {
            // 1. Create a player instance.
            _mediaPlayer = [[AliVcMediaPlayer alloc] init];
        }
        return _mediaPlayer;
        } 
        -(void)player{
        
        self.contentView.frame = CGRectMake(0, 0, self.view.width, self.view.height-64);
        [self.view addSubview:self.contentView];
        [self.mediaPlayer create:self.contentView];
        self.mediaPlayer.scalingMode = scalingModeAspectFit;
        self.mediaPlayer.circlePlay = YES;
        self.mediaPlayer.dropBufferDuration = 3000;
        self.mediaPlayer.printLog = YES;
        AliVcMovieErrorCode err = [self.mediaPlayer prepareToPlay:[NSURL URLWithString:self.playUrl]];
        // 5. Check for an error to determine whether the stream can be played back.
        if (err ! = ALIVC_SUCCESS) {
            NSLog(@"chinese-playback failed");
        }else{
            [self.mediaPlayer play];
        }
        }
        
        ```

        For more information about how to use the iOS player, see [ApsaraVideo Player Basic](). For more information about the features and APIs of the iOS player, see [API Reference]().


## Step 4: Deliver a question through the application server. {#section_mbq_ghp_dgb .section}

When the caster is ready to broadcast a question, the on-site director needs to call an API of the application server to deliver the question. The API used for delivering the question contains the following parameters:

-    `liveId`: the unique ID of the live Q&A activity.
-    `questionId`: the ID of the question to be delivered.
-    `expiredSeconds`: the validity period for submitting the answer to the question, in seconds. Only the answers submitted within the specified period are valid.

The application server completes the following actions after receiving the request:

-   Finds the live stream information based on `liveId`, and calls an ApsaraVideo API to insert custom SEI signals \(containing `questionId`\) into the live stream. For more information about the API, see the API definition in the live Q&A scheme.

-   Initializes the Q&A session. A Q&A session includes the content of the question, the absolute timestamp when answer submission expires, and the number of users that select each option.


**Examples**

```language-text
https://live.aliyuncs.com?Action=AddTrancodeSEI&Domain=test101.cdnpe.com&App=xxx&Stream=xxx&Text=hahaha&Pattern=frame&Repeat=300&Delay=0&<common request parameters>

```

**Note:** In the live Q&A scenario, we recommend that you set `Pattern` to `frame` and `Repeat` to three times the keyframe interval. \(In the example, the value of `Repeat` is 300.\) These settings ensure that the player can obtain the SEI once it receives one frame in three keyframe intervals no matter whether frames are lost in such intervals. Because the SEI in frames may be duplicate with each other, the player needs to deduplicate the SEI.

**Considerations**

-   Because stream ingest has a fixed delay and the on-site director uses a cloud service to insert SEI signals, SEI signals may be inserted into an image earlier than expected. To resolve this issue, the on-site director needs to measure the stream ingest delay in advance and adds a fixed delay when inserting SEI signals into the live stream.
-   To measure the stream ingest delay, the on-site director can place a stopwatch on the screen. For example, if an SEI signal is inserted at T0 and the player detects the SEI signal when it plays the image with the clock time Ts, the stream ingest delay is `T0 - Ts` \(`Ts < T0`\).

    Assume that the on-site caster raises a question at 12:00:00 and that there is a 1-second delay for ingesting streams from the site to Alibaba Cloud. In this scenario, the on-site director needs to call the API to insert SEI signals at 12:00:01. Alternatively, the on-site director can call the API at 12:00:00 and set `delay` to `1000` milliseconds in the API. This ensures that the SEI signals are inserted into the image just at the right time when the caster raises the question.

-   After receiving the SEI signals, the client needs to obtain the question from the application server, which consumes a certain amount of communication time. When delivering a question, increase the value of `expiredSeconds` as needed, for example, increase it by 1 second.

## Step 5: The player parses the SEI. {#section_kqr_shp_dgb .section}

The player listens on the callback of SEI signals. You can use the SEI callback API of the player to obtain the SEI delivered from the application server.

-   Parse the SEI on an Android device.
    1.  Set the callback API.

        **setSEIDataListener**

        ```
        public void setSEIDataListener(MediaPlayerSEIDataListener
                    listener)
        ```

    2.  Listen on the callback of SEI signals.

        **MediaPlayer.MediaPlayerSEIDataListener**`public void onSEIdata(String data)`

-   Parse the SEI on an iOS device.
    1.  Add a listening notification API.

        ```
        // The notification received during live Q&A.
        [[NSNotificationCenter defaultCenter] addObserver:self
                                                selector:@selector(onSeiData:)
                                                    name:AliVcMediaPlayerSeiDataNotification object:self.mediaPlayer];
        ```

    2.  Process the SEI in the listening notification.

        ```
        - (void)onSeiData:(NSNotification *)notification{   
        NSDictionary* dict = [notification userInfo];
        if (dict) {
           NSString* seiData = [dict objectForKey:@"seiData"];
           if (seiData) {
               NSLog(@"sei data is %@",seiData);
        }
        ```


## Step 6: The application obtains and displays the complete question content. {#section_yny_b3p_dgb .section}

After obtaining the `questionId` contained in the SEI, the application sends a request \(containing `liveId` and `questionId`\) to the application server to obtain the question content.

After receiving the request, the application server sends the application a response containing the question content and `remainSeconds`. The remainSeconds parameter specifies the number of seconds left for submitting the answer to the question. The value of remainSeconds is calculated by the following formula:

```
Value of remainSeconds = Absolute timestamp when answer submission expires - Current absolute timestamp
```

``

## Step 7: The application counts down the seconds and reports the answers submitted by users to the application server. {#section_tlr_ztp_dgb .section}

-   After receiving the response, the application displays the question content and starts to count down based on the value of `remainSeconds`. Only the users who correctly answered the previous question can select an option to answer the current question. The users who incorrectly answered the previous question have failed the Q&A quiz and therefore cannot answer the current question.

-   After a user selects an option, the application sends a request \(containing `liveId`, `questionId`, `answerId`, and `userId`\) to report the user's answer to the application server. The user cannot change the option.

-   The users who do not select any options this time are considered to fail the Q&A quiz and therefore cannot answer the next question. No answer is reported for such users.

-   After reporting the answers to a question, the application records them as the Q&A results for determining whether a user can answer the next question.


## Step 8: The application server collects the answers. {#section_kn1_b5p_dgb .section}

After receiving the answers reported by the application, the application server needs to perform the following actions:

-   Checks for the Q&A session based on `liveId` and `questionId` in the answer reporting request. If the specified Q&A session does not exist, the application server rejects the request.
-   Checks whether the current absolute timestamp is later than the absolute timestamp when answer submission expires. If so, the answer submission times out and the answer becomes invalid.

    **Note:** Considering that there is a certain network delay for the application to upload answers, you can extend the timeout interval by a certain period of time, for example, by 2 seconds.

-   Collects statistics on the number of users who correctly answer the question. The number increases by 1 for each user who correctly answers the question.

## Step 9: Deliver the Q&A results. {#section_n1d_25p_dgb .section}

When the caster announces the expiration of answer submission and is ready to announce the Q&A results, the on-site director needs to call an API of the application server to deliver the Q&A results. The call request contains `liveId` and `questionId`.

Then, the application server calls an ApsaraVideo API to insert the SEI signal \(containing `questionId`\) into the live stream to instruct the application to request the Q&A results.

## Step 10: The application displays the Q&A results and the Q&A quiz goes to the next question. {#section_qnd_f5p_dgb .section}

-   When the application player obtains the SEI signal about the Q&A summary, the application checks whether the SEI signal is about the Q&A or Q&A summary. If the SEI signal is about the Q&A summary, the application sends a request containing `liveId` and `questionId` to the application server to obtain the Q&A summary.

-   After receiving the Q&A summary, the application displays a summary dialog box, showing whether the answer is correct and the number of users who select each option.

-   The summary dialog box is hidden after being displayed for a certain period of time. Then the next round of Q&A starts.


