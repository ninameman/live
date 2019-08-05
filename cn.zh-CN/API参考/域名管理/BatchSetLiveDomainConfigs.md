# BatchSetLiveDomainConfigs {#doc_api_live_BatchSetLiveDomainConfigs .reference}

调用BatchSetLiveDomainConfigs批量配置域名。

Functions格式如下：

 `[{"functionArgs":[{"argName":"domain_name","argValue":"www.testdomain.com"}],"functionName":"set_req_host_header"}]` 

示例如下：

 `[{"functionArgs":[{"argName":"file_type","argValue":"jpg"},{"argName":"ttl","argValue":"18"},{"argName":"weight","argValue":"30"}],"functionName":"filetype_based_ttl_set","configId":506xxx}]` 

**说明：** 某些功能，例如**filetype\_based\_ttl\_set**，可以设置多条纪录，当需要更新其中某条纪录时，可通过该条纪录的**configId**来指定。

功能说明如下，所有参数值均按照字符串类型处理。

|名称

|参数

|
|----|----|
|\*\*referer\_white\_list\_set\*\*：refer白名单

|refer\_domain\_allow\_list：白名单列表，多个逗号分隔；

 allow\_empty：是否允许空refer进入，取值范围：on/off。

 |
|\*\*referer\_black\_list\_set\*\*：refer黑名单

|refer\_domain\_deny\_list：黑名单列表，多个逗号分隔；

 allow\_empty：是否允许空refer进入，取值范围：on/off。

 |
|\*\*filetype\_based\_ttl\_set\*\*：文件过期时间设置

|ttl：cache时间，单位：秒；

 file\_type：文件类型，支持多个，用逗号\(英文\)隔开，如txt,jpg；

 weight：权重，取值范围1~199

 |
|\*\*path\_based\_ttl\_set\*\*：目录过期时间设置

|ttl：cache时间，单位：秒；

 path：目录，必须以"/"开头；

 weight：权重，取值范围1~99

 |
|\*\*oss\_auth\*\*：OSS鉴权Bucket

|oss\_bucket\_id：用户bucket地址

|
|\*\*ip\_black\_list\_set\*\*：IP黑名单

|ip\_list：IP列表多个用逗号隔开

|
|\*\*ip\_white\_list\_set\*\*：TMD免拦截

|ip\_list：IP列表多个用逗号隔开

|
|\*\*error\_page\*\*：错误页面重定向

|error\_code：错误码；

 rewrite\_page：重定向页面

 |
|\*\*set\_req\_host\_header\*\*：修改回源自定义头

|domain\_name：回源Host头内容

|
|\*\*set\_hashkey\_args\*\*：忽略url参数

|hashkey\_args：保留参数的列表，多个用逗号分隔；

 disable：disable等于on的时候表示忽略所有参数，off不忽略

 |
|\*\*aliauth\*\*：阿里鉴权

|auth\_type：鉴权类型，取值范围"no\_auth","type\_a","type\_b","type\_c"；

 auth\_key1：鉴权key1；auth\_key2：鉴权key2；

 ali\_auth\_delta：自定义鉴权缓冲时间

 |
|\*\*set\_resp\_header\*\*：设置响应头（浏览器端可见）

|key：响应头；

 value：响应头内容，删除填写null

 |
|\*\*https\_force\*\*：强制HTTPS跳转

|enable：功能开关，取值范围：on/off

|
|\*\*http\_force\*\*：强制HTTP跳转

|enable：功能开关，取值范围：on/off

|
|\*\*l2\_oss\_key\*\*：L2 OSS 回源私钥

|private\_oss\_auth：是否开启私有oss鉴权功能，取值范围：on/off

|
|\*\*green\_manager\*\*：鉴黄功能

|enable：是否开启鉴黄功能，取值范围：on/off

|
|\*\*tmd\_signature\*\*：TMD自定义规则

|name：规则名称，域名内不可重复

 path：可重复，需校验uri路径合法性

 pathType：匹配规则，0 前缀匹配，1 完全匹配

 interval：监测时长，单位秒，参数限制必须\>=10

 count：单IP访问次数

 action：阻断类型，0 封禁，1 人机识别

 ttl:阻断时长，单位秒

 |

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=BatchSetLiveDomainConfigs&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|BatchSetLiveDomainConfigs|系统规定参数，取值：**BatchSetLiveDomainConfigs**。

 |
|DomainNames|String|是|play.yourdomain.com|您的直播域名，多个用英文半角逗号分隔。

 |
|Functions|String|是|\[\{"functionArgs":\[\{"argName":"domain\_name","argValue":"home.1sapp.com"\}\],"functionName":"set\_req\_host\_header"\}\]|功能列表。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|04F0F334-1335-436C-A1D7-6C044FE73368|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=BatchSetLiveDomainConfigs
&DomainNames=play.yourdomain.com
&Functions=[{"functionArgs":[{"argName":"domain_name","argValue":"home.1sapp.com"}],"functionName":"set_req_host_header"}]
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<BatchSetLiveDomainConfigsResponse>
	  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</BatchSetLiveDomainConfigsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。

