# Facebook 服务器API事件上报（测试版）
### 该系统域名为测试域名，需要留一个修改口子

## 接口参数

|参数|值|
|-----------------|-----------------|
| URL     | https://api.grtghcorp.com/event  （测试域名）   |
| Method        | POST      |
| Content-Type        | application/json         |

## 请求参数
### 请使用 JSON 格式在 Request Body 中传递；event_name 请根据广告平台的事件名进行传递，extra里的数据请根据平台的对应事件的相关额外字段进行传递，我们会对应发送给平台。即event_name事件名和extra里的字段按平台规则来写。
|参数名|类型|是否必须|参考值|	描述|
|-----------------|-----------------|-----------------|-----------------|-----------------|
| link_id     | string     | 是     | 173042697222345     | 由系统生成的	推广链接ID  (后续通过链接拼接方式传递 https://xxx/xx?link_id=173042697222345)   |
| event_name        | string     | 是     | Purchase     | 从广告平台获取的事件名称或标识。（含自定义事件）      |
| extra        | string     | 否     | {"currency": "USD", "value": 19.99}    | 事件的额外参数。如果对应的事件需要传递额外参数放在本字段中，服务器将会透传至facebook广告平台。         |


## 关于是否需要传递额外参数请查询各广告平台的事件定义。以下是 Facebook 平台部分需要提供的额外字段的事件：
|事件名称|英文名称|必填参数|
|-----------------|-----------------|-----------------|
| 加入购物车     | AddToCart     | event_name     |
| 加入心愿单        | AddToWishlist      | event_name     |
| 完成注册       | CompleteRegistration         | event_name     |
| 订阅       | Subscribe         | event_name     |
| 结账       | Purchase         | event_name、currency、value     |
| 自定义事件       | test_event         | event_name     |

## 响应参数

### 服务器固定以 JSON 方式返回响应。

|参数名|类型|参考值|描述|
|-----------------|-----------------|-----------------|-----------------|
| code     | int     | 0     |0 代表成功，其他代表失败    |
| msg        | String      |success!|详细信息|
| data        | object        |{}|返回数据|
| fb_msg        | object        |[]|facebook 返回值|
| fb_traceId        | String        |""|facebook 返回值 |

## 请求示例

### 有附加extra数据格式
```
{
  "link_id": "173081035393713",
  "event_name": "Purchase",
  "extra": {
    "currency": "USD",
    "value": 19.99
  }
}
```

### 无附加extra数据格式
```
{
  "link_id": "173081035393713",
  "event_name": "Purchase"
}
```

## 返回示例
```
{
  "code":0,
  "msg":"success!",
  "data":{
      "fb_msg":[],
      "fb_traceId":"AbOz36g-Do8BJw0PUZS53o2"
  }
}
```

