# DescribeCasterChannels {#doc_api_live_DescribeCasterChannels .reference}

调用DescribeCasterChannels查询导播台通道信息列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeCasterChannels&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCasterChannels|系统规定参数，取值：**DescribeCasterChannels**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|RegionId|String|否|cn-shanghai|地域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Channels| | |通道列表。

 |
|ChannelId|String|RV01|通道位置ID。

 布局应用通道ID，每个位置至多设置一个视频源，格式需符合“RV01...RV12”。

 |
|ResourceId|String|87642866-281E-4AEA-9582-B1248798765|视频源Id。

 |
|RtmpUrl|String|rtmp://XXX/caster/YYY|rtmp地址。

 |
|StreamUrl|String|http://XXX/caster/YYY.flv|通道输出地址。

 |
|RequestId|String|83C52866-281E-4AEA-9582-B1245406349D|请求ID。

 |
|Total|Integer|1|总数量。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeCasterChannels
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCasterChannelsResponse>
	  <RequestId>3be7ade8-d907-483c-b24a-0dad4595beaf</RequestId>
	  <Channels>
		    <ChannelId>RV01</ChannelId>
		    <ResourceId>3be7ade8-d907-483c-b24a-0da827389387</ResourceId>
		    <StreamUrl>http://XXXXXX/XXXXXX/XXXXXXX.flv</StreamUrl>
	  </Channels>
</DescribeCasterChannelsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Channels":[
		{
			"ChannelId":"RV01",
			"ResourceId":"3be7ade8-d907-483c-b24a-0da827389387",
			"StreamUrl":"http://XXXXXX/XXXXXX/XXXXXXX.flv"
		}
	],
	"RequestId":"3be7ade8-d907-483c-b24a-0dad4595beaf"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

