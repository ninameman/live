# UpdateLiveDetectNotifyConfig {#doc_api_live_UpdateLiveDetectNotifyConfig .reference}

调用UpdateLiveDetectNotifyConfig更新回调通知URL。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=UpdateLiveDetectNotifyConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateLiveDetectNotifyConfig|系统规定参数。取值：**UpdateLiveDetectNotifyConfig**。

 |
|DomainName|String|是|www.yourdomain.com|用户域名。

 |
|NotifyUrl|String|是|http://www.yourdomain.cn/examplecallback.action|发现涉黄等违规内容的回调函数。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=UpdateLiveDetectNotifyConfig
&DomainName=www.yourdomain.com
&NotifyUrl=http://www.yourdomain.cn/examplecallback.action
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateLiveDetectNotifyConfigResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</UpdateLiveDetectNotifyConfigResponse>
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
|400|InvalidNotifyUrl.Malformed|Specified NotifyUrl is invalid.|指定的notifyurl错误，请您确认该notifyurl参数是否正确。|
|400|InvalidNotifyUrl.Unsafe|Specified NotifyUrl is not safe.|指定的notifyurl错误，请您确认该notifyurl参数是否正确。|
|404|InvalidConfig.NotFound|Config does not exist.|配置错误，请您确认该配置是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

