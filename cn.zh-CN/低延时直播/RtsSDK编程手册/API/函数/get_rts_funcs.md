# get\_rts\_funcs

这是唯一一个对外可见的api。通过这个api获得其他api的指针。

原型

```

const struct rts_glue_funcs *get_rts_funcs(
    int [version](#version)
);
                        
```

参数

|参数|解释|
|--|--|
|version|api兼容版本。必须是2|

返回值

如果成功，返回[rts\_glue\_funcs]()指针。如果失败（一般是version参数不匹配），返回NULL

Remarks

获取[rts\_glue\_funcs]()变量。通过该变量得到其他api

