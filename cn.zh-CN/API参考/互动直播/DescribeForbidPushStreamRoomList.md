# DescribeForbidPushStreamRoomList {#doc_api_live_DescribeForbidPushStreamRoomList .reference}

获取禁播房间列表，被禁止推流的房间可以通过此接口获取。

获取禁播房间列表，被禁止推流的房间可以通过此接口获取。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeForbidPushStreamRoomList&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeForbidPushStreamRoomList|系统规定参数，取值：**DescribeForbidPushStreamRoomList**

 |
|AppId|String|是|live-app|业务方APP ID。

 |
|Order|String|否|desc|支持的创建时间排列方式，递增：asc， 降序：desc 默认：desc 降序

 |
|PageNum|Integer|否|1|页码。 默认：1

 |
|PageSize|Integer|否|3|每页数量。 默认：10

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|89867394-E4C7-4612-A467-C20F062B0C07|该条任务请求Id

 |
|RoomList| | |房间列表

 |
|AnchorId|String|xxx|主播Id

 |
|OpEndTime|String|2018-05-24T08:58:26Z|禁播结束时间\(UTC\)

 |
|OpStartTime|String|2018-05-24T08:58:26Z|禁播开始时间\(UTC\)

 |
|RoomId|String|miyou\_test\_1|房间Id

 |
|TotalNum|Integer|3|总条数

 |
|TotalPage|Integer|1|总页数

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com?Action=DescribeForbidPushStreamRoomList
&AppId=live-app
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeForbidPushStreamRoomListResponse>
	  <TotalPage>1</TotalPage>
	  <TotalNum>3</TotalNum>
	  <RequestId>89867394-E4C7-4612-A467-C20F062B0C07</RequestId>
	  <RoomList>
		    <Room>
			      <AnchorId></AnchorId>
			      <RoomId>miyou_test_1</RoomId>
			      <OpStartTime>2018-05-24T08:58:26Z</OpStartTime>
			      <OpEndTime>2018-05-24T08:58:26Z</OpEndTime>
		    </Room>
		    <Room>
			      <AnchorId></AnchorId>
			      <RoomId>roomId-1000</RoomId>
			      <OpStartTime>2018-05-24T08:58:26Z</OpStartTime>
			      <OpEndTime>2018-05-24T08:58:26Z</OpEndTime>
		    </Room>
		    <Room>
			      <AnchorId></AnchorId>
			      <RoomId>roomId-1001</RoomId>
			      <OpStartTime>2018-05-24T08:58:26Z</OpStartTime>
			      <OpEndTime>2018-05-24T08:58:26Z</OpEndTime>
		    </Room>
	  </RoomList>
</DescribeForbidPushStreamRoomListResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalPage":1,
	"TotalNum":3,
	"RequestId":"89867394-E4C7-4612-A467-C20F062B0C07",
	"RoomList":{
		"Room":[
			{
				"AnchorId":"",
				"RoomId":"miyou_test_1",
				"OpStartTime":"2018-05-24T08:58:26Z",
				"OpEndTime":"2018-05-24T08:58:26Z"
			},
			{
				"AnchorId":"",
				"RoomId":"roomId-1000",
				"OpStartTime":"2018-05-24T08:58:26Z",
				"OpEndTime":"2018-05-24T08:58:26Z"
			},
			{
				"AnchorId":"",
				"RoomId":"roomId-1001",
				"OpStartTime":"2018-05-24T08:58:26Z",
				"OpEndTime":"2018-05-24T08:58:26Z"
			}
		]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

