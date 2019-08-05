# UpdateLiveAppSnapshotConfig {#doc_api_live_UpdateLiveAppSnapshotConfig .reference}

调用UpdateLiveAppSnapshotConfig更新直播流下的截图配置。输出内容保存到OSS中，重新推流后生效。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=UpdateLiveAppSnapshotConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateLiveAppSnapshotConfig|系统规定参数。取值：**UpdateLiveAppSnapshotConfig**

 |
|AppName|String|是|test123| 

 直播流所属应用名称。

 支持**＊**号，代表该域名下所有的AppName。

 |
|DomainName|String|是|test.com|加速域名。

 |
|OssBucket|String|否|test123|OSSBucket名称。

 |
|OssEndpoint|String|否|oss-cn-shanghai.aliyuncs.com|OSSEndpoint域名。

 |
|OverwriteOssObject|String|否|\{AppName\}/\{StreamName\}.jpg|OSS存储文件名，每次截图都覆盖此文件。

 -   小于256bytes。
-   目前仅支持生成jpg图片。
-   支持变量匹配，包含 \{AppName\}、\{StreamName\}。例如：`{AppName}/{StreamName}.jpg`。
-   传入**-**，表示删除此字段。

 |
|SequenceOssObject|String|否|snapshot/\{AppName\}/\{StreamName\}/\{UnixTimestamp\}.jpg|OSS存储文件名。每次截图都递增存储，**DescribeLiveStreamSnapshotInfo**接口查询一段时间的文件。

 -   小于256bytes。
-   目前仅支持生成jpg图片。
-   支持变量匹配，包含 \{AppName\}、\{StreamName\}、\{UnixTimestamp\}、\{Sequence\}，其中 \{UnixTimestamp\}、\{Sequence\} 必填一个。例如：`snapshot/{AppName}/{StreamName}/{UnixTimestamp}.jpg`。
-   传入**-**，表示删除此字段。

 |
|TimeInterval|Integer|否|5|截图周期，单位：秒。

 取值范围：**5~3600**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=UpdateLiveAppSnapshotConfig
&AppName=test123
&DomainName=test.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateLiveAppSnapshotConfigResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</UpdateLiveAppSnapshotConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidOverwriteOssObjectOrSequenceOssObject.Malformed|Specified paramters OverwriteOssObject or SequenceOssObject should have one.|OverwriteOssObject与SequenceOssObject参数任选其一。|
|400|InvalidOssEndpoint.Malformed|Specified parameter OssEndpoint is not valid.|OSSEndpoint参数错误，请您确认该OSSEndpoint参数是否正确。|
|400|InvalidOssBucket.Malformed|Specified parameter OssBucket is not valid.|OSSBucket参数错误，请您确认该OSS BUCKET参数是否正确。|
|400|InvalidOssBucket.NotFound|The parameter OssBucket does not exist.|OSSBucket参数错误，请您确认该OSS BUCKET参数是否正确。|
|400|InvalidOverwriteOssObject.Malformed|Specified parameter OverwriteOssObject is not valid.|OverwriteOSSObject参数错误，请您确认该OverwriteOSSObject参数是否正确。|
|400|InvalidSequenceOssObject.Malformed|Specified parameter SequenceOssObject is not valid.|SequenceOssObject参数错误，请您确认该SequenceOssObject参数是否正确。|
|400|InvalidConfig.NotFound|The speicified config does not exist.|OssBucket错误，请您确认该OssBucket是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

