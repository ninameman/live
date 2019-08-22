# SetLiveStreamsNotifyUrlConfig {#doc_api_live_SetLiveStreamsNotifyUrlConfig .reference}

调用SetLiveStreamsNotifyUrlConfig设置推流回调配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=SetLiveStreamsNotifyUrlConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLiveStreamsNotifyUrlConfig|系统规定参数。取值：**SetLiveStreamsNotifyUrlConfig**。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|NotifyUrl|String|是|rtmp://play.aliyunlive.com/notify|设置直播流信息推送到的URL地址。

 **说明：** 必须以`http://`开头。

 |
|RegionId|String|否|cn-hangzhou|地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?DomainName=www.yourdomain.com
&NotifyUrl=rtmp://play.aliyunlive.com/notify
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetLiveStreamsNotifyUrlConfigResponse>
	  <RequestId>4C747C97-7ECD-4C61-8A92-67AD806331FF</RequestId>
</SetLiveStreamsNotifyUrlConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"4C747C97-7ECD-4C61-8A92-67AD806331FF"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

