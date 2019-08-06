# ModifyCasterEpisode {#doc_api_live_ModifyCasterEpisode .reference}

调用ModifyCasterEpisode修改导播台节目配置,节目类型不允许修改。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=ModifyCasterEpisode&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyCasterEpisode|系统规定参数，取值：**ModifyCasterEpisode**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|EpisodeId|String|是|a2b8e671-2fe5-4642-a2ec-bf9386233849|节目ID。

 |
|ComponentId.N|RepeatList|否|\["16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"\]|组件列表。

 按照元素顺序由下而上排列，组件将与视频源同步切换。

 -   若类型为**Component**时，参数必选。
-   若类型为**Resource**时，表示组件与视频源绑定并同步切换。

 |
|EndTime|String|否|2016-06-29T19:20:00Z|结束时间。UTC格式 ，例如：2016-06-29T19:20:00Z。

 |
|EpisodeName|String|否|episode\_name\_1|节目名称。

 |
|ResourceId|String|否|16A96B9A-F203-4EC5-8E43-CB92E6837463|视频源ID。

 -   若节点类型为**Resource视频源**时，参数有效且必选。
-   若节点类型为**Component组件**时，参数无效。

 |
|StartTime|String|否|2016-06-29T19:00:00Z|起始时间。UTC格式，例如：2016-06-29T19:00:00Z。

 |
|SwitchType|String|否|TimeFirst|切换策略。 节点类型为Resource视频源时有效。

 -   **TimeFirst**：时间优先，直播类视频源只允许采用时间优先。
-   **ContentFirst**：内容优先。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CasterId|String|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|EpisodeId|String|a2b8e671-2fe5-4642-a2ec-bf9386233849|节目ID。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyCasterEpisode
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&EpisodeId=a2b8e671-2fe5-4642-a2ec-bf9386233849
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyCasterEpisodeResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
      <EpisodeId>a2b8e671-2fe5-4642-a2ec-bf9386233849</EpisodeId>
      <CasterId>a2b8e671-2fe5-4642-a2ec-bf93880e1a49</CasterId>
</ModifyCasterEpisodeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CasterId":"a2b8e671-2fe5-4642-a2ec-bf93880e1a49",
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"EpisodeId":"a2b8e671-2fe5-4642-a2ec-bf9386233849"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

