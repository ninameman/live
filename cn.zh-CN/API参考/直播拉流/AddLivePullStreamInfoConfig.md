# AddLivePullStreamInfoConfig {#doc_api_990450 .reference}

添加直播拉流信息，仅支持拉取直播流。 支持rtmp，http，flv格式。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=live&api=AddLivePullStreamInfoConfig)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddLivePullStreamInfoConfig|系统规定参数。取值：**AddLivePullStreamInfoConfig**

 |
|AppName|String|是|testApp|直播流所属应用名称。

 |
|DomainName|String|是|live.yourdomain.com|您的拉流域名为用户的播放域名。

 |
|EndTime|String|是|2017-12-22T08:00:00Z|2017-12-22T08:00:00Z

 |
|SourceUrl|String|是|live.yourdomain.com|用户的直播流所在的源站。

 多个源站可以填多个地址，用分号分隔。

 |
|StartTime|String|是|2017-12-21T08:00:00Z|拉流开始时间。

 -   UTC格式，
-   StartTime和EndTime时间间隔在7天内。

 |
|StreamName|String|是|testStream|直播流名。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CF8|该条任务请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=AddLivePullStreamInfoConfig
&AppName=testApp
&DomainName=live.yourdomain.com
&EndTime=2017-12-22T08:00:00Z
&SourceUrl=live.yourdomain.com
&StartTime=2017-12-21T08:00:00Z
&StreamName=testStream
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddLivePullStreamInfoConfigResponse>
  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CF8</RequestId>
</AddLivePullStreamInfoConfigResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CF8"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|Specified StartTime is malformed.|StartTime参数错误，请您确认该StartTime参数是否正确。|
|400|InvalidEndTime.Malformed|Specified EndTime is malformed.|结束时间错误，请您确认结束时间是否正确。|
|400|ConfigAlreadyExists|Config has already exist.|配置已添加。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)

