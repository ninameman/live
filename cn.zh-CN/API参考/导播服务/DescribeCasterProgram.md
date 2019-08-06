# DescribeCasterProgram {#doc_api_live_DescribeCasterProgram .reference}

调用DescribeCasterProgram查询导播台节目单。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeCasterProgram&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCasterProgram|系统规定参数，取值：**DescribeCasterProgram**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|EndTime|String|否|2016-06-29T20:00:00|查询范围。 返回指定结束时间前开启的节目。

 |
|EpisodeId|String|否|1872639A-F203-4EC5-8E43-CB92E68F8732|节目ID。

 |
|EpisodeType|String|否|Resource|节点类型。取值：

 -   **Resource**：视频源
-   **Component**：组件

 |
|PageNum|Integer|否|5|页码。

 |
|PageSize|Integer|否|10|每页节目数量。

 |
|StartTime|String|否|2016-06-29T19:00:00|查询范围。 返回指定开始时间后开启的节目。

 |
|Status|Integer|否|0|节目状态。 取值：

 -   **0**：未播放
-   **1**：播放中
-   **2**：播放完毕

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CasterId|String|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|Episodes| | |节点列表。

 |
|ComponentIds| |\["1872639A-F203-4EC5-8E43-CB9292827362" \]|组件列表。

 |
|EndTime|String|"2016-06-29T19:02:00Z"|结束时间。UTC格式，例如：`2016-06-29T19:00:00Z`。

 |
|EpisodeId|String|1872639A-F203-4EC5-8E43-CB92E68F8732|节目ID。

 |
|EpisodeName|String|program\_name\_1|节目名称。

 |
|EpisodeType|String|Resource|节点类型。

 |
|ResourceId|String|1872639A-F203-4EC5-8E43-CB92E8374827|视频源ID。

 |
|StartTime|String|2016-06-29T19:00:00Z|起始时间。UTC格式，例如：`2016-06-29T19:00:00Z`。

 |
|Status|Integer|0|节目状态。

 |
|SwitchType|String|TimeFirst|切换策略。取值：

 -   **TimeFirst**：时间优先，直播节目只允许采用时间优先。
-   **ContentFirst**：内容优先。

 |
|ProgramEffect|Integer|1|启用标志。

 -   **0**：不启用
-   **1**：启用

 |
|ProgramName|String|programs\_name|节目单名称。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|Total|Integer|1|总记录数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com?Action=DescribeCasterProgram
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCasterProgramResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <ProgramId>1872639A-F203-4EC5-8E43-CB92E68F8378</ProgramId>
	  <ProgramName>programs_name</ProgramName>
      <ProgramEffect>1</ProgramEffect>
	  <Episodes>
		    <EpisodeId>1872639A-F203-4EC5-8E43-CB92E68F8732</EpisodeId>
		    <EpisodeType>Resource</EpisodeType>
		    <EpisodeName>program_name_1</EpisodeName>
		    <ResourceId>1872639A-F203-4EC5-8E43-CB92E8374827</ResourceId>
		    <ComponentIds>1872639A-F203-4EC5-8E43-CB9292827362</ComponentIds>
		    <StartTime>2016-06-29T19:00:00Z</StartTime>
		    <EndTime>2016-06-29T19:02:00Z</EndTime>
		    <Duration>120</Duration>
		    <SwitchType>TimeFirst</SwitchType>
	  </Episodes>
	  <Episodes>
		    <EpisodeId>1872639A-F203-4EC5-8E43-CB92E6873726</EpisodeId>
		    <EpisodeType>Component</EpisodeType>
		    <ComponentIds>1872639A-F203-4EC5-8E43-CB6253647382</ComponentIds>
		    <StartTime>2016-06-29T19:02:00Z</StartTime>
		    <EndTime>2016-06-29T19:04:00Z</EndTime>
	  </Episodes>
</DescribeCasterProgramResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ProgramName":"programs_name",
	"ProgramId":"1872639A-F203-4EC5-8E43-CB92E68F8378",
	"ProgramEffect":1,
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"Episodes":[
		{
			"SwitchType":"TimeFirst",
			"EpisodeType":"Resource",
			"ComponentIds":[
				"1872639A-F203-4EC5-8E43-CB9292827362"
			],
			"ResourceId":"1872639A-F203-4EC5-8E43-CB92E8374827",
			"Duration":120,
			"EpisodeName":"program_name_1",
			"EpisodeId":"1872639A-F203-4EC5-8E43-CB92E68F8732",
			"EndTime":"2016-06-29T19:02:00Z",
			"StartTime":"2016-06-29T19:00:00Z"
		},
		{
			"EpisodeType":"Component",
			"ComponentIds":[
				"1872639A-F203-4EC5-8E43-CB6253647382"
			],
			"EpisodeId":"1872639A-F203-4EC5-8E43-CB92E6873726",
			"EndTime":"2016-06-29T19:04:00Z",
			"StartTime":"2016-06-29T19:02:00Z"
		}
	]
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

