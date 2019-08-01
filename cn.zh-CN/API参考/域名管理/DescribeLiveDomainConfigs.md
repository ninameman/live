# DescribeLiveDomainConfigs {#doc_api_live_DescribeLiveDomainConfigs .reference}

调用DescribeLiveDomainConfigs查询直播域名配置，一次可查询多个功能配置。

功能说明

|名称

|说明

|
|----|----|
|referer\_white\_list\_set

|refer白名单

|
|referer\_black\_list\_set

|refer黑名单

|
|filetype\_based\_ttl\_set

|文件过期时间设置

|
|path\_based\_ttl\_set

|目录过期时间设置

|
|cc\_defense

|防CC攻击

|
|oss\_auth

|OSS鉴权Bucket

|
|ip\_black\_list\_set

|IP黑名单

|
|ip\_white\_list\_set

|IP白名单

|
|error\_page

|错误页面重定向

|
|tesla

|页面优化加速

|
|set\_req\_host\_header

|修改回源自定义头

|
|set\_hashkey\_args

|忽略url参数

|
|aliauth

|阿里鉴权

|
|set\_resp\_header

|设置响应头（浏览器端可见）

|
|video\_seek

|视频切片拖拽开关

|
|range

|Range请求功能

|
|gzip

|页面Gzip优化

|
|https\_force

|强制HTTPS跳转

|
|http\_force

|强制HTTP跳转

|
|alilive

|视频直播配置

|
|forward\_scheme

|自适应回源

|
|tmd\_signature

|TMD自定义规则

|

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDomainConfigs&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDomainConfigs|系统规定参数，取值：**DescribeLiveDomainConfigs**。

 |
|DomainName|String|是|live.yourdomain.com|您的加速域名。

 |
|FunctionNames|String|是|set\_req\_host\_header|功能列表名称，用逗号分隔。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DomainConfigs| | |直播域名配置。

 |
|ConfigId|String|5003576|配置ID。

 |
|FunctionArgs| | |域名功能配置参数。

 |
|ArgName|String|domain\_name|参数名称。

 |
|ArgValue|String|testscdn3.cdnpe.com|配置参数值。

 |
|FunctionName|String|set\_req\_host\_header|域名配置功能名称。

 |
|Status|String|success|配置状态。

 |
|RequestId|String|F8AA0364-0FDB-4AD5-AC74-D69FAB8924ED|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveDomainConfigs
&DomainName=live.yourdomain.com
&FunctionNames=set_req_host_header
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveDomainConfigsResponse>
	  <RequestId>F8AA0364-0FDB-4AD5-AC74-D69FAB8924ED</RequestId>
	  <DomainConfigs>
		    <DomainConfig>
			      <Status>success</Status>
			      <FunctionArgs>
				        <FunctionArg>
					          <ArgName>domain_name</ArgName>
					          <ArgValue>testscdn3.cdnpe.com</ArgValue>
				        </FunctionArg>
			      </FunctionArgs>
			      <ConfigId>5003576</ConfigId>
			      <FunctionName>set_req_host_header</FunctionName>
		    </DomainConfig>
		    <DomainConfig>
			      <FunctionArgs>
				        <Status>success</Status>
				        <FunctionArg>
					          <ArgName>file_type</ArgName>
					          <ArgValue>txt</ArgValue>
				        </FunctionArg>
				        <FunctionArg>
					          <ArgName>ttl</ArgName>
					          <ArgValue>13</ArgValue>
				        </FunctionArg>
				        <FunctionArg>
					          <ArgName>weight</ArgName>
					          <ArgValue>8</ArgValue>
				        </FunctionArg>
			      </FunctionArgs>
			      <ConfigId>5068995</ConfigId>
			      <FunctionName>filetype_based_ttl_set</FunctionName>
		    </DomainConfig>
	  </DomainConfigs>
</DescribeLiveDomainConfigsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"F8AA0364-0FDB-4AD5-AC74-D69FAB8924ED",
	"DomainConfigs":{
		"DomainConfig":[
			{
				"Status":"success",
				"FunctionArgs":{
					"FunctionArg":[
						{
							"ArgName":"domain_name",
							"ArgValue":"testscdn3.cdnpe.com"
						}
					]
				},
				"FunctionName":"set_req_host_header",
				"ConfigId":5003576
			},
			{
				"FunctionArgs":{
					"Status":"success",
					"FunctionArg":[
						{
							"ArgName":"file_type",
							"ArgValue":"txt"
						},
						{
							"ArgName":"ttl",
							"ArgValue":"13"
						},
						{
							"ArgName":"weight",
							"ArgValue":"8"
						}
					]
				},
				"FunctionName":"filetype_based_ttl_set",
				"ConfigId":5068995
			}
		]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

