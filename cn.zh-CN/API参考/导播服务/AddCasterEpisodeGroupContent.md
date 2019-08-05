# AddCasterEpisodeGroupContent {#doc_api_live_AddCasterEpisodeGroupContent .reference}

调用AddCasterEpisodeGroupContent添加导播台节目列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddCasterEpisodeGroupContent&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddCasterEpisodeGroupContent|系统规定参数，取值：**AddCasterEpisodeGroupContent**。

 |
|ClientToken|String|是|8751ad99-2ddb-4aac-ad44-84b211021c04|用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |
|Content|String|是|\{"CallbackUrl":"http://XXX:8000/","SideOutputUrl":"rtmp://YYY","DomainName":"ZZZ","StartTime":"2018-03-26T16:00:00Z","RepeatNum":-1,"Items":\[\{"ItemName":"节目1","VodUrl":"http://xxx-1.ts"\},\{"ItemName":"节目2","VodUrl":"http://xxx-2.ts"\}\]\}|JSON字符串型的轮播单信息。参数采用首字母大写驼峰格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ItemIds| |\["21926b36-7dd2-4fde-ae25-51b5bc8e52d8", "21926b36-7dd2-4fde-ae25-51b5bc98765t" \]|节目ID列表。

 |
|ProgramId|String|16A96B9A-F203-4EC5-8E43-CB92E68XX876|节目单ID。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=AddCasterEpisodeGroupContent
&ClientToken=8751ad99-2ddb-4aac-ad44-84b211021c04
&Content={"CallbackUrl":"http://XXX:8000/","SideOutputUrl":"rtmp://YYY","DomainName":"ZZZ","StartTime":"2018-03-26T16:00:00Z","RepeatNum":-1,"Items":[{"ItemName":"节目1","VodUrl":"http://xxx-1.ts"},{"ItemName":"节目2","VodUrl":"http://xxx-2.ts"}]}
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddCasterEpisodeGroupContentResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <ProgramId>16A96B9A-F203-4EC5-8E43-CB92E68XX876</ProgramId>
	  <ItemIds>21926b36-7dd2-4fde-ae25-51b5bc8e52d8</ItemIds>
	  <ItemIds>21926b36-7dd2-4fde-ae25-51b5bc98765t</ItemIds>
</AddCasterEpisodeGroupContentResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ProgramId":"16A96B9A-F203-4EC5-8E43-CB92E68XX876",
	"ItemIds":[
		"21926b36-7dd2-4fde-ae25-51b5bc8e52d8",
		"21926b36-7dd2-4fde-ae25-51b5bc98765t"
	],
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

