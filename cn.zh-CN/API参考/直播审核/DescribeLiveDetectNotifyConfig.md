# DescribeLiveDetectNotifyConfig {#doc_api_live_DescribeLiveDetectNotifyConfig .reference}

调用DescribeLiveDetectNotifyConfig查询回调通知URL。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDetectNotifyConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDetectNotifyConfig|系统规定参数。取值：**DescribeLiveDetectNotifyConfig**

 |
|DomainName|String|是|www.yourdomain.com|用户域名。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|LiveDetectNotifyConfig| | |回调配置，只在正确返回时有。

 |
|DomainName|String|live.aliyunlive.com|用户域名。

 |
|NotifyUrl|String|http://callback.com|通知回调。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveDetectNotifyConfig
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveDetectNotifyConfigResponse>
	  <LiveDetectNotifyConfig>
		    <DomainName>live.aliyunlive.com</DomainName>
		    <NotifyUrl>http://callback.com</NotifyUrl>
	  </LiveDetectNotifyConfig>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</DescribeLiveDetectNotifyConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"LiveDetectNotifyConfig":{
		"NotifyUrl":"http://callback.com",
		"DomainName":"live.aliyunlive.com"
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidConfig.NotFound|Config does not exist.|配置错误，请您确认该配置是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

