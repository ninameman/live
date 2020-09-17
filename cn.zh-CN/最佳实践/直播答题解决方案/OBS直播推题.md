# OBS直播推题

## 一、直播答题流程

直播答题通过推流SDK、定制版OBS或者阿里云OpenAPI在直播流中插入SEI信息（题目信息），当播放器解析到SEI信息后，会回调给用户的App，此时用户就可以将题目的具体题目内容展示出来。具体流程如下：

![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/3905520061/p55314.png)

**说明：** 详细接入请查看 [直播答题方案]()，按照说明提交工单申请接入。播放器接入见 [答题播放器](https://help.aliyun.com/document_detail/61908.html?spm=5176.doc61912.6.683.ObmM6C)。

## 二、OBS安装说明

Mac版安装说明

1.  下载 （参见 [SDK下载]()）OBS直播答题定制程序，直接打开运行。

2.  安装时需要信任，在 **系统设置** \> **安全与隐私** 中，单击 **仍要打开**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/66134/cn_zh/1516935547607/%E7%B2%98%E8%B4%B4%E5%9B%BE%E7%89%87.png)


Windows版安装说明

下载 （参见 [SDK下载]()）OBS直播答题定制程序，单击安装文件按提示进行安装，然后运行OBS。

## 三、参数配置

1.  打开OBS，单击右下角 **设置**，在弹出的设置对话框中，首先选中左侧 **输出** 选项，确认当前使用的编码器为x264。因为目前答题的场景主要是在手机上使用的，因此需要将输出分辨率调整成9:16比例。考虑到终端大屏的手机，可根据实际情况修改成540x960，码率也需要相应的做调整。

**说明：** 为了节省流量以及观看流畅，请选择合适的码率。

![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/66134/cn_zh/1517303347587/12.png)

    参数建议值：

    -   比特率：600

    -   cpu使用预设：faster

    -   关键帧间隔：1

    -   profile：high

    -   在网络传输过程中，视频到达终端有可能会丢帧，最好在视频流中多次插入sei信息。默认的为5次，应根据实际情况修改成相应数字。

    分辨率建议值：

    |对应|码率|帧率|
    |:-|:-|:-|
    |360×640|700k|20|
    |540×960|1000k|25|

2.  选中左侧 **流** 选项，设置Rtmp推流地址。以中心推流地址举例：完整的推流地址是`rtmp://video-center.alivecdn.com/sei/stream01?vhost=qt1.alivecdn.com`。其中，推流URL填写为阿里云提供的推流地址中appName前面部分，如`rtmp://video-center.alivecdn.com/sei/`，流名称为阿里云提供的推流地址中streamName后面部分（含鉴权信息），如`{streamName}?vhost=qt1.alivecdn.com`，`{streamName}`可根据业务情况进行分配设置。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/66134/cn_zh/1516935001323/%E5%9B%BE%E7%89%87%202.png)

    **说明：** 如果要在云端添加SEI功能，务必在推流地址中加上参数wm=1。如果在OBS中直接对视频插入SEI，此参数可以去除。


## 四、添加出题页面

在OBS界面右下角，单击直播答题按钮，并在弹出的对话框中填入答题网页地址，加载出答题页面。streamName的值应该与OBS设置的流名称保持一致。每次测试的时候最好换用不同的streamName。

![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/66134/cn_zh/1517304537377/e7db2c91-1ba9-4287-9041-ab0d357a01c1.png)

在调用该页面可以通过OBS内部接口直接对视频进行插入SEI信号。根据现场主持的人发出的信号，直接操作下发题目和下载答案操作即可。页面代码参见 [题目推送](http://paas-static.oss-cn-hangzhou.aliyuncs.com/demo/live.html?streamName=aliyun)。

**说明：** 答题页面中的网络请求参数包含了流id，目前Demo答题页面的流Id参数通过url中的streamName参数传入，该流id需要与参数配置中推流地址使用的\{streamName\}一致），demo中为aliyun，用户可替换为自己推流的流名称。

![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/66134/cn_zh/1517310355899/%E7%B2%98%E8%B4%B4%E5%9B%BE%E7%89%87.png)

## 五、配置场景开始直播

1.  预览窗口中确认摄像头采集正常，直播场景布置完毕，单击OBS界面右下方 **开始推流** 按钮，启动直播。更多OBS配置参见 [OBS使用说明]()。

2.  开始直播后，导播需要根据主持人的播报时机，在答题网页中进行题目插入操作。当主持人开始播报题目时，导播可单击相应题目后的 **下发题目** 按钮，在视频流中插入题目下发信息。同理，当主持人开始播报题目答案时，导播单击相应题目后的 **下发答案** 按钮，即可在播放端展示答题结果。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/66134/cn_zh/1516936524331/55.png)


## 六、注意事项

-   答题页面如何将题目信息插入到OBS视频流中？

    答题页面JS部分需要引入了Qt的 [qwebchannel.js](http://paas-static.oss-cn-hangzhou.aliyuncs.com/demo/qwebchannel.js)，用以支持在JS中回调OBS本地对象进行SEI插入，例如单击下发题目事件时，通过创建QWebChannel对象来获取本地内建的brige对象，进而调取该对象方法sendSEI来插入信息。因此修改答题页面时，必须确保引入该JS文件，同时确保回调对象名称及方法名称保持一致，否则将造成回调失效问题；

-   如何组织答题页面中的题目信息？

    目前答题页面中，题目信息包括题目id，题目内容，以及下发题目和下发答案操作。在下发题目和下发答案点击时，会触发SEI回调方法，将题目信息组织为Json信息回调给OBS插入视频。目前答题页面模板中，下发题目对应的Json格式为

    ```
    {
        "questionId": "001",//下载题目的ID
        "type": "startAnswer",
        showTime:15 //答案显示时间
    }
                        
    ```

    在OBS插入SEI后，需要通知服务器，对应的题目答题截止时间（超过答题时间，提交的答案无效），请求的格式如下：

    ```
    {
        liveId: seiLiveId,
        questionId: qid,
        expiredSeconds: 15,
        seiDelay:2000,
        noSEI:true
    }
                        
    ```

    下发答案对应的Json格式为：

    ```
    {
        "questionId": "001", 
        "type": "showResult", 
        "showTime": "5"
    }
                        
    ```

    修改答题页面时，可参考当前Json组织形式，按照业务需求进行修改。播放端收到题目信息后，会根据题目id到业务服务器请求详细的题目及答案信息。因此，在编辑题目信息时，请确保题目id对应正确，目前答题页面下发按钮对应的题目id目前赋值在链接属性data-role中。

-   下发题目和答案时如何通知到业务服务器？

    答题页面中，下发题目和答案操作触发的同时，会通过JS发送POST请求通知服务器。修改答题页面时，确保请求对应的服务地址更新为正确的地址。同时，请求中还包含当前对应的推流id，需要与步骤2中推流名称里自定义的liveId保持一致, 目前Demo中请求体里使用liveId参数形式为：`qt1.alivecdn.com/sei/{streamName}`，其中liveId参数通过url中的 streamName参数传入，参考参数配置中的流配置。

-   如何观看答题直播？

    在确认以上操作完毕后，在OBS中开始推流。目前阿里云已有最新的版本支持直播答题，可下载DEMO体验 [下载答题播放器SDK](http://paas-static.oss-cn-hangzhou.aliyuncs.com/demo/alivcvideosdk/index.html)。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/66134/cn_zh/1517986737422/QALive.png)


