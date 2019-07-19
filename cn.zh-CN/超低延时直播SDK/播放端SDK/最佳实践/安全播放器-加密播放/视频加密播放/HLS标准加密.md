# HLS标准加密 {#concept_1253741 .concept}

介绍HLS标准加密的设置方式。

HLS标准加密支持 HTTP Live Streaming 中规定的通用加密方案，使用AES-128对视频内容本身进行加密，同时能支持所有的HLS播放器，用户可选择使用自研或开源的播放器。相比私有加密方案，灵活性更好，但使用门槛更高、安全性更低。HLS标准加密流程如下图所示。

![HLS标准加密流程](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/987747/156350755752193_zh-CN.png)

-   用户需搭建密钥管理服务，提供密钥生成（用于转码时对视频内容进行加密）和解密服务（用于播放时获取解密密钥），也可基于 阿里云KMS 进行封装。
-   用户需提供令牌颁发服务，用于验证播放端的身份，避免解密密钥被非法获取，此处为关键点，处理不好会千里之堤溃于蚁穴。
-   播放器和云端传输明文Key，容易被窃取。

具体可以参考[HLS标准加密流程](https://help.aliyun.com/document_detail/59885.html?spm=5176.product29194.6.607.2bynDX)。

## 如何播放HLS标准加密 {#section_q58_9ii_big .section}

阿里云播放器支持用户令牌传递，阿里CDN会动态修改m3u8文件中的解密URI，解密URI中会带上用户的令牌，业务方可以对令牌进行验证。比如：控制key的时效性。

## STS设置HlsUriToken {#section_3ih_a2x_8a9 .section}

STS设置HlsUriToken的使用方式如下：

-   Android使用方式

    通过`VidSts`播放源来设置playConfig，playConfig中携带mtsHlsUriToken参数。

    ``` {#codeblock_vtk_x7w_hus .language-java}
    VidSts vidsts = new VidSts();
    VidPlayerConfigGen playerConfig = new VidPlayerConfigGen();
    //设置用户令牌
    playerConfig.setMtsHlsUriToken("用户令牌");
    vidsts.setPlayConfig(playerConfig);
    ```

-   iOS使用方式

    通过AVPVidStsSource播放来设置playConfig，playConfig中携带mtsHlsUriToken参数。

    ``` {#codeblock_gop_y01_rfn .language-java}
    - (instancetype)initWithVid:(NSString *)vid
                    accessKeyId:(NSString *)accessKeyId
                accessKeySecret:(NSString *)accessKeySecret
                  securityToken:(NSString *)securityToken
                         region:(NSString *)region
                    playConfig:(NSString *)playConfig;
    - (void)setStsSource:(AVPVidStsSource*)source;
    ```


如何生成playConfig参数？SDK中提供了一个类：VidPlayerConfigGenerator，通过这个类的setHlsUriToken来设置令牌，然后最终通过generatePlayerConfig接口来生成playConfig。

``` {#codeblock_0ej_0yh_vl2 .language-java}
-(void) setHlsUriToken:(NSString*)MtsHlsUriToken;
-(NSString*) generatePlayerConfig;
```

## PlayAuth设置HlsUriToken {#section_j10_uzu_9u3 .section}

PlayAuth设置HlsUriToken的使用方式如下：

-   Android使用方式

    通过`VidAuth`播放源来设置playConfig，playConfig中携带mtsHlsUriToken参数。

    ``` {#codeblock_91u_hlz_6c9 .language-java}
    VidAuth vidauth = new VidAuth();
    VidPlayerConfigGen playerConfig = new VidPlayerConfigGen();
    //设置用户令牌
    playerConfig.setMtsHlsUriToken("用户令牌");
    vidauth.setPlayConfig(playerConfig);
    ```

-   iOS使用方式

    通过`AVPVidAuthSource`播放来设置playConfig，playConfig中携带mtsHlsUriToken参数。

    ``` {#codeblock_81y_30r_p45 .language-java}
    - (instancetype)initWithVid:(NSString *)vid
            playAuth:(NSString *)playAuth
              region:(NSString *)region
              playConfig:(NSString *)playConfig;
    - (void)setAuthSource:(AVPVidAuthSource*)source;
    ```


如何生成playConfig参数？SDK中提供了一个类：VidPlayerConfigGenerator，通过这个类的setHlsUriToken来设置令牌，然后最终通过generatePlayerConfig接口来生成playConfig。

``` {#codeblock_s9v_pjj_ldm .language-java}
-(void) setHlsUriToken:(NSString*)MtsHlsUriToken;
-(NSString*) generatePlayerConfig;
```

## MPS设置HlsUriToken {#section_dvo_v36_oi1 .section}

MPS设置HlsUriToken的使用方式如下：

-   Android使用方式

    Android创建`VidMps`对象后，通过调用setHlsUriToken方法设置。然后传递给播放器播放即可。

    ``` {#codeblock_ucv_1xt_mb5 .language-java}
    VidMps vidmps = new VidMps();
    //设置用户令牌
    vidmps.setHlsUriToken("用户令牌");
    ... // vidmps的其他设置。
    
    AliPlayer player = AliPlayerFactory.createAliPlayer(context);
    //设置vidmps到播放器
    player.setDataSource(vidmps);
    ...//播放器的其他设置
    ```

-   iOS使用方式

    通过AVPVidMpsSource播放来设置mtsHlsUriToken。

    ``` {#codeblock_9gb_26n_ewp .language-java}
    - (instancetype)initWithVid:(NSString*)vid
                     accId:(NSString *)accId
                 accSecret:(NSString*)accSecret
                  stsToken:(NSString*)stsToken
                  authInfo:(NSString*)authInfo
                    region:(NSString*)region
                playDomain:(NSString*)playDomain
            mtsHlsUriToken:(NSString*)mtsHlsUriToken;
    - (void)setMpsSource:(AVPVidMpsSource*)source;
    ```


