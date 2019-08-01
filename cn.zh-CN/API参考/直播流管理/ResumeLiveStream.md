# ResumeLiveStream {#doc_api_live_ResumeLiveStream .reference}

调用ResumeLiveStream恢复某条流的推送。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=ResumeLiveStream&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ResumeLiveStream|系统规定参数。取值：**ResumeLiveStream**。

 |
|AppName|String|是|testApp|应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|LiveStreamType|String|是|publisher|用于指定主播推流还是客户端拉流，目前支持“publisher”（主播推送）。

 |
|StreamName|String|是|testStream|流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16BFE188-B193-4C3C-ADC5-79A7E31486EA|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=ResumeLiveStream
&AppName=testApp
&DomainName=www.yourdomain.com
&LiveStreamType=publisher
&StreamName=testStream
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ResumeLiveStreamResponse>
	  <RequestId>16BFE188-B193-4C3C-ADC5-79A7E31486EA</RequestId>
</ResumeLiveStreamResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16BFE188-B193-4C3C-ADC5-79A7E31486EA"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

