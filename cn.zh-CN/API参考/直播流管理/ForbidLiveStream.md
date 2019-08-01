# ForbidLiveStream {#doc_api_1003557 .reference}

禁止某条流的推送，可以预设某个时刻将流恢复。

**说明：** 禁止直播流的上限为10,000路，超出限制将禁用失败，请您注意统计当前禁用流的数量。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=live&api=ForbidLiveStream)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ForbidLiveStream|系统规定参数。取值：**ForbidLiveStream**

 |
|AppName|String|是|testApp|应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|LiveStreamType|String|是|publisher|用于指定主播推流还是客户端拉流，目前支持 “publisher”\(主播推送\)。

 |
|StreamName|String|是|testStream|流名称。

 |
|ResumeTime|String|否|2015-12-01T17:37:00Z|恢复流的时间。

 UTC 时间，格式：2015-12-01T17:37:00Z。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16BFE188-B193-4C3C-ADC5-79A7E31486EA|该条任务请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ForbidLiveStream
&AppName=testApp
&DomainName=www.yourdomain.com
&LiveStreamType=publisher
&StreamName=testStream
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ForbidLiveStreamResponse>
  <RequestId>16BFE188-B193-4C3C-ADC5-79A7E31486EA</RequestId>
</ForbidLiveStreamResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16BFE188-B193-4C3C-ADC5-79A7E31486EA"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidResumeTime.Malformed|Specified parameter ResumeTime is not valid.|ResumeTime参数错误，请您确认该ResumeTime参数是否正确。|
|400|ConfigAlreadyExists|Config has already exist.|配置已添加。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

