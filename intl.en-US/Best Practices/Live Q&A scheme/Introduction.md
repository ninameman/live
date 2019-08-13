# Introduction {#concept_66082_zh .concept}

Live Q&A is an activity during which users enter a live stream channel at the scheduled time and complete an online quiz under the guidance of a caster. Users who give correct answers to all twelve questions can share the bonus set for each activity. At the beginning of 2018, Internet circles witnessed a boom in "online Q&A games with big bonuses." You can introduce this interactive game to your business to build a highly interactive user community. The following section uses the live Q&A scheme provided by ApsaraVideo as an example to describe how to implement the live Q&A feature.

-   Before starting live Q&A, you must [register an Alibaba Cloud account](https://live.console.aliyun.com/?spm=5176.7991389.632955.btn1.131053a24JJS2m#/live/domains) and [activate ApsaraVideo Live](https://live.console.aliyun.com/?spm=5176.7991389.632955.btn1.131053a24JJS2m#/live/domains).
-   In the live Q&A scheme, we call an API through the application server to insert Supplemental Enhancement Information \(SEI\) signals into live streams, and use the Q&A player of ApsaraVideo to parse the SEI signals.

## Procedure {#section_0se_8d2_tei .section}

 **Step 1: Understand the live Q&A process.** 

1.  When the caster raises a question, the on-site director prepares to deliver the question.
2.  The on-site director calls an API through the application server on the access side to insert several SEI frames into the current location of the live video stream. The SEI content can be customized based on the business needs.
3.  ApsaraVideo Player SDK receives the video stream, parses the SEI frames in the stream, and sends a callback message to the application. The application immediately requests the question content from the application server and displays the question content to users.

    **Note:** Because stream ingest has a fixed delay and the on-site director uses a cloud service to insert SEI signals, SEI signals may be inserted into an image earlier than expected. To resolve this issue, the on-site director needs to measure the stream ingest delay in advance and adds a fixed delay when inserting SEI signals into the live stream.

    Assume that the on-site caster raises a question at 12:00:00 and that there is a 1-second delay for ingesting streams from the site to Alibaba Cloud. In this scenario, the on-site director needs to call the API to insert SEI signals at 12:00:01. Alternatively, the on-site director can call the API at 12:00:00 and set `delay` to `1000` milliseconds in the API. This ensures that the SEI signals are inserted into the image just at the right time when the caster raises the question.

    **Note:** 

    -   After receiving the SEI signals, the client needs to obtain the question from the application server, which consumes a certain amount of communication time. In the actual Q&A system, you can extend the answer submission period to an appropriate extent, for example, by 1 second based on the original one.
    -   After users answer the question, the client needs to report the answers, which consumes a certain amount of communication time. In the actual Q&A system, the application server allows a grace period for users to submit answers. For example, answers received within a 1-second delay of the original answer submission period are all considered valid.
    The following figure shows the architecture of the live Q&A scheme.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20757/156568102755298_en-US.png)


 **Step 2: Activate ApsaraVideo Live and prepare for starting live Q&A.** 

-   Activate ApsaraVideo Live first.
-   Submit a ticket containing the domain name and application name to enable the feature of inserting SEI signals on ApsaraVideo.
-   When ingesting streams, add the `wm=1` parameter to the ingest URL.

 **Step 3: Call the API through the application server.** 

As described in the previous process, the application server on the access side needs to call the following API to insert SEI signals into a live stream.

**Note:** Alternatively, you can use the [custom OBS tool]() provided by ApsaraVideo to deliver questions.

1.  API for inserting SEI signals
    -   Request parameters

        |Name|Type|Required|Description|
        |:---|:---|:-------|:----------|
        |Action|String|Yes|The operation that you want to perform. Set the value to AddTrancodeSEI.|
        |DomainName|String|Yes|The CDN domain name.|
        |AppName|String|Yes|The name of the live streaming application.|
        |StreamName|String|Yes|The name of the live stream. SEI will be inserted into this stream and all its encoded streams.|
        |Text|String|Yes|The SEI text. Length constraint: 4,000 bytes.|
        |Pattern|String|Yes|Indicates whether to insert SEI into each keyframe or frame. Valid values: keyframe and frame.

 |
        |Repeat|Integer|Yes|The number of times that SEI is inserted. A value of -1 indicates that SEI is inserted for unlimited times until the end of live streaming.|
        |Delay|Integer|Yes|The delay for inserting SEI upon the request. Unit: milliseconds.|

    -   Response parameters

        |Name|Type|Description|
        |:---|:---|:----------|
        |RequestId|String|The GUID generated by Alibaba Cloud for the request.|

    -   Error codes

        |Error code|Error message|HTTP status code|Description|
        |:---------|:------------|:---------------|:----------|
        |InvalidDomain.NotFound|The domain provided does not exist in our records.|404|The error message returned when the domain name does not exist or does not belong to the current user.|
        |IllegalOperation|Illegal domain operate is not permitted.|403|The error message returned when the current operation is not supported. For example, the domain name is not used for live streaming.|
        |InvalidParams|Invalid parameters|400|The error message returned when a parameter is invalid.|
        |InternalError|The request processing has failed due to some unknown error.|500|The error message returned when an unknown error occurred in the background.|

2.  Examples

    ``` {#codeblock_0mq_x18_p26}
    https://live.aliyuncs.com?Action=AddTrancodeSEI&Domain=test101.cdnpe.com&App=xxx&Stream=xxx&Text=hahaha&Pattern=frame&Repeat=300&Delay=0&<common request parameters>
    					
    ```

    **Note:** In the live Q&A scenario, we recommend that you set `Pattern` to `frame` and `Repeat` to three times the keyframe interval. \(In the example, the value of `Repeat` is 300.\) These settings ensure that the player can obtain the SEI once it receives one frame in three keyframe intervals no matter whether frames are lost in such intervals. Because the SEI in frames may be duplicate with each other, the player needs to deduplicate the SEI.


 **Step 4: Integrate and use ApsaraVideo Player SDK.** 

Integrate ApsaraVideo Player SDK first. For more information, see [Player SDK \> Product introduction]().

For live Q&A, ApsaraVideo Player SDK provides the feature of calling back SEI. The following section describes the SEI callback APIs for Android and iOS devices.

1.  SEI callback API for Android devices

    Set the SEI callback API in the player to obtain SEI for business processing. The methods are as follows:

    -   **setSEIDataListener** 

        `public void setSEIDataListener(MediaPlayerSEIDataListener listener)`

        Description: Set the SEI callback API in the player to obtain SEI in streams.

        Parameter: listener, which indicates the callback listener.

    -   **MediaPlayer.MediaPlayerSEIDataListener** 

        `public void onSEIdata(String data)`

        Description: Listen on SEI callback messages.

        Parameter: data, which indicates the SEI to be called back.

    **Note:** In a playback process, the same SEI is called back only once.

     **Examples** 

    ``` {#codeblock_ori_jsk_w6g}
    aliVcMediaPlayer = new AliVcMediaPlayer(DemoLiveAnswerActivity.this, videoSurface);
    aliVcMediaPlayer.setSEIDataListener(new MediaPlayer.MediaPlayerSEIDataListener() {
            @Override
            public void onSEIdata(String data) {
                   praseData(data); // Parse SEI data.
            }
    });
    aliVcMediaPlayer.setMaxBufferDuration(3 * 1000);
    aliVcMediaPlayer.prepareAndPlay(liveUrl);
    
    private void praseData(String data) {
    // Parse the SEI into the format that meets the business needs and then perform business processing.
         JSONObject jsonObject = null;
         try {
             jsonObject = new JSONObject(data);
         } catch (JSONException e) {
             e.printStackTrace();
         }
    
         SeiInfo seiInfo = SeiInfo.getFromJson(jsonObject);
         if (seiInfo == null) {
             Toast.makeText(getApplicationContext(), "SEI data error", Toast.LENGTH_SHORT).show();
             return;
         }
    
         if (seiInfo.type.equals("startAnswer")) {
         // Request question content from the application server.
             requestQuestion(seiInfo.questionId);
         } else if (seiInfo.type.equals("showResult")) {
         // Request the Q&A summary from the application server.
             requestQuestionReport(seiInfo.questionId, seiInfo.showTime);
         }
    
     }
    						
    ```

    For more information, see the demo.

2.  SEI callback API for iOS devices

    Listen on the SEI data notification in the player to obtain SEI data. The notification is as follows:

    AliVcMediaPlayerSeiDataNotification

     **Examples** 

    Add a listening notification API.

    ``` {#codeblock_6pg_ios_5zj}
    // The message received during live Q&A.
        [[NSNotificationCenter defaultCenter] addObserver:self
                                                 selector:@selector(onSeiData:)
                                                     name:AliVcMediaPlayerSeiDataNotification object:self.mediaPlayer];
    
    							
    ```

    Process the SEI in the listening notification.

    ``` {#codeblock_e01_kk8_tkm}
    // Answer questions.
    - (void)onSeiData:(NSNotification *)notification{
        /*
        {
         "questionId": "001”,
         "type": "startAnswer"
         } Start to answer questions.
    
         {
         "questionId": "001”,
         "type": "showResult",
         "showTime": "5"
         } Show the Q&A result.
    
         */
        NSDictionary* dict = [notification userInfo];
        if (dict) {
            NSString* seiData = [dict objectForKey:@"seiData"];
            if (seiData) {
                NSLog(@"sei data is %@",seiData);
        }
    
      }
    							
    ```

    For more information, see the demo.


## Considerations {#section_4z8_u6j_w4b .section}

-   How to cope with the player delay

    You can set the longest player delay to ensure the same delay on each terminal. Generally, a longer delay indicates a stronger jitter resistance capability, and a shorter delay indicates a higher video stalling rate. Considering the overall delay of the entire link for live Q&A, the delay setting affects the validity time of each question. If the player delay is 3 seconds and the answer submission period is 10 seconds, the validity time of each question is 13 \(which equals 10 plus 3\) seconds.

    In @property\(nonatomic, readwrite\) int dropBufferDuration;, the dropBufferDuration parameter specifies the player delay for iOS devices, in milliseconds.

    In public void setMaxBufferDuration\(int duration\);, the setMaxBufferDuration API controls the player delay for Android devices. The duration parameter specifies the player delay, in milliseconds.

-   How to cope with the question delivery delay

    After receiving the SEI signals, the client needs to obtain the question from the application server, which consumes a certain amount of communication time. When delivering a question, increase the value of `expiredSeconds` as needed, for example, increase it by 1 second.


