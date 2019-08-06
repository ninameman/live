# DescribeCasterLayouts {#doc_api_live_DescribeCasterLayouts .reference}

调用DescribeCasterLayouts查询布局列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeCasterLayouts&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCasterLayouts|系统规定参数，取值：**DescribeCasterLayouts**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|LayoutId|String|否|72d2ec7a-4cd7-4a01-974b-7cd53947f053|布局ID。

 若未指定，则查询导播台下所有布局列表。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|3be7ade8-d907-483c-b24a-0dad4595beaf|请求ID。

 |
|Layouts| | |布局列表。

 |
|LayoutId|String|72d2ec7a-4cd7-4a01-974b-7cd53947f053|布局ID。

 |
|VideoLayers| | |Videolayer配置列表，采用数组默认序列。

 |
|HeightNormalized|Float|0.5|设置该layer元素的高度归一化比例值。

 -   若采用不填充模式，元素的宽度会按照该高度来进行等比缩放。**默认值为0**，表示按照画面的原始尺寸进行显示。
-   若采用自适应方式，该字段必选且**大于0**，表示填充区\(框\)高度归一化比例值。

 |
|WidthNormalized|Float|0.5|设置该layer元素的宽度归一化比例值。

 -   若采用不填充模式，元素的高度会按照该宽度来进行等比缩放。**默认值为0**，表示按照画面的原始尺寸进行显示。
-   若采用自适应方式，该字段必选且**大于0**，表示填充区\(框\)宽度归一化比例值。

 |
|PositionNormalizeds| |0,0.3|设置该layer元素的位置归一化值`[x,y]`, 默认为`[0,0]`。注意x,y需要进行归一化计算。

 |
|PositionRefer|String|topLeft|设置元素的position参考坐标值。取值范围：

 取值范围：**topLeft（默认值）**| **topRight** | **bottomLeft** | **bottomRight** | **center** | **topCenter** | **bottomCenter** | **leftCenter** | **rightCenter**。

 |
|FillMode|String|fit|元素填充方式。取值：

 -   **none（默认）**：不填充。以画面作为配置目标进行Layer设置。
-   **fit**：自适应。以填充区（框）作为配置目标进行Layer设置，此时画面会按照原始的宽高比缩放，长边对齐的自适应方式在填充区（框）内居中填充，若填充区宽高比和画面不一致，则短边两侧无填充（显示为下层Layer画面，若下层未配置Layer，默认为底图黑色）。

 |
|FixedDelayDuration|Integer|20|该字段对视频进行固定延迟设置，可用于字幕同步。

 -   单位：**ms**
-   默认值：**0**
-   取值范围：**0~5000**

 |
|AudioLayers| | |Audiolayer配置列表。

 |
|VolumeRate|Float|1|设置该layer元素的高度归一化比例值，其中元素的宽度会按照该高度来进行等比缩放。 **默认值为0**，其表示按照元素的原始尺寸进行显示。

 |
|ValidChannel|String|all|确定哪些声道可以作为音量输入。

 取值范围：**leftChannel** | **rightChannel** | **all（默认值）**

 |
|FixedDelayDuration|Integer|20|该字段对视频进行固定延迟设置，可用于字幕同步。

 -   单位：**ms**
-   默认值：**0**
-   取值范围：**0~5000**

 |
|BlendList| |"RV01", "RV02"|位置关联列表，与VideoLayers顺序保持一致。

 |
|MixList| |RV01|位置关联列表，与AudioLayers顺序保持一致。

 |
|Total|Integer|3|总记录数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeCasterLayouts
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCasterLayoutsResponse>
	  <RequestId>3be7ade8-d907-483c-b24a-0dad4595beaf</RequestId>
	  <Layouts>
		    <MixList>RV01</MixList>
		    <AudioLayers>
			      <ValidChannel>all</ValidChannel>
			      <VolumeRate>1</VolumeRate>
		    </AudioLayers>
		    <VideoLayers>
			      <HeightNormalized>0.5</HeightNormalized>
			      <PositionRefer>topLeft</PositionRefer>
			      <WidthNormalized>0.5</WidthNormalized>
			      <PositionNormalized>0</PositionNormalized>
			      <PositionNormalized>0.3</PositionNormalized>
		    </VideoLayers>
		    <VideoLayers>
			      <HeightNormalized>0.5</HeightNormalized>
			      <PositionRefer>topLeft</PositionRefer>
			      <WidthNormalized>0.5</WidthNormalized>
			      <PositionNormalized>0.5</PositionNormalized>
			      <PositionNormalized>0.3</PositionNormalized>
		    </VideoLayers>
		    <LayoutId>72d2ec7a-4cd7-4a01-974b-7cd53947f053</LayoutId>
		    <BlendList>RV01</BlendList>
		    <BlendList>RV02</BlendList>
	  </Layouts>
	  <Layouts>
		    <MixList>RV01</MixList>
		    <AudioLayers>
			      <ValidChannel>all</ValidChannel>
			      <VolumeRate>0.5</VolumeRate>
		    </AudioLayers>
		    <VideoLayers>
			      <HeightNormalized>1</HeightNormalized>
			      <PositionRefer>topLeft</PositionRefer>
			      <WidthNormalized>1</WidthNormalized>
			      <PositionNormalized>0</PositionNormalized>
			      <PositionNormalized>0</PositionNormalized>
		    </VideoLayers>
		    <VideoLayers>
			      <HeightNormalized>0.4</HeightNormalized>
			      <PositionRefer>topLeft</PositionRefer>
			      <WidthNormalized>0.4</WidthNormalized>
			      <PositionNormalized>0.1</PositionNormalized>
			      <PositionNormalized>0.1</PositionNormalized>
		    </VideoLayers>
		    <LayoutId>21926b36-7dd2-4fde-ae25-51b5bc8e52d8</LayoutId>
		    <BlendList>RV01</BlendList>
		    <BlendList>RV02</BlendList>
	  </Layouts>
</DescribeCasterLayoutsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Layouts":[
		{
			"BlendList":[
				"RV01",
				"RV02"
			],
			"MixList":[
				"RV01"
			],
			"VideoLayers":[
				{
					"PositionNormalized":[
						0,
						0.3
					],
					"HeightNormalized":0.5,
					"WidthNormalized":0.5,
					"PositionRefer":"topLeft"
				},
				{
					"PositionNormalized":[
						0.5,
						0.3
					],
					"HeightNormalized":0.5,
					"WidthNormalized":0.5,
					"PositionRefer":"topLeft"
				}
			],
			"AudioLayers":[
				{
					"VolumeRate":1,
					"ValidChannel":"all"
				}
			],
			"LayoutId":"72d2ec7a-4cd7-4a01-974b-7cd53947f053"
		},
		{
			"BlendList":[
				"RV01",
				"RV02"
			],
			"MixList":[
				"RV01"
			],
			"VideoLayers":[
				{
					"PositionNormalized":[
						0,
						0
					],
					"HeightNormalized":1,
					"WidthNormalized":1,
					"PositionRefer":"topLeft"
				},
				{
					"PositionNormalized":[
						0.1,
						0.1
					],
					"HeightNormalized":0.4,
					"WidthNormalized":0.4,
					"PositionRefer":"topLeft"
				}
			],
			"AudioLayers":[
				{
					"VolumeRate":0.5,
					"ValidChannel":"all"
				}
			],
			"LayoutId":"21926b36-7dd2-4fde-ae25-51b5bc8e52d8"
		}
	],
	"RequestId":"3be7ade8-d907-483c-b24a-0dad4595beaf"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

