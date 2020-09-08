# rts\_glue\_funcs

这个数据结构以函数指针的形式保存了api函数。调用者首先通过const struct rts\_glue\_funcs \*[get\_rts\_funcs]()\(int version\)来获取rts\_glue\_funcs变量，然后才能通过rts\_glue\_funcs变量访问其他api函数

定义

```

struct rts_glue_funcs
{
    int [api\_version](#api_version);
    int (* [preconfig](#preconfig))(const char *key, const char *val);
    void (* [open](#open))(const char *url, const char mode);
    void (* [close](#close))(void handle);
    long long (* [ioctl](#ioctl))(void *handle, const char *cmd, void arg);
    int (* [read](#read))(struct rtsframe **frame, void handle);
    int (* [write](#write))(struct rtsframe **frame, void *handle);
};
  
```

成员

|成员|解释|
|--|--|
|api\_version|api版本号。必须是2|
|preconfig|全局参数配置函数。调用顺序：在open前调用，不要在open后调用。详细描述参见[preconfig]()|
|open|打开一个流。详细描述参见[open]()|
|close|关闭一个流。详细描述参见[close]()|
|ioctl|参数配置/查询。详细描述参见[ioctl]()|
|read|读取一帧数据。详细描述参见[read]()|
|write|发送一帧数据。详细描述参见[write]()|

Remarks

无

