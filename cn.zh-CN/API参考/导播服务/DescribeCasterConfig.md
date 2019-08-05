# DescribeCasterConfig {#doc_api_live_DescribeCasterConfig .reference}

调用DescribeCasterConfig查询导播台配置信息。

查询导播台配置信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeCasterConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCasterConfig|系统规定参数，取值：**DescribeCasterConfig**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|RegionId|String|否|cn-shanghai|地域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CallbackUrl|String|http://XXX/YYY|用户回调地址。

 |
|CasterId|String|b4810848-bcf9-4aef-bd4a-e6bba2d966c8|导播台ID。

 |
|CasterName|String|coco-caster10|导播台名称。

 |
|ChannelEnable|Integer|1|是否启用Channel。 取值：

 -   **0**：不启用
-   **1**：启用

 |
|Delay|Float|0|延时播放，单位：秒 。

 -   **0**：禁用延时
-   **大于0**：启用延时

 |
|DomainName|String|XXX|域名。

 |
|ProgramEffect|Integer|0|轮播生效标志。 取值：

 -   **0**：不生效
-   **1**：生效

 |
|ProgramName|String|program\_name|轮播台名称。

 |
|RecordConfig| | |录制配置参数为空时，表示不启用录制功能。

 |
|OssBucket|String|ossbucket|存储位置。

 |
|OssEndpoint|String|endpoint|存储位置所在OSS节点。

 |
|RecordFormat| | |录制格式配置。

 |
|CycleDuration|Integer|3600|录制时长。

 |
|Format|String|m3u8|录制格式。

 |
|OssObjectPrefix|String|record/\{AppName\}/\{StreamName\}|录制文件名。

 |
|SliceOssObjectPrefix|String|record/\{AppName\}/\{StreamName\}/\{UnixTimestamp\}|切片名称。

 |
|RequestId|String|97df6b7f-3490-47d2-ac50-8833e1b64597|请求ID。

 |
|SideOutputUrl|String|rtmp://XXX/YYY/ZZZ|用户自定义导播台旁路输出地址。

 |
|TranscodeConfig| | |转码配置。

 |
|CasterTemplate|String|lp\_hd|导播台转码模板。取值：

 -   **lp\_ld**：流畅
-   **lp\_sd**：标清
-   **lp\_hd**：高清
-   **lp\_ud**：超清
-   **lp\_ld\_v**：竖屏流畅
-   **lp\_sd\_v**：竖屏标清
-   **lp\_hd\_v**：竖屏高清
-   **lp\_ud\_v**：竖屏超清

 |
|LiveTemplateIds| |lld|直播转码配置。取值：

 -   **lsd**：标清
-   **lld**：流畅
-   **lud**：超清
-   **lhd**：高清自适应转码模板
-   **daobo-lsd**：标清
-   **daobo-lld**：流畅
-   **daobo-lud**：超清
-   **daobo-lhd**：高清

 |
|UrgentMaterialId|String|98646538-bcf9-4aef-bd4a-e6bb765887878|备播视频，媒资库素材ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeCasterConfig
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCasterConfigResponse>
	  <RequestId>97df6b7f-3490-47d2-ac50-8833e1b64597</RequestId>
	  <CasterName>coco-caster10</CasterName>
	  <DomainName>XXXXXX</DomainName>
	  <TranscodeConfig>
		    <CasterTemplate>lp_hd</CasterTemplate>
		    <LiveTemplate>lld</LiveTemplate>
	  </TranscodeConfig>
	  <Delay>0</Delay>
	  <RecordConfig>
		    <Endpoint>XXXXXX</Endpoint>
		    <OssBucket>XXXXXX</OssBucket>
		    <VideoFormat>
			      <Format>flv</Format>
			      <Prefix>record/{AppName}/{StreamName}</Prefix>
			      <SlicePrefix>record/{AppName}/{StreamName}/{UnixTimestamp}</SlicePrefix>
			      <Interval>3600</Interval>
		    </VideoFormat>
		    <VideoFormat>
			      <Format>m3u8</Format>
			      <Prefix>record/{AppName}/{StreamName}</Prefix>
			      <SlicePrefix>record/{AppName}/{StreamName}/{UnixTimestamp}</SlicePrefix>
			      <Interval>3600</Interval>
		    </VideoFormat>
	  </RecordConfig>
</DescribeCasterConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TranscodeConfig":{
		"CasterTemplate":"lp_hd",
		"LiveTemplate":[
			"lld"
		]
	},
	"CasterName":"coco-caster10",
	"Delay":0,
	"RequestId":"97df6b7f-3490-47d2-ac50-8833e1b64597",
	"RecordConfig":{
		"VideoFormat":[
			{
				"Format":"flv",
				"Interval":3600,
				"SlicePrefix":"record/{AppName}/{StreamName}/{UnixTimestamp}",
				"Prefix":"record/{AppName}/{StreamName}"
			},
			{
				"Format":"m3u8",
				"Interval":3600,
				"SlicePrefix":"record/{AppName}/{StreamName}/{UnixTimestamp}",
				"Prefix":"record/{AppName}/{StreamName}"
			}
		],
		"OssBucket":"XXXXXX",
		"Endpoint":"XXXXXX"
	},
	"DomainName":"XXXXXX"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

