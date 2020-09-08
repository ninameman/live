# rts\_frame

封装音频和视频帧的数据类型

定义

```

struct rts_frame
{
    void [buf](#buf);
    int [size](#size);
    int [is\_audio](#is_audio);
    unsigned long long [pts](#pts);
    unsigned long long [dts](#dts);
    int [flag](#flag);
    int [duration](#duration);
    void ([free\_ptr](#free_ptr))(struct rts_frame *);
    unsigned int [uid](#uid);
};
                    
```

成员

|成员|解释|
|--|--|
|buf|frame数据buffer|
|size|[buf](#buf)的字节数|
|is\_audio|1: 音频帧；0: 视频帧|
|pts|presentation time stamp, in ms|
|dts|decoding time stamp, in ms|
|flag|当视频帧的时候\(is\_audio == 0\), bit 0: key frame flag; bit 1: corruption flag|
|duration|frame duration, in ms|
|free\_ptr|函数指针，用来释放当前的rts\_frame对象|
|uid|reserved|

Remarks

free\_ptr: 参数是需要释放的rts\_frame对象，比如：

frm-\>free\_ptr\(frm\);

