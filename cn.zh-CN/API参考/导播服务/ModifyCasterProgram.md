# ModifyCasterProgram {#doc_api_live_ModifyCasterProgram .reference}

调用ModifyCasterProgram修改导播台节目单。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=ModifyCasterProgram&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyCasterProgram|系统规定参数，取值：**ModifyCasterProgram**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|Episode.N.ComponentId.N|RepeatList|否|\["a2b8e671-2fe5-4642-a2ec-bf938887653" \]|组件列表。按照元素顺序由下而上排列，组件将与视频源同步切换

 -   若类型为**Component**时，参数必选。
-   若类型为**Resource**时，表示组件与视频源绑定并同步切换。

 |
|Episode.N.EndTime|String|否|2016-06-29T19:04:00Z|结束时间。UTC格式，例如：2016-06-29T19:00:02Z。

 |
|Episode.N.EpisodeId|String|否|a2b8e671-2fe5-4642-a2ec-bf9388876473|节目ID。

 |
|Episode.N.EpisodeName|String|否|program\_name\_2|节目名称。

 |
|Episode.N.EpisodeType|String|否|Resource|节点类型。

 |
|Episode.N.ResourceId|String|否|a2b8e671-2fe5-4642-a2ec-bf9388876473|视频源ID。

 |
|Episode.N.StartTime|String|否|2016-06-29T19:02:00Z|起始时间。UTC格式 ，例如：2016-06-29T19:00:00Z。

 |
|Episode.N.SwitchType|String|否|TimeFirst|切换策略。 节点类型为Resource视频源时有效。

 -   **TimeFirst**：时间优先，直播类视频源只允许采用时间优先。
-   **ContentFirst**：内容优先。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CasterId|String|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com?Action=ModifyCasterProgram
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyCasterProgramResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
      <CasterId>a2b8e671-2fe5-4642-a2ec-bf93880e1a49</CasterId>
</ModifyCasterProgramResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CasterId":"a2b8e671-2fe5-4642-a2ec-bf93880e1a49",
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

