# DescribeLiveStreamsFrameRateAndBitRateData {#doc_api_live_DescribeLiveStreamsFrameRateAndBitRateData .reference}

调用DescribeLiveStreamsFrameRateAndBitRateData实时查询直播流帧率和码率数据。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamsFrameRateAndBitRateData&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamsFrameRateAndBitRateData|系统规定参数，取值：**DescribeLiveStreamsFrameRateAndBitRateData**。

 |
|AppName|String|是|testApp|直播流所属应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的域名。

 |
|EndTime|String|否|2017-12-21T09:00:00Z|结束时间。

 UTC格式。StartTime和EndTime时间间隔在7天内，且EndTime超过当前时间。

 |
|StartTime|String|否|2017-12-21T08:00:00Z|开始时间。UTC格式。

 |
|StreamName|String|否|testStream|直播流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|FrameRateAndBitRateInfos| | |各直播流的帧率/码率信息。

 |
|StreamUrl|String|rtmp://play.aliyunlive.com/AppName/StreamName|直播流的URL。

 |
|VideoFrameRate|Float|30|直播流的视频帧率。

 |
|AudioFrameRate|Float|50|直播流的音频帧率。

 |
|BitRate|Float|600|直播流的码率。

 |
|Time|String|2016-09-13T16:05:00Z|统计时刻，UTC时间。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveStreamsFrameRateAndBitRateData
&AppName=testApp
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveStreamsFrameRateAndBitRateDataResponse>
	  <FrameRateAndBitRateInfos>
		    <FrameRateAndBitRateInfo>
			      <AudioFrameRate>167.67</AudioFrameRate>
			      <BitRate>192.02</BitRate>
			      <StreamUrl>rtmp://live.aliyunlive.com/live/test101</StreamUrl>
			      <Time>2016 - 09 - 13 T16: 05: 00 Z</Time>
			      <VideoFrameRate>30.01</VideoFrameRate>
		    </FrameRateAndBitRateInfo>
	  </FrameRateAndBitRateInfos>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</DescribeLiveStreamsFrameRateAndBitRateDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"FrameRateAndBitRateInfos":{
		"FrameRateAndBitRateInfo":[
			{
				"AudioFrameRate":"167.67",
				"Time":"2016 - 09 - 13 T16: 05: 00 Z",
				"StreamUrl":"rtmp://live.aliyunlive.com/live/test101",
				"BitRate":"192.02",
				"VideoFrameRate":"30.01"
			}
		]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

