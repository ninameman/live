# 直播录制存储至VOD {#concept_84936_zh .concept}

视频直播服务将直播内容进行录制存储，并转入点播系统中进行管理。

在一个直播加速域名下，直播录制配置按直播推流的 AppName 和 StreamName 进行区分，即相同 AppName 和 StreamName 下的视频流（Stream）都按此 AppName 和 StreamName 下的录制配置进行录制。

## 说明 {#section_9qq_dys_036 .section}

-   您需要先开通视频点播服务，才能将视频存储至VOD。参见 [开始使用视频点播](https://help.aliyun.com/document_detail/51512.html?spm=a2c4g.11174283.6.555.3846149bpeOhZP)。

-   为了避免录制时，因网络抖动或临时断流而导致录制文件被异常截断，系统会延迟断流180s，即如果断流之后在180s内重新推流，系统会默认是同一路录制流，超过180s则认为是两路录制流。


## 创建直播转点播录制模板 {#section_e21_wtt_3t4 .section}

1.  登录 [视频直播控制台](https://live.console.aliyun.com/?spm=5176.2020520001.1001.113.O9moDX#/live/domains)。
2.  单击 **域名管理**。
3.  选择所需的播放域名，并单击右侧的 **模板管理**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84936/cn_zh/1532768517163/%E5%8D%95%E5%87%BB%20%E5%9F%9F%E5%90%8D%E7%AE%A1%E7%90%86-%E6%A8%A1%E6%9D%BF%E9%85%8D%E7%BD%AE.png)

4.  单击 **录制配置** \> **存储至VOD**，并单击 **添加**。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84936/cn_zh/1531721018078/%E7%9B%B4%E6%92%AD%E5%AD%98%E5%82%A8%E8%87%B3VOD%EF%BC%8C%E5%8D%95%E5%87%BB%E6%B7%BB%E5%8A%A0.png)

5.  在 **录制模板** 中，输入录制参数。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84936/cn_zh/1535116011546/%E7%82%B9%E6%92%AD%E5%BD%95%E5%88%B6%E6%A8%A1%E6%9D%BF.png)

    -   **AppName**：视频的应用名称，输入的 **AppName** 必须与直播推流的 **AppName** 保持一致方可生效。如果您想要进行域名级别录制，输入星号（\*）号即可。

    -   **StreamName**：存储至VOD支持流级别的录制。您只需输入指定的流名称即可。如果您想要进行全部流录制，即该**AppName**下的流全部录制，输入星号（\*）号即可。

**说明：** **AppName**与**StreamName**参数支持英文、数字、“-”、“\_”符号，长度限制在255字符以内。

    -   **录制周期**：**录制周期** 范围为15-360分钟，最大支持 6 小时录制。超过 6 小时，系统将按照录制命名规则生成新文件。**ts** 切片时长默认为 30s。

**说明：** 录制周期为当前直播转为点播文件后的最大时长。

    -   **录制转码模板**：从列表中选择存储转码规则，可以在点播服务中对录制的视频进行转码处理。

        存储转码规则设置是将录制下来的视频转换为可供传播的点播文件格式。可转码为不同规格的视频，也可以不转码即保持原画格式。您可以在点播服务中新增转码设置，详情参见下文。


## 在点播服务中创建存储规则 {#section_imq_fyc_ils .section}

1.  单击 **去点播控制台修改**， 进入 [视频点播控制台](https://vod.console.aliyun.com/?spm=5176.2020520107.0.0.780f53b3Fcustk#/vod/index)。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84936/cn_zh/1535116172597/%E7%82%B9%E6%92%AD%E5%BD%95%E5%88%B6%E6%A8%A1%E6%9D%BF.png)

2.  在视频点播控制台页面，单击 **媒体处理配置** \> **转码设置** \> **添加转码模板组**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20706/156888473861404_zh-CN.jpg)

3.  在 **添加转码模板组**页面，对 **模板名称**、**封装格式**、**清晰度**、**码率**、**分辨率** 等参数进行配置，并单击 **保存**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20706/156888473861415_zh-CN.jpg)

4.  创建好直播转点播 **录制转码模板**，您可在录制列表中查看。

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/84936/cn_zh/1535116356577/%E5%BD%95%E5%88%B6vod.png)


