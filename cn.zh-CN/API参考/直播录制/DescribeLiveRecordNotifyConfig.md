# DescribeLiveRecordNotifyConfig {#doc_api_live_DescribeLiveRecordNotifyConfig .reference}

调用DescribeLiveRecordNotifyConfig查询域名级别录制回调配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveRecordNotifyConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveRecordNotifyConfig|系统规定参数。取值：**DescribeLiveRecordNotifyConfig**。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|5056369B-D337-499E-B8B7-B761BD37B08A|请求ID。

 |
|LiveRecordNotifyConfig| | |域名录制回调配置。

 |
|DomainName|String|test.com|流所属加速域名。

 |
|NotifyUrl|String|http://www.yourdomain.cn/examplecallback.action|录制回调地址。

 |
|NeedStatusNotify|Boolean|false|是否需要录制任务状态回调。

 |
|OnDemandUrl|String|http://www.yourdomain.cn/ondemandcallback.action|按需录制回调url地址。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com/?Action=DescribeLiveRecordNotifyConfig
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveRecordNotifyConfigResponse>
	  <LiveRecordNotifyConfig>
		    <DomainName>xxxx</DomainName>
		    <NeedStatusNotify>false</NeedStatusNotify>
		    <NotifyUrl>http://xxx</NotifyUrl>
	  </LiveRecordNotifyConfig>
	  <RequestId>5056369B-D337-499E-B8B7-B761BD37B08A</RequestId>	
</DescribeLiveRecordNotifyConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"5056369B-D337-499E-B8B7-B761BD37B08A",
	"LiveRecordNotifyConfig":{
		"NeedStatusNotify":false,
		"NotifyUrl":"http://xxx",
		"DomainName":"xxxx"
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|InvalidConfig.NotFound|Config does not exist.|配置错误，请您确认该配置是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

