# AddCasterEpisode {#doc_api_live_AddCasterEpisode .reference}

调用AddCasterEpisode添加导播台节目。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddCasterEpisode&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddCasterEpisode|系统规定参数，取值：**AddCasterEpisode**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|EndTime|String|是|2016-06-29T19:10:00Z|结束时间。

 UTC 格式，例如：`2016-06-29T19:10:00Z`。

 |
|EpisodeType|String|是|Resource|节点类型。 取值：

 -   **Resource**：视频源
-   **Component**：组件

 |
|StartTime|String|是|2016-06-29T19:00:00Z|起始时间。

 UTC格式，例如：`2016-06-29T19:00:00Z` 。

 |
|SwitchType|String|是|TimeFirst|切换策略。取值：

 -   **TimeFirst**：时间优先
-   **ContentFirst**：内容优先

 **说明：** 直播类视频源只允许采用时间优先，当节点类型为Resource时有效。

 |
|ComponentId.N|RepeatList|否|\["a2b8e671-2fe5-4642-a2ec-bf93880e1a41"\]|组件列表。按照元素顺序由下而上排列，组件将与视频源同步切换。

 若类型为**Component**时，参数必选。

 若类型为**Resource**时，参数非必选，输入时表示组件与视频源绑定并同步切换。

 |
|EpisodeName|String|否|episode\_1|节目名称。

 |
|ResourceId|String|否|a2b8e671-2fe5-4642-a2ec-bf93880e1a41|视频源ID。

 **说明：** 

-   若节点类型为**Resource**时，参数有效且必选，
-   若节点类型为**Component**时，参数无效。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|EpisodeId|String|21926b36-7dd2-4fde-ae25-51b5bc8e52d8|节目ID。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=AddCasterEpisode
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&EndTime=2016-06-29T19:10:00Z
&EpisodeType=Resource
&StartTime=2016-06-29T19:00:00Z
&SwitchType=TimeFirst
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddCasterComponentResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <EpisodeId>21926b36-7dd2-4fde-ae25-51b5bc8e52d8</EpisodeId>
</AddCasterComponentResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"EpisodeId":"21926b36-7dd2-4fde-ae25-51b5bc8e52d8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

