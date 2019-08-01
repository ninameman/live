# DescribeLiveStreamBitRateData {#doc_api_live_DescribeLiveStreamBitRateData .reference}

调用DescribeLiveStreamBitRateData查询RTMP协议的直播流的设置时间范围内的一组帧率和码率，适用于获取历史数据。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamBitRateData&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamBitRateData|系统规定参数。取值：**DescribeLiveStreamBitRateData**。

 |
|DomainName|String|是|www.yourdomain.com|您的域名。

 |
|AppName|String|否|testApp|直播流所属应用名称。

 |
|EndTime|String|否|2017-12-22T08:00:00Z|结束时间。

 UTC格式，例如：2016-06-30T19:00:00Z

 |
|StartTime|String|否|2017-12-21T08:00:00Z|起始时间。

 UTC格式，例如：2016-06-29T19:00:00Z。

 |
|StreamName|String|否|testStream|直播流的名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|FrameRateAndBitRateInfos| | |各直播流的帧率、码率信息。

 |
|StreamUrl|String|rtmp://play.aliyunlive.com/AppName/StreamName|直播流的URL。

 |
|VideoFrameRate|Float|30|直播流的视频帧率。

 |
|AudioFrameRate|Float|100|直播流的音频帧率。

 |
|BitRate|Float|600|直播流的码率。

 |
|Time|String|2016-09-13T16:04:00Z|统计时刻，UTC格式。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLiveStreamBitRateData
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveStreamBitRateDataResponse>
	  <FrameRateAndBitRateInfos>
		    <FrameRateAndBitRateInfo>
			      <AudioFrameRate>167.67</AudioFrameRate>
			      <BitRate>192.02</BitRate>
			      <StreamUrl>rtmp://live.aliyunlive.com/live/test101</StreamUrl>
			      <Time> 2016 - 09 - 13 T16: 05: 00 Z</Time>
			      <VideoFrameRate>30.01</VideoFrameRate>
		    </FrameRateAndBitRateInfo>
		    <FrameRateAndBitRateInfo>
			      <AudioFrameRate>165.43</AudioFrameRate>
			      <BitRate>192</BitRate>
			      <StreamUrl>rtmp://live.aliyunlive.com/live/test102</StreamUrl>
			      <Time>2016 - 09 - 13 T16: 04: 00 Z</Time>
			      <VideoFrameRate>29.22</VideoFrameRate>
		    </FrameRateAndBitRateInfo>
		    <FrameRateAndBitRateInfo>
			      <AudioFrameRate>166.77</AudioFrameRate>
			      <BitRate>192</BitRate>
			      <StreamUrl>rtmp://live.aliyunlive.com/live/test103</StreamUrl>
			      <Time>2016 - 09 - 13 T16: 03: 00 Z</Time>
			      <VideoFrameRate>30.33</VideoFrameRate>
		    </FrameRateAndBitRateInfo>
		    <FrameRateAndBitRateInfo>
			      <AudioFrameRate>167.53</AudioFrameRate>
			      <BitRate>192</BitRate>
			      <StreamUrl>rtmp://live.aliyunlive.com/live/test104</StreamUrl>
			      <Time>2016 - 09 - 13 T16: 02: 00 Z</Time>
			      <VideoFrameRate>30</VideoFrameRate>
		    </FrameRateAndBitRateInfo>
		    <FrameRateAndBitRateInfo>
			      <AudioFrameRate>168.01</AudioFrameRate>
			      <BitRate>192</BitRate>
			      <StreamUrl>rtmp://live.aliyunlive.com/live/test104</StreamUrl>
			      <Time>2016 - 09 - 13 T16: 01: 00 Z</Time>
			      <VideoFrameRate>30</VideoFrameRate>
		    </FrameRateAndBitRateInfo>
	  </FrameRateAndBitRateInfos>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</DescribeLiveStreamBitRateDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"FrameRateAndBitRateInfos":{
		"FrameRateAndBitRateInfo":[
			{
				"AudioFrameRate":"167.67",
				"Time":" 2016 - 09 - 13 T16: 05: 00 Z",
				"StreamUrl":"rtmp://live.aliyunlive.com/live/test101",
				"BitRate":"192.02",
				"VideoFrameRate":"30.01"
			},
			{
				"AudioFrameRate":"165.43",
				"Time":"2016 - 09 - 13 T16: 04: 00 Z",
				"StreamUrl":"rtmp://live.aliyunlive.com/live/test102",
				"BitRate":"192",
				"VideoFrameRate":"29.22"
			},
			{
				"AudioFrameRate":"166.77",
				"Time":"2016 - 09 - 13 T16: 03: 00 Z",
				"StreamUrl":"rtmp://live.aliyunlive.com/live/test103",
				"BitRate":"192",
				"VideoFrameRate":"30.33"
			},
			{
				"AudioFrameRate":"167.53",
				"Time":"2016 - 09 - 13 T16: 02: 00 Z",
				"StreamUrl":"rtmp://live.aliyunlive.com/live/test104",
				"BitRate":"192",
				"VideoFrameRate":"30"
			},
			{
				"AudioFrameRate":"168.01",
				"Time":"2016 - 09 - 13 T16: 01: 00 Z",
				"StreamUrl":"rtmp://live.aliyunlive.com/live/test104",
				"BitRate":"192",
				"VideoFrameRate":"30"
			}
		]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

