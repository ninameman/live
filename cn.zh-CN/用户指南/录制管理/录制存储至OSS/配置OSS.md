# 配置OSS

如果要将直播录制下来的文件存储在OSS产品中，您需要先创建OSS bucket，授予直播写入OSS的权限，才能在OSS列表进行查看、下载、播放等操作。

如果更改OSS录制配置，需要进行重新推流配置才生效。

## 创建OSS bucket

1.  登录 [OSS控制台](https://oss.console.aliyun.com/index?spm=5176.2020520107.1002.d10oss.3dfe962ekybGY)。
2.  单击 **创建Bucket**。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0368600061/p21762.png)

3.  输入Bucket信息。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0368600061/p21763.png)

    **说明：** Bucket **区域** 与直播域名所在区域必须一致。如，直播域名所在区域是 **华东2**，因此，Bucket也必须选择 **华东2**。Bucket创建完成后，您可以根据使用需求来创建Bucket的文件夹。

4.  在Bucket列表中，单击您创建的Bucket名称，并单击 **文件管理** \> **新建目录**。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0368600061/p21764.png)

    **说明：** 当您的录制文件较多时，创建目录是为了对录制内容进行分类，方便对录制内容进行管理。

5.  在 **新建目录** 中，输入 **目录名**，并单击 **确定**。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0368600061/p21765.png)


## 配置直播写入OSS权限

视频直播录制文件和截图文件保存到用户OSS，需要授权live访问OSS，目前使用的是AliyunMTSDefaultRole角色。

1.  要将直播录制下来的文件存储在用户OSS的Bucket中，需要对直播服务Live授权访问OSS，[去授权](https://ram.console.aliyun.com/?spm=5176.12246746.0.0.2a817bbcYIpo3H#/role/authorize?request=%7B%22ReturnUrl%22:%22https:%2F%2Fmps.console.aliyun.com%22,%22Service%22:%22MTS%22,%22Requests%22:%7B%22request1%22:%7B%22TemplateId%22:%22DefaultRole%22,%22RoleName%22:%22AliyunMTSDefaultRole%22%7D%7D%7D)
2.  查看授权是否成功：主账号于阿里云官网，搜索“访问控制”\> RAM角色管理 \> 搜索角色：AliyunMTSDefaultRole \> 角色授权策略
3.  如使用子账号查看是否有AliyunMTSDefaultRole授权，需要主账号为其子账号配置AliyunRAMFullAccess权限

## 配置CDN域名

如录制文件存储在OSS中，您可以配置一个CDN加速域名，查看录制视频时会进行CDN加速服务。CDN会将您OSS存储的视频分发到全国各地的节点。用户访问时只需访问最近的CDN节点读取文件，而无需访问OSS的源文件，也不会消耗OSS的外网流量。不仅可提升边缘用户的访问速度和体验，同时，CDN的外网流量费用相对OSS外网流量较低，仅为OSS外网流量的50%，可有效的节省整体应用的网络费用。

1.  在您所创建的bucket页面，单击 **传输管理\>域名管理** \> **绑定域名**。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0368600061/p21768.png)

2.  在 **绑定用户域名** 中，配置CDN加速域名，并单击 **提交**。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/0368600061/p21769.png)

    如果您仅对视频进行存储，可不用配置CDN加速域名。

    **说明：** CDN加速域名与直播服务域名不能是同一个，请您分别进行配置。


