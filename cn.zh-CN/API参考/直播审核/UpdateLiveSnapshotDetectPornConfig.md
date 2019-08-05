# UpdateLiveSnapshotDetectPornConfig {#doc_api_live_UpdateLiveSnapshotDetectPornConfig .reference}

调用UpdateLiveSnapshotDetectPornConfig更新审核配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=UpdateLiveSnapshotDetectPornConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateLiveSnapshotDetectPornConfig|系统规定参数。取值：**UpdateLiveSnapshotDetectPornConfig**。

 |
|AppName|String|是|testApp|App名，支持\*表示全部。

 |
|DomainName|String|是|www.yourdomain.com|用户域名。

 |
|Interval|Integer|否|5|采样间隔。

 取值范围：**5-3600秒**。

 |
|OssBucket|String|否|test123|OSS存储bucket名称。

 |
|OssEndpoint|String|否|oss-cn-shanghai.aliyuncs.com|OSS域名。

 |
|OssObject|String|否|\{AppName\}/\{StreamName\}/\{Date\}/\{Hour\}/\{Minute\}\_\{Second\}.jpg|保存涉黄涉政等违规图片的对象模板。

 如不明确给出，默认为`{AppName}/{StreamName}/{Date}/{Hour}/{Minute}{Second}.jpg`。

 |
|Scene.N|RepeatList|否|porn|检测场景，包括：**porn（默认值） | terrorism | ad | live**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=UpdateLiveSnapshotDetectPornConfig
&AppName=testApp
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateLiveSnapshotDetectPornConfigResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</UpdateLiveSnapshotDetectPornConfigResponse>
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
|400|InvalidOssEndpoint.Malformed|Specified parameter OssEndpoint is not valid.|OSSEndpoint参数错误，请您确认该OSSEndpoint参数是否正确。|
|400|InvalidOssBucket.Malformed|Specified parameter OssBucket is not valid.|OSSBucket参数错误，请您确认该OSS BUCKET参数是否正确。|
|400|InvalidOssBucket.NotFound|The parameter OssBucket does not exist.|OSSBucket参数错误，请您确认该OSS BUCKET参数是否正确。|
|404|InvalidConfig.NotFound|Config does not exist.|配置错误，请您确认该配置是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

