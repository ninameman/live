# AddCasterComponent {#doc_api_live_AddCasterComponent .reference}

调用AddCasterComponent添加组件。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddCasterComponent&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddCasterComponent|系统规定参数，取值：**AddCasterComponent**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播间ID。

 |
|ComponentLayer|String|是|\{"HeightNormalized":"1","PositionRefer":"topRight","WidthNormalized":"0","PositionNormalized":\["0.1","0.2"\]\}|设置该组件Layer的尺寸，布局等信息。

 JSON格式字符串，参数名采用首字母大写、驼峰格式。

 |
|ComponentType|String|是|text|组件类型。可取值：**text** | **image** | **caption**。

 |
|LocationId|String|是|RC01|用于指定组件位置，每个位置至多设置一个组件，格式需符合“RC01…RC99”。

 **说明：** 组件类型为caption时，表示引用的视频源Location。

 |
|CaptionLayerContent|String|否|\{"BorderWidthNormalized":0.01,"SizeNormalized":0.05,"Color":"0x000000","LocationId":"RV01","SourceLan":"cn","FontName":"KaiTi","BorderColor":"0xffffff"\}|设置该Layer元素属性，JSON格式字符串，参数名采用首字母大写，驼峰格式。

 |
|ComponentName|String|否|text01|组件名称。默认为组件ID。

 |
|Effect|String|否|animateH|组件显示的特效 。可取值：

 -   **none（默认值）**：无
-   **animateH**：水平滚动
-   **animateV**：垂直滚动

 |
|ImageLayerContent|String|否|\{"MaterialId":"6cf724c6ebfd4a59b5b3cec6f10d5ecf"\}|设置该Layer元素属性，JSON格式字符串，参数名采用首字母大写，驼峰格式。

 |
|RegionId|String|否|cn-shanghai|区域。

 |
|TextLayerContent|String|否|\{"BorderWidthNormalized":"1","SizeNormalized":"0.2","Color":"0x000000","FontName":"KaiTi","BorderColor":"0x000000","Text":"hello world!"\}|设置该Layer元素属性，JSON格式字符串，参数名采用首字母大写，驼峰格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|ComponentId|String|21926b36-7dd2-4fde-ae25-51b5bc8e52d8|组件ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=AddCasterComponent
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&ComponentLayer={"HeightNormalized":"1","PositionRefer":"topRight","WidthNormalized":"0","PositionNormalized":["0.1","0.2"]}
&ComponentType=text
&LocationId=RC01
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddCasterComponentResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <ComponentId>21926b36-7dd2-4fde-ae25-51b5bc8e52d8</ComponentId>
</AddCasterComponentResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"ComponentId":"21926b36-7dd2-4fde-ae25-51b5bc8e52d8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

