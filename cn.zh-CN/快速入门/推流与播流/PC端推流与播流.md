PC端推流与播流 {#title-tn2-t0n-ekx}
=============================

视频直播使用边缘推流，优先将视频推流至最优CDN节点，保证您访问的都是最佳的上行网络，减少因上行传输带来的卡顿、拉流缓慢的问题。请您按照以下步骤进行推流和播流操作。{#shortdesc-dke-2ds-zuv}

前提条件 {#title-ate-xzk-qr7}
-------------------------

**推流和播放工具** {#p-w7r-idh-m0i}

{#p-w7r-idh-m0i}

* 推流工具：下载并安装推流工具。本文以使用OBS推流工具为例说明。下载地址见 [OBS官方下载地址](https://obsproject.com/download?spm=a2c4g.11186623.2.3.FRgTS8)。

  {#p-plq-8zm-d8z}
{#li-z1e-fha-47h}
* 播放工具：下载并安装播流工具。本文以使用VLC播放器为例说明。下载地址见 [VLC media player官方下载地址](http://www.videolan.org/vlc/?spm=a2c4g.11186623.2.3.HA1ICZ)。

  {#p-yeb-wiw-lcz}
{#li-2ji-j4z-qjq}

{#ul-fhl-wpc-bfb}

推流 {#title-ye0-p3j-vt5}
-----------------------

1. 登录 [视频直播控制台](https://live.console.aliyun.com/#/live/domains)。

   {#p-j5w-v4h-3v4}

2. 单击 **直播管理** **\>地址生成器** 。

   {#p-233-i0b-x4b}
{#li-dx2-124-l0u}
3. 选择您创建的 **播流域名** 和关联的 **推流域名** 。

   {#p-mgu-ewt-vos}
{#li-sey-rsv-7w2}
4. 输入 **AppName** 和 **StreamName** 。

   {#p-e3b-l3g-ywq}
{#li-qdn-a7e-w7j}
5. 单击 **开始生成** 。{#p-5zp-z56-k0j}

   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/9433469951/p33185.png){#p-bed-77p-aki}

   您可以获得推流地址和播流地址。{#p-hpg-fc9-dgd}

   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65174/154391691433187_zh-CN.png)
   {#p-hpg-fc9-dgd}
{#li-p3p-bbu-xiv}
6. 下载并安装OBS推流工具。{#p-y7q-7sx-m4w}

   关于OBS推流工具配置及使用，详情参见 [OBS推流工具](https://help.aliyun.com/document_detail/45212.html)。

   您需要将鉴权后的推流地址分两部分输入 **URL** 与 **流秘钥** 中。{#p-laz-99y-3s6}

   {#p-laz-99y-3s6}
   * **URL** ：填写包含 **AppName** 前的地址，

     {#p-avm-r05-a7s}
   {#li-4rv-1pv-9eu}
   * **流名称** ：填写包含 **StreamName** 后的地址。

     {#p-2vp-e7a-faq}
   {#li-sc2-x1f-j5a}

   {#ul-x5r-zr1-yfb}

   以推流地址`rtmp://push.aliyunlive.com/app/stream?auth_key=1543302081-0-0-9c6e7c8190c10bdfb3c0************`为例，{#p-ogr-q4s-60b}

   {#p-ogr-q4s-60b}
   * URL：填写`rtmp://push.aliyunlive.com/app/`

     {#p-4up-jl2-e0z}
   {#li-fys-dee-ey0}
   * 流名称：填写`stream?auth_key=1543302081-0-0-9c6e7c8190c10bdfb3c0************`{#p-0s3-3ld-qga}

     ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65174/154391691433188_zh-CN.png)
     {#p-k2o-2n6-57n}
   {#li-yfx-xqs-gk6}

   {#ul-dtx-ss1-yfb}
   **说明**

   以上推流地址示例由推流域名、AppName、StreamName和鉴权串组成，您需要根据实际情况，替换成您自己的AppName、StreamName和相应的鉴权串。

   {#li-9ci-gny-waj}
{#li-9ci-gny-waj}

{#ol-sbq-ywh-yfb}

播流 {#title-sni-al0-u2t}
-----------------------

1. 下载并安装VLC播放器。{#p-d95-fya-40q}

   关于VLC播放器使用，参见 [VLC播放器](https://help.aliyun.com/document_detail/52142.html?spm=a2c4g.11186623.6.863.5f8d1445E3P7Eh)。
   
{#li-m72-1ta-w3q}
2. 打开VLC播放器。

   {#p-0oi-077-xhh}
{#li-vc0-a24-dn2}
3. 单击 **媒体\>** **打开网络串流(N)。** {#p-lc3-00f-qxp}

   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1399691751/p33189.png)
   {#p-l1h-ir2-2jd}
{#li-y67-8uu-ude}
4. 根据推流操作 **步骤6** 获取播流地址。

   {#p-yny-amw-ufk}
{#li-hpi-li3-oc5}
5. 在 **请输入网络URL** 中，输入播流地址并单击播放。{#p-p3z-e8p-mq8}

   以播流地址`rtmp://play.aliyunlive.com/app/stream?auth_key=1543300311-0-0-d47ce016332bf280cf275********`为例，将播流地址复制到URL的输入框并单击 **播放** 即可。{#p-48q-drj-8jb}

   {#p-48q-drj-8jb}

   ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/4837056951/p33190.png){#p-1fy-fza-h7w}
   **说明**

   以上播流地址示例由播流域名、AppName、StreamName和鉴权串组成，您需要根据实际情况，替换成您自己的AppName、StreamName和相应的鉴权串。

   {#li-3f5-l0v-u92}
{#li-3f5-l0v-u92}

{#ol-inc-j13-yfb}
