# ModifyCasterLayout {#doc_api_live_ModifyCasterLayout .reference}

调用ModifyCasterLayout修改布局配置，传递修改项，非修改内容无需传递。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=ModifyCasterLayout&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyCasterLayout|系统规定参数，取值：**ModifyCasterLayout**。

 |
|BlendList.N|RepeatList|是|RV02|元素为资源的位置ID（locationId参见添加视频源），与VideoLayers元素顺序对应。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台Id。

 |
|LayoutId|String|是|21926b36-7dd2-4fde-ae25-51b5bc8e52d8|布局Id。

 |
|MixList.N|RepeatList|是|RV02|元素为资源的位置ID（locationId参见添加视频源），与VideoLayers元素顺序对应。

 |
|AudioLayer.N.FixedDelayDuration|Integer|否|5000|该字段对视频进行固定延迟设置，可用于字幕同步。

 -   单位：**ms**
-   默认值：**0**
-   取值范围：`[0-5000]`

 |
|AudioLayer.N.ValidChannel|String|否|all|确定哪些声道可以作为音量输入。

 取值范围：**leftChannel** | **rightChannel** | **all（默认值）**

 |
|AudioLayer.N.VolumeRate|Float|否|1|设置该layer元素的高度归一化比例值，其中元素的宽度会按照该高度来进行等比缩放。

 默认值：**0**，表示按照元素的原始尺寸进行显示。

 |
|RegionId|String|否|cn-shanghai|地域。

 |
|VideoLayer.N.FillMode|String|否|fit|元素填充方式。

 -   **none（默认）**：不填充，以画面作为配置目标进行Layer设置。
-   **fit**：自适应，以填充区（框）作为配置目标进行Layer设置，此时画面会按照原始的宽高比缩放，长边对齐的自适应方式在填充区（框）内居中填充，若填充区宽高比和画面不一致，则短边两侧无填充（显示为下层Layer画面，若下层未配置Layer，默认为底图黑色）。

 |
|VideoLayer.N.FixedDelayDuration|Integer|否|5000|该字段对视频进行固定延迟设置，可用于字幕同步。

 -   单位：**ms**
-   默认值：**0**
-   取值范围：`[0-5000]`

 |
|VideoLayer.N.HeightNormalized|Float|否|1|设置该layer元素的高度归一化比例值。

 -   若采用不填充模式，元素的宽度会按照该高度来进行等比缩放，**默认为0**，表示按照画面的原始尺寸进行显示。
-   若采用自适应方式时，该字段必选且**大于0**，表示填充区\(框\)高度归一化比例值。

 |
|VideoLayer.N.PositionNormalized.N|RepeatList|否|0.3|设置该layer 元素的位置归一化值`[x,y]`, 默认为`[0,0]`。注意x,y需要进行归一化计算。

 |
|VideoLayer.N.PositionRefer|String|否|topLeft|设置元素的position参考坐标值。

 取值范围：**topLeft（默认值）** | **topRight** | **bottomLeft** | **bottomRight** | **center** | **topCenter** | **bottomCenter** | **leftCenter** | **rightCenter**。

 |
|VideoLayer.N.WidthNormalized|Float|否|1|设置该layer元素的宽度归一化比例值。

 -   若采用不填充模式，元素的高度会按照该宽度来进行等比缩放，**默认为0**，表示按照画面的原始尺寸进行显示。
-   若采用自适应方式时，该字段必选且**大于0**，表示填充区\(框\)宽度归一化比例值。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|LayoutId|String|21926b36-7dd2-4fde-ae25-51b5bc8e52d8|布局ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyCasterLayout
&BlendList.1=RV02
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&LayoutId=21926b36-7dd2-4fde-ae25-51b5bc8e52d8
&MixList.1=RV02
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyCasterLayoutResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <LayoutId>21926b36-7dd2-4fde-ae25-51b5bc8e52d8</LayoutId>
</ModifyCasterLayoutResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"LayoutId":"21926b36-7dd2-4fde-ae25-51b5bc8e52d8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

