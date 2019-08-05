# DescribeLiveStreamRecordIndexFile {#doc_api_live_DescribeLiveStreamRecordIndexFile .reference}

调用DescribeLiveStreamRecordIndexFile查询单个录制索引文件。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamRecordIndexFile&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamRecordIndexFile|系统规定参数。取值：**DescribeLiveStreamRecordIndexFile**。

 |
|AppName|String|是|testApp|直播流所属应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|RecordId|String|是|xxx|索引文件ID。

 |
|StreamName|String|是|testStream|直播流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RecordIndexInfo| | |录制配置。

 |
|RecordUrl|String|http://xxx.xxx/atestObject.m3u8|索引文件地址。

 |
|DomainName|String|test.com|流所属加速域名。

 |
|AppName|String|xxx|流所属应用名称。

 |
|StreamName|String|xxx|直播流名称。

 |
|OssBucket|String|tes123|OSS存储的bucket名称。

 |
|OssEndpoint|String|oss-cn-hangzhou.aliyuncs.com|OSS存储的endpoint名称。

 |
|OssObject|String|test123|OSS存储的录制文件名。

 |
|StartTime|String|2015-12-01T17:36:00Z|开始时间，格式：2015-12-01T17:36:00Z。

 |
|EndTime|String|2016-05-25T05:47:11Z|结束时间，格式：2015-12-01T17:36:00Z。

 |
|Duration|Float|588.849|录制时长。

 |
|Height|Integer|480|视频高。

 |
|Width|Integer|640|视频宽。

 |
|CreateTime|String|2016-05-27T09:40:56Z|创建时间。

 |
|RecordId|String|c4d7f0a4-b506-43f9-8de3-07732c3f3d82|索引文件ID。

 |
|RequestId|String|5EBF2AC3-4B73-40A5-8B32-83F49D5F035E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[live.aliyuncs.com]/?Action=DescribeLiveStreamRecordIndexFile
&AppName=testApp
&DomainName=www.yourdomain.com
&RecordId=xxx
&StreamName=testStream
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveStreamRecordIndexFileResponse>
	  <RecordIndexInfo>
		    <AppName>xxx</AppName>
		    <CreateTime>2016-05-27T09:40:56Z</CreateTime>
		    <DomainName>xxx</DomainName>
		    <Duration>588.849</Duration>
		    <EndTime>2016-05-25T05:47:11Z</EndTime>
		    <Height>480</Height>
		    <OssBucket>bucket</OssBucket>
		    <OssEndpoint>oss-cn-hangzhou.aliyuncs.com</OssEndpoint>
		    <OssObject>atestObject.m3u8</OssObject>
		    <RecordId>c4d7f0a4-b506-43f9-8de3-07732c3f3d82</RecordId>
		    <RecordUrl>http://xxx.xxx/atestObject.m3u8</RecordUrl>
		    <StartTime>2016-05-25T05:37:11Z</StartTime>
		    <StreamName>xxx</StreamName>
		    <Width>640</Width>
	  </RecordIndexInfo>
	  <RequestId>5EBF2AC3-4B73-40A5-8B32-83F49D5F035E</RequestId>
</DescribeLiveStreamRecordIndexFileResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"5EBF2AC3-4B73-40A5-8B32-83F49D5F035E",
	"RecordIndexInfo":{
		"OssObject":"atestObject.m3u8",
		"RecordId":"c4d7f0a4-b506-43f9-8de3-07732c3f3d82",
		"StreamName":"xxx",
		"Height":480,
		"OssBucket":"bucket",
		"CreateTime":"2016-05-27T09:40:56Z",
		"Duration":588.849,
		"DomainName":"xxx",
		"AppName":"xxx",
		"EndTime":"2016-05-25T05:47:11Z",
		"OssEndpoint":"oss-cn-hangzhou.aliyuncs.com",
		"Width":640,
		"StartTime":"2016-05-25T05:37:11Z",
		"RecordUrl":"http://xxx.xxx/atestObject.m3u8"
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

