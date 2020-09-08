# rts\_worker\_demux\_info

查询媒体信息返回的数据类型。

定义

```

struct rts_worker_demux_info
{
    int [audio\_flag](#audio_flag);
    int [audio\_channels](#audio_channels);
    int [audio\_sample\_rate](#audio_sample_rate);

    int [video\_flag](#video_flag);
    int [video\_codec](#video_codec);
    int [video\_width](#video_width);
    int [video\_height](#video_height);
    int [video\_profile](#video_profile);
    int [video\_level](#video_level);

    unsigned char [spspps](#audio_sample_rate)[10 * 1024];
    int [spspps\_len](#spspps_len);
};
                    
```

成员

|成员|解释|
|--|--|
|audio\_flag|指示跟随其后的audio信息是否valid的flag。1表示valid, 0表示invalid|
|audio\_channels|音频channel数。当audio\_flag == 1的时候才有意义|
|audio\_sample\_rate|音频采样率。当audio\_flag == 1的时候才有意义|
|video\_flag|指示跟随其后的video信息是否valid的flag。1表示valid, 0表示invalid|
|video\_codec|视频帧类型。1表示h264。当video\_flag == 1的时候才有意义|
|video\_width|视频分辨率宽度。当video\_flag == 1的时候才有意义|
|video\_height|视频分辨率高度。当video\_flag == 1的时候才有意义|
|video\_profile|视频编码使用的profile。当video\_flag == 1，且video\_codec == 1的时候才有意义|
|video\_level|视频编码使用的level。当video\_flag == 1，且video\_codec == 1的时候才有意义|
|spspps|存放sps和pps数据，可以用于提前初始化解码器。有可能为空。当videoflag == 1，且video\_codec == 1的时候才有意义|
|spspps\_len|spspps的长度（字节为单位）。当video\_flag == 1，且video\_codec == 1的时候才有意义|

Remarks

无

