# AddCasterEpisodeGroup {#doc_api_live_AddCasterEpisodeGroup .reference}

调用AddCasterEpisodeGroup添加导播台节目列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddCasterEpisodeGroup&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddCasterEpisodeGroup|系统规定参数，取值：**AddCasterEpisodeGroup**。

 |
|CallbackUrl|String|是|http://XXXXXX/XXXXXXX|用户回调地址。

 |
|ClientToken|String|是|8751ad99-2ddb-4aac-ad44-84b211021c04|用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |
|DomainName|String|是|XXXXX.XXX.XXX|域名。

 |
|RepeatNum|Integer|是|3|重复次数。其中。**0**表示不循环，**-1**表示无限循环。

 |
|SideOutputUrl|String|是|http://XXXX/XXXX|用户自定义旁路输出地址。

 |
|StartTime|String|是|2018-03-06T19:00:00Z|起始时间。

 UTC格式，例如：`2016-06-29T19:00:00Z`。

 |
|Item.N.ItemName|String|否|节目1|节目名称。

 |
|Item.N.VodUrl|String|否|http://XXXX/XXXXXX1.flv|点播文件地址。

 -   当且仅当资源为文件视频，且视频文件未导入素材库时使用。
-   支持mp4/flv/ts格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ItemIds| |\[ "21926b36-7dd2-4fde-ae25-51b5bc8e52d8", "21926b36-7dd2-4fde-ae25-51b5bc98765t" \]|节目ID列表。

 |
|ProgramId|String|16A96B9A-F203-4EC5-8E43-CB92E68XX876|节目单ID。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=AddCasterEpisodeGroup
&CallbackUrl=http://XXXXXX/XXXXXXX
&ClientToken=8751ad99-2ddb-4aac-ad44-84b211021c04
&DomainName=XXXXX.XXX.XXX
&RepeatNum=3
&SideOutputUrl=http://XXXX/XXXX
&StartTime=2018-03-06T19:00:00Z
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddCasterEpisodeGroupResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <ProgramId>16A96B9A-F203-4EC5-8E43-CB92E68XX876</ProgramId>
	  <ItemIds>21926b36-7dd2-4fde-ae25-51b5bc8e52d8</ItemIds>
	  <ItemIds>21926b36-7dd2-4fde-ae25-51b5bc98765t</ItemIds>
</AddCasterEpisodeGroupResponse>
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

