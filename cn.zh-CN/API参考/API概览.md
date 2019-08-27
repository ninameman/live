# API概览 {#doc_20771 .concept}

视频直播提供以下相关API接口。

## 调用方式 {#section_5ug_zhg_uxw .section}

|API|描述|
|---|--|
|[请求结构](cn.zh-CN/API参考/调用方式/请求结构.md)|请求结构|
|[返回结果](cn.zh-CN/API参考/调用方式/返回结果.md)|调用 API 服务后返回数据采用统一格式：|
|[签名机制](cn.zh-CN/API参考/调用方式/签名机制.md)|签名机制|

## 域名管理 {#section_ie0_qkv_pd6 .section}

|API|描述|
|---|--|
|[DescribeLiveDomainDetail](cn.zh-CN/API参考/域名管理/DescribeLiveDomainDetail.md)|调用DescribeLiveDomainDetail获取指定直播域名配置的基本信息。|
|[DescribeLiveCertificateDetail](cn.zh-CN/API参考/域名管理/DescribeLiveCertificateDetail.md)|调用DescribeLiveCertificateDetail获取证书详细信息。|
|[AddLiveDomain](cn.zh-CN/API参考/域名管理/AddLiveDomain.md)|调用AddLiveDomain添加直播域名，一次只能提交一个域名。|
|[AddLiveDomainMapping](cn.zh-CN/API参考/域名管理/AddLiveDomainMapping.md)|调用AddLiveDomainMapping添加直播域名播流域名和推流域名的映射关系配置。|
|[DeleteLiveDomain](cn.zh-CN/API参考/域名管理/DeleteLiveDomain.md)|调用DeleteLiveDomain删除已添加的直播域名。|
|[DeleteLiveDomainMapping](cn.zh-CN/API参考/域名管理/DeleteLiveDomainMapping.md)|调用DeleteLiveDomainMapping删除直播域名播流域名和推流域名的映射关系配置。|
|[DescribeLiveUserDomains](cn.zh-CN/API参考/域名管理/DescribeLiveUserDomains.md)|调用DescribeLiveUserDomains查询用户名下所有的直播域名。|
|[DescribeLiveCertificateList](cn.zh-CN/API参考/域名管理/DescribeLiveCertificateList.md)|调用DescribeLiveCertificateList获取证书列表信息。|
|[SetLiveDomainCertificate](cn.zh-CN/API参考/域名管理/SetLiveDomainCertificate.md)|调用SetLiveDomainCertificate设置某域名下证书功能是否启用及修改证书信息。|
|[BatchSetLiveDomainConfigs](cn.zh-CN/API参考/域名管理/BatchSetLiveDomainConfigs.md)|调用BatchSetLiveDomainConfigs批量配置域名。|
|[BatchDeleteLiveDomainConfigs](cn.zh-CN/API参考/域名管理/BatchDeleteLiveDomainConfigs.md)|调用BatchDeleteLiveDomainConfigs批量删除域名配置。|
|[DescribeLiveDomainConfigs](cn.zh-CN/API参考/域名管理/DescribeLiveDomainConfigs.md)|调用DescribeLiveDomainConfigs查询直播域名配置，一次可查询多个功能配置。|
|[StartLiveDomain](cn.zh-CN/API参考/域名管理/StartLiveDomain.md)|调用StartLiveDomain启用状态为停用的直播域名，将DomainStatus变更为online。|
|[StopLiveDomain](cn.zh-CN/API参考/域名管理/StopLiveDomain.md)|调用StopLiveDomain停用某个直播域名，将DomainStatus变更为offline。|

## 直播拉流 {#section_6sr_etr_p6u .section}

|API|描述|
|---|--|
|[AddLivePullStreamInfoConfig](cn.zh-CN/API参考/直播拉流/AddLivePullStreamInfoConfig.md)|添加直播拉流信息，仅支持拉取直播流。 支持rtmp，http，flv格式。|
|[DescribeLivePullStreamConfig](cn.zh-CN/API参考/直播拉流/DescribeLivePullStreamConfig.md)|调用DescribeLivePullStreamConfig查询域名下拉流配置信息。|
|[DeleteLivePullStreamInfoConfig](cn.zh-CN/API参考/直播拉流/DeleteLivePullStreamInfoConfig.md)|调用DeleteLivePullStreamInfoConfig删除拉流信息。|

## 直播流管理 {#section_tu8_1sc_r4n .section}

|API|描述|
|---|--|
|[DescribeLiveStreamsOnlineList](cn.zh-CN/API参考/直播流管理/DescribeLiveStreamsOnlineList.md)|调用DescribeLiveStreamsOnlineList查看指定域名下（或者指定域名下某个应用）的所有正在推的流的信息。|
|[DescribeLiveStreamsPublishList](cn.zh-CN/API参考/直播流管理/DescribeLiveStreamsPublishList.md)|调用DescribeLiveStreamsPublishList获取某一时间段内某个域名（或域名下某应用或某个流）的推流记录。|
|[DescribeLiveStreamsBlockList](cn.zh-CN/API参考/直播流管理/DescribeLiveStreamsBlockList.md)|调用DescribeLiveStreamsBlockList获取域名下直播流播放的黑名单。|
|[DescribeLiveStreamsControlHistory](cn.zh-CN/API参考/直播流管理/DescribeLiveStreamsControlHistory.md)|调用DescribeLiveStreamsControlHistory获取某个域名或应用下的直播流操作记录。|
|[DescribeLiveStreamBitRateData](cn.zh-CN/API参考/直播流管理/DescribeLiveStreamBitRateData.md)|调用DescribeLiveStreamBitRateData查询RTMP协议的直播流的设置时间范围内的一组帧率和码率，适用于获取历史数据。|
|[ForbidLiveStream](cn.zh-CN/API参考/直播流管理/ForbidLiveStream.md)|调用ForbidLiveStream禁止某条流的推送，可以预设某个时刻将流恢复。|
|[ResumeLiveStream](cn.zh-CN/API参考/直播流管理/ResumeLiveStream.md)|调用ResumeLiveStream恢复某条流的推送。|
|[DescribeLiveStreamsFrameRateAndBitRateData](cn.zh-CN/API参考/直播流管理/DescribeLiveStreamsFrameRateAndBitRateData.md)|调用DescribeLiveStreamsFrameRateAndBitRateData实时查询直播流帧率和码率数据。|
|[DescribeLiveDomainOnlineUserNum](cn.zh-CN/API参考/直播流管理/DescribeLiveDomainOnlineUserNum.md)|调用DescribeLiveDomainOnlineUserNum查询域名下所有流某分钟的在线人数信息。|
|[DescribeLiveDomainFrameRateAndBitRateData](cn.zh-CN/API参考/直播流管理/DescribeLiveDomainFrameRateAndBitRateData.md)|调用DescribeLiveDomainFrameRateAndBitRateData查询直播域名下流帧率和码率数据。|

## 推流回调 {#section_s5z_bj8_bvt .section}

|API|描述|
|---|--|
|[SetLiveStreamsNotifyUrlConfig](cn.zh-CN/API参考/推流回调/SetLiveStreamsNotifyUrlConfig.md)|调用SetLiveStreamsNotifyUrlConfig设置推流回调配置。|
|[DescribeLiveStreamsNotifyUrlConfig](cn.zh-CN/API参考/推流回调/DescribeLiveStreamsNotifyUrlConfig.md)|调用DescribeLiveStreamsNotifyUrlConfig查询推流回调配置。|
|[DeleteLiveStreamsNotifyUrlConfig](cn.zh-CN/API参考/推流回调/DeleteLiveStreamsNotifyUrlConfig.md)|调用DeleteLiveStreamsNotifyUrlConfig删除推流回调配置。|
|[回调格式说明](cn.zh-CN/API参考/推流回调/回调格式说明.md)|流状态实时信息回调，可以及时通知用户推流或断流操作结果。|

## 直播时移 {#section_upw_lid_guf .section}

|API|描述|
|---|--|
|[直播时移](cn.zh-CN/API参考/直播时移/直播时移.md)|直播时移|

## 直播转码 {#section_yu4_e5e_fyr .section}

|API|描述|
|---|--|
|[AddLiveStreamTranscode](cn.zh-CN/API参考/直播转码/AddLiveStreamTranscode.md)|调用AddLiveStreamTranscode添加转码配置信息。|
|[AddCustomLiveStreamTranscode](cn.zh-CN/API参考/直播转码/AddCustomLiveStreamTranscode.md)|调用AddCustomLiveStreamTranscode添加自定义转码配置信息。|
|[DeleteLiveStreamTranscode](cn.zh-CN/API参考/直播转码/DeleteLiveStreamTranscode.md)|调用DeleteLiveStreamTranscode删除转码配置信息。|
|[DescribeLiveStreamTranscodeInfo](cn.zh-CN/API参考/直播转码/DescribeLiveStreamTranscodeInfo.md)|调用DescribeLiveStreamTranscodeInfo查询转码配置信息。|
|[AddTrancodeSEI](cn.zh-CN/API参考/直播转码/AddTrancodeSEI.md)|调用AddTrancodeSEI添加转码SEI信息。|

## 直播转点播 {#section_kwf_nix_7qr .section}

|API|描述|
|---|--|
|[AddLiveRecordVodConfig](cn.zh-CN/API参考/直播转点播/AddLiveRecordVodConfig.md)|调用AddLiveRecordVodConfig增加直播录制转点播配置，将录制内容保存到点播媒资库。|
|[DeleteLiveRecordVodConfig](cn.zh-CN/API参考/直播转点播/DeleteLiveRecordVodConfig.md)|调用DeleteLiveRecordVodConfig删除直播录制转点播配置。|
|[DescribeLiveRecordVodConfigs](cn.zh-CN/API参考/直播转点播/DescribeLiveRecordVodConfigs.md)|调用DescribeLiveRecordVodConfigs查询直转点配置列表。|

## 直播录制 {#section_t2p_eqj_vua .section}

|API|描述|
|---|--|
|[RealTimeRecordCommand](cn.zh-CN/API参考/直播录制/RealTimeRecordCommand.md)|调用RealTimeRecordCommand按需完成手动录制。例如，动态地启动、停止录制 。|
|[DescribeLiveRecordConfig](cn.zh-CN/API参考/直播录制/DescribeLiveRecordConfig.md)|调用DescribeLiveRecordConfig查询域名下所有App录制配置。|
|[按需录制回调](cn.zh-CN/API参考/直播录制/按需录制回调.md)|进行录制配置之后，您可以选择是否按需录制。|
|[录制事件回调](cn.zh-CN/API参考/直播录制/录制事件回调.md)|录制事件回调|
|[AddLiveAppRecordConfig](cn.zh-CN/API参考/直播录制/AddLiveAppRecordConfig.md)|调用AddLiveAppRecordConfig配置APP录制，输出内容保存到OSS中。|
|[DeleteLiveAppRecordConfig](cn.zh-CN/API参考/直播录制/DeleteLiveAppRecordConfig.md)|调用DeleteLiveAppRecordConfig解除录制配置。|
|[DescribeLiveStreamRecordContent](cn.zh-CN/API参考/直播录制/DescribeLiveStreamRecordContent.md)|调用DescribeLiveStreamRecordContent查询录制内容。|
|[CreateLiveStreamRecordIndexFiles](cn.zh-CN/API参考/直播录制/CreateLiveStreamRecordIndexFiles.md)|调用CreateLiveStreamRecordIndexFiles创建录制索引文件。|
|[DescribeLiveStreamRecordIndexFile](cn.zh-CN/API参考/直播录制/DescribeLiveStreamRecordIndexFile.md)|调用DescribeLiveStreamRecordIndexFile查询单个录制索引文件。|
|[DescribeLiveStreamRecordIndexFiles](cn.zh-CN/API参考/直播录制/DescribeLiveStreamRecordIndexFiles.md)|调用DescribeLiveStreamRecordIndexFiles查询某个时间段内的所有录制索引文件。|
|[AddLiveRecordNotifyConfig](cn.zh-CN/API参考/直播录制/AddLiveRecordNotifyConfig.md)|调用AddLiveRecordNotifyConfig添加域名级别录制回调配置。|
|[DeleteLiveRecordNotifyConfig](cn.zh-CN/API参考/直播录制/DeleteLiveRecordNotifyConfig.md)|调用DeleteLiveRecordNotifyConfig删除域名级别录制回调配置。|
|[DescribeLiveRecordNotifyConfig](cn.zh-CN/API参考/直播录制/DescribeLiveRecordNotifyConfig.md)|调用DescribeLiveRecordNotifyConfig查询域名级别录制回调配置。|
|[UpdateLiveRecordNotifyConfig](cn.zh-CN/API参考/直播录制/UpdateLiveRecordNotifyConfig.md)|调用UpdateLiveRecordNotifyConfig更新域名级别录制回调配置。|

## 直播截图 {#section_tjm_yns_xy9 .section}

|API|描述|
|---|--|
|[DescribeLiveStreamSnapshotInfo](cn.zh-CN/API参考/直播截图/DescribeLiveStreamSnapshotInfo.md)|调用DescribeLiveStreamSnapshotInfo查询一段时间内截图内容。|
|[AddLiveAppSnapshotConfig](cn.zh-CN/API参考/直播截图/AddLiveAppSnapshotConfig.md)|调用AddLiveAppSnapshotConfig配置截图信息。输出内容保存到OSS中，重新推流即生效。|
|[DeleteLiveAppSnapshotConfig](cn.zh-CN/API参考/直播截图/DeleteLiveAppSnapshotConfig.md)|调用DeleteLiveAppSnapshotConfig解除直播流下AppName的截图配置，重新推流后生效。|
|[DescribeLiveSnapshotConfig](cn.zh-CN/API参考/直播截图/DescribeLiveSnapshotConfig.md)|调用DescribeLiveSnapshotConfig查询域名下的截图配置。|
|[UpdateLiveAppSnapshotConfig](cn.zh-CN/API参考/直播截图/UpdateLiveAppSnapshotConfig.md)|调用UpdateLiveAppSnapshotConfig更新直播流下的截图配置。输出内容保存到OSS中，重新推流后生效。|

## 直播审核 {#section_t2v_4ek_hag .section}

|API|描述|
|---|--|
|[DescribeLiveSnapshotDetectPornConfig](cn.zh-CN/API参考/直播审核/DescribeLiveSnapshotDetectPornConfig.md)|调用DescribeLiveSnapshotDetectPornConfig查询审核配置。|
|[AddLiveSnapshotDetectPornConfig](cn.zh-CN/API参考/直播审核/AddLiveSnapshotDetectPornConfig.md)|调用AddLiveSnapshotDetectPornConfig可按照域名和App级别配置直播流审核服务。|
|[AddLiveDetectNotifyConfig](cn.zh-CN/API参考/直播审核/AddLiveDetectNotifyConfig.md)|调用AddLiveDetectNotifyConfig添加回调通知URL。|
|[DescribeLiveDetectNotifyConfig](cn.zh-CN/API参考/直播审核/DescribeLiveDetectNotifyConfig.md)|调用DescribeLiveDetectNotifyConfig查询回调通知URL。|
|[UpdateLiveSnapshotDetectPornConfig](cn.zh-CN/API参考/直播审核/UpdateLiveSnapshotDetectPornConfig.md)|调用UpdateLiveSnapshotDetectPornConfig更新审核配置。|
|[UpdateLiveDetectNotifyConfig](cn.zh-CN/API参考/直播审核/UpdateLiveDetectNotifyConfig.md)|调用UpdateLiveDetectNotifyConfig更新回调通知URL。|
|[DeleteLiveSnapshotDetectPornConfig](cn.zh-CN/API参考/直播审核/DeleteLiveSnapshotDetectPornConfig.md)|调用DeleteLiveSnapshotDetectPornConfig删除直播审核的配置。|
|[DeleteLiveDetectNotifyConfig](cn.zh-CN/API参考/直播审核/DeleteLiveDetectNotifyConfig.md)|调用DeleteLiveDetectNotifyConfig删除回调通知URL。|

## 资源监控 {#section_ncu_iku_upq .section}

|API|描述|
|---|--|
|[DescribeLiveDomainBpsData](cn.zh-CN/API参考/资源监控/DescribeLiveDomainBpsData.md)|调用DescribeLiveDomainBpsData查询直播域名的网络带宽监控数据。|
|[DescribeLiveDomainRecordData](cn.zh-CN/API参考/资源监控/DescribeLiveDomainRecordData.md)|调用DescribeLiveDomainRecordData查询直播域名录制时长数据。|
|[DescribeLiveDomainSnapshotData](cn.zh-CN/API参考/资源监控/DescribeLiveDomainSnapshotData.md)|调用DescribeLiveDomainSnapshotData查询直播域名截图张数数据。|
|[DescribeLiveDomainTrafficData](cn.zh-CN/API参考/资源监控/DescribeLiveDomainTrafficData.md)|调用DescribeLiveDomainTrafficData查询直播域名网络流量监控数据。|
|[DescribeLiveDomainTranscodeData](cn.zh-CN/API参考/资源监控/DescribeLiveDomainTranscodeData.md)|调用DescribeLiveDomainTranscodeData查询直播域名转码时长数据。|
|[DescribeLiveStreamOnlineUserNum](cn.zh-CN/API参考/资源监控/DescribeLiveStreamOnlineUserNum.md)|调用DescribeLiveStreamOnlineUserNum查询直播流实时在线人数。|
|[DescribeLiveDomainRealTimeBpsData](cn.zh-CN/API参考/资源监控/DescribeLiveDomainRealTimeBpsData.md)|调用DescribeLiveDomainRealTimeBpsData获取域名1分钟粒度带宽数据。|
|[DescribeLiveDomainRealTimeHttpCodeData](cn.zh-CN/API参考/资源监控/DescribeLiveDomainRealTimeHttpCodeData.md)|调用DescribeLiveDomainRealTimeHttpCodeData获取加速域名1分钟粒度的HTTP返回码占比数据。|
|[DescribeLiveDomainRealTimeTrafficData](cn.zh-CN/API参考/资源监控/DescribeLiveDomainRealTimeTrafficData.md)|调用DescribeLiveDomainRealTimeTrafficData获取加速域名的1分钟流量监控数据。|
|[DescribeLiveStreamHistoryUserNum](cn.zh-CN/API参考/资源监控/DescribeLiveStreamHistoryUserNum.md)|调用DescribeLiveStreamHistoryUserNum查询直播流历史在线人数。|

## 导播服务API {#section_58h_drr_0ae .section}

|API|描述|
|---|--|
|[CreateCaster](cn.zh-CN/API参考/导播服务/CreateCaster.md)|调用CreateCaster创建导播台。|
|[AddCasterLayout](cn.zh-CN/API参考/导播服务/AddCasterLayout.md)|调用AddCasterLayout添加导播台布局。|
|[AddCasterVideoResource](cn.zh-CN/API参考/导播服务/AddCasterVideoResource.md)|调用AddCasterVideoResource添加视频源，视频源数量受限于导播台输入路数。|
|[AddCasterEpisode](cn.zh-CN/API参考/导播服务/AddCasterEpisode.md)|调用AddCasterEpisode添加导播台节目。|
|[AddCasterComponent](cn.zh-CN/API参考/导播服务/AddCasterComponent.md)|调用AddCasterComponent添加组件。|
|[AddCasterProgram](cn.zh-CN/API参考/导播服务/AddCasterProgram.md)|调用AddCasterProgram添加导播台节目单。|
|[AddCasterEpisodeGroup](cn.zh-CN/API参考/导播服务/AddCasterEpisodeGroup.md)|调用AddCasterEpisodeGroup添加导播台节目列表。|
|[AddCasterEpisodeGroupContent](cn.zh-CN/API参考/导播服务/AddCasterEpisodeGroupContent.md)|调用AddCasterEpisodeGroupContent添加导播台节目列表。|
|[CopyCaster](cn.zh-CN/API参考/导播服务/CopyCaster.md)|调用CopyCaster复制导播台，复制指定导播台并返回新导播台实例。|
|[CopyCasterSceneConfig](cn.zh-CN/API参考/导播服务/CopyCasterSceneConfig.md)|调用CopyCasterSceneConfig将原场景配置应用至目标场景并生效，仅限PVW场景配置拷贝至PGM场景。|
|[DeleteCaster](cn.zh-CN/API参考/导播服务/DeleteCaster.md)|调用DeleteCaster删除导播台。|
|[DeleteCasterLayout](cn.zh-CN/API参考/导播服务/DeleteCasterLayout.md)|调用DeleteCasterLayout删除布局数据。|
|[DeleteCasterVideoResource](cn.zh-CN/API参考/导播服务/DeleteCasterVideoResource.md)|调用DeleteCasterVideoResource删除视频资源。|
|[DeleteCasterEpisode](cn.zh-CN/API参考/导播服务/DeleteCasterEpisode.md)|调用DeleteCasterEpisode删除导播台节目。|
|[DeleteCasterProgram](cn.zh-CN/API参考/导播服务/DeleteCasterProgram.md)|调用DeleteCasterProgram删除导播台节目单。|
|[DeleteCasterEpisodeGroup](cn.zh-CN/API参考/导播服务/DeleteCasterEpisodeGroup.md)|调用DeleteCasterEpisodeGroup删除导播台节目列表。|
|[DeleteCasterComponent](cn.zh-CN/API参考/导播服务/DeleteCasterComponent.md)|调用DeleteCasterComponent删除组件。|
|[DeleteCasterSceneConfig](cn.zh-CN/API参考/导播服务/DeleteCasterSceneConfig.md)|调用DeleteCasterSceneConfig清除指定场景的配置信息。|
|[DescribeCasterConfig](cn.zh-CN/API参考/导播服务/DescribeCasterConfig.md)|调用DescribeCasterConfig查询导播台配置信息。|
|[DescribeCasterLayouts](cn.zh-CN/API参考/导播服务/DescribeCasterLayouts.md)|调用DescribeCasterLayouts查询布局列表。|
|[DescribeCasters](cn.zh-CN/API参考/导播服务/DescribeCasters.md)|调用DescribeCasters查询导播台列表。|
|[DescribeCasterScenes](cn.zh-CN/API参考/导播服务/DescribeCasterScenes.md)|调用DescribeCasterScenes查询场景信息列表。|
|[DescribeCasterStreamUrl](cn.zh-CN/API参考/导播服务/DescribeCasterStreamUrl.md)|调用DescribeCasterStreamUrl查询导播台流信息列表。|
|[DescribeCasterVideoResources](cn.zh-CN/API参考/导播服务/DescribeCasterVideoResources.md)|调用DescribeCasterVideoResources查询视频源。|
|[DescribeCasterProgram](cn.zh-CN/API参考/导播服务/DescribeCasterProgram.md)|调用DescribeCasterProgram查询导播台节目单。|
|[DescribeCasterComponents](cn.zh-CN/API参考/导播服务/DescribeCasterComponents.md)|调用DescribeCasterComponents查询导播台组件列表。|
|[DescribeCasterSceneAudio](cn.zh-CN/API参考/导播服务/DescribeCasterSceneAudio.md)|调用DescribeCasterSceneAudio查询场景音频配置信息。|
|[DescribeCasterChannels](cn.zh-CN/API参考/导播服务/DescribeCasterChannels.md)|调用DescribeCasterChannels查询导播台通道信息列表。|
|[EffectCasterUrgent](cn.zh-CN/API参考/导播服务/EffectCasterUrgent.md)|调用EffectCasterUrgent将指定场景画面紧急切换至备播视频，限制仅用于PGM场景的备播切换。|
|[EffectCasterVideoResource](cn.zh-CN/API参考/导播服务/EffectCasterVideoResource.md)|调用EffectCasterVideoResource将视频资源生效至指定场景，场景引用该视频资源时有效。|
|[ModifyCasterLayout](cn.zh-CN/API参考/导播服务/ModifyCasterLayout.md)|调用ModifyCasterLayout修改布局配置，传递修改项，非修改内容无需传递。|
|[ModifyCasterComponent](cn.zh-CN/API参考/导播服务/ModifyCasterComponent.md)|调用ModifyCasterComponent修改组件。|
|[ModifyCasterVideoResource](cn.zh-CN/API参考/导播服务/ModifyCasterVideoResource.md)|调用ModifyCasterVideoResource修改视频资源。|
|[ModifyCasterEpisode](cn.zh-CN/API参考/导播服务/ModifyCasterEpisode.md)|调用ModifyCasterEpisode修改导播台节目配置,节目类型不允许修改。|
|[ModifyCasterProgram](cn.zh-CN/API参考/导播服务/ModifyCasterProgram.md)|调用ModifyCasterProgram修改导播台节目单。|
|[SetCasterConfig](cn.zh-CN/API参考/导播服务/SetCasterConfig.md)|调用SetCasterConfig配置导播台，全量覆盖配置信息，若指定参数置为空则清除导播台该项配置。|
|[SetCasterSceneConfig](cn.zh-CN/API参考/导播服务/SetCasterSceneConfig.md)|调用SetCasterSceneConfig全量设置场景配置，清空场景配置，并将布局信息设置并生效至指定场景。|
|[SetCasterChannel](cn.zh-CN/API参考/导播服务/SetCasterChannel.md)|调用SetCasterChannel在视频源同步模式时，将视频资源设置到通道中。|
|[StartCaster](cn.zh-CN/API参考/导播服务/StartCaster.md)|调用StartCaster启动导播台。若PVW、PGM场景不存在则创建，启动PVW、PGM场景，启动底层音视频处理任务。|
|[StartCasterScene](cn.zh-CN/API参考/导播服务/StartCasterScene.md)|调用StartCasterScene启动指定场景，限制仅用于PVW的打开。|
|[StopCaster](cn.zh-CN/API参考/导播服务/StopCaster.md)|调用StopCaster停止导播台，停止PVW、PGM场景，清理输出配置，停止底层音视频处理任务。|
|[StopCasterScene](cn.zh-CN/API参考/导播服务/StopCasterScene.md)|调用StopCasterScene停止指定场景，限制仅用于PVW的关闭。|
|[UpdateCasterSceneConfig](cn.zh-CN/API参考/导播服务/UpdateCasterSceneConfig.md)|调用UpdateCasterSceneConfig增量设置场景配置，不清空原配置，布局信息在原场景上增量修改，效率较全量设置高。|
|[UpdateCasterSceneAudio](cn.zh-CN/API参考/导播服务/UpdateCasterSceneAudio.md)|调用UpdateCasterSceneAudio更新场景音频配置。|

