# CreateLiveStreamRecordIndexFiles {#doc_api_live_CreateLiveStreamRecordIndexFiles .reference}

调用CreateLiveStreamRecordIndexFiles创建录制索引文件。

该API用于创建某个时间范围的M3U8索引文件，需要注意以下几点：

-   创建录制索引必保证直播流发生过推流行为，如果设置的时间内未发生过直播或流名错误等会导致创建录制索引失败。
-   接口中的开始时间和结束时间需要按格式填写UTC时间，请注意与本地时区的时间差。
-   TS分片信息在视频直播系统中只保存3个月，创建m3u8文件只能选择最近3个月的录制内容。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=CreateLiveStreamRecordIndexFiles&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateLiveStreamRecordIndexFiles|系统规定参数。取值：**CreateLiveStreamRecordIndexFiles**。

 |
|AppName|String|是|testApp|直播流所属应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|EndTime|String|是|2017-12-22T08:00:00Z|结束时间。与StartTime间隔时间不能超过4天。

 格式：UTC时间。

 示例：2015-12-01T17:36:00Z。

 |
|OssBucket|String|是|test123|OSS存储bucket名称。

 |
|OssEndpoint|String|是|oss-cn-shanghai.aliyuncs.com|OSS endpoint。

 |
|OssObject|String|是|\{AppName\}/\{StreamName\}/\{Date\}/\{Hour\}/\{Minute\}\_\{Second\}.m3u8|OSS存储的录制文件名。

 |
|StartTime|String|是|2017-12-21T08:00:00Z|开始时间。

 格式：UTC时间。

 示例：2015-12-01T17:36:00Z。

 |
|StreamName|String|是|testStream|直播流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RecordInfo| | |录制配置。

 |
|RecordUrl|String|http://xxx.xxx/atestObject.m3u8|索引文件地址。

 |
|DomainName|String|test.com|流所属加速域名。

 |
|AppName|String|test123|流所属应用名称。

 |
|StreamName|String|test123|直播流名称。

 |
|StartTime|String|2015-12-01T17:36:00Z|开始时间。

 格式：2015-12-01T17:36:00Z。

 |
|EndTime|String|2015-12-01T17:36:00Z|结束时间。

 格式：2015-12-01T17:36:00Z。

 |
|Duration|Float|20|录制时长，单位：秒。

 |
|Height|Integer|480|视频高。

 |
|Width|Integer|640|视频宽。

 |
|CreateTime|String|2016-05-27T09:40:56Z|创建时间。

 |
|OssBucket|String|bucket|OssBucket名称。

 |
|OssEndpoint|String|oss-cn-hangzhou.aliyuncs.com|OssEndpoint域名。

 |
|OssObject|String|atestObject.m3u8|OssObject名称。

 |
|RecordId|String|c4d7f0a4-b506-43f9-8de3-07732c3f3d82|索引文件ID。

 |
|RequestId|String|550439A3-F8EC-4CA2-BB62-B9DB43EEEF30|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[live.aliyuncs.com]/?Action=CreateLiveStreamRecordIndexFiles
&AppName=testApp
&DomainName=www.yourdomain.com
&EndTime=2017-12-22T08:00:00Z
&OssBucket=test123
&OssEndpoint= oss-cn-shanghai.aliyuncs.com
&OssObject={AppName}/{StreamName}/{Date}/{Hour}/{Minute}_{Second}.m3u8
&StartTime=2017-12-21T08:00:00Z
&StreamName=testStream
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateLiveStreamRecordIndexFilesResponse>
	  <RecordInfo>
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
	  </RecordInfo>
	  <RequestId>550439A3-F8EC-4CA2-BB62-B9DB43EEEF30</RequestId>
</CreateLiveStreamRecordIndexFilesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"550439A3-F8EC-4CA2-BB62-B9DB43EEEF30",
	"RecordInfo":{
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

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|Specified StartTime is malformed.|StartTime参数错误，请您确认该StartTime参数是否正确。|
|400|InvalidEndTime.Malformed|Specified EndTime is malformed.|结束时间错误，请您确认结束时间是否正确。|
|400|InvalidEndTime.Mismatch|Specified end time does not math the specified start time.|结束时间与开始时间不匹配，请您确认时间的匹配度。|
|400|InvalidOssBucket.Malformed|Specified OssBucket is malformed.|OSSBucket参数错误，请您确认该OSS BUCKET参数是否正确。|
|400|InvalidOssObject.Malformed|Specified OssObject is malformed.|OSSObject参数错误，请您确认该OSSObject参数是否正确。|
|400|InvalidStream.NotFound|Speicified stream does not exist.|直播流不存在，请您确认直播流是否正确。|
|400|InvalidConfig.Changed|The oss bucket info between StartTime and EndTime has changed.|ossbuckt开始结束时间已经改变。|
|400|NoRecordContent|The record content between StartTime and EndTime is empty.|开始时间和结束时间为空。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

