# Facebook 后台事件上报

## 接口参数
|参数|值|
|-----------------|-----------------|
| URL     | https://api.grtghcorp.com/event     |
| Method        | POST      |
| Content-Type        | application/json         |

##json参数含义
|参数名|类型|是否必须|参考值|	描述|
|-----------------|-----------------|-----------------|-----------------|-----------------|
| link_id     | string     | 是     | 173042697222345     | 由系统生成的	推广链接ID     |
| event_name        | string     | 是     | Purchase     | 从广告平台获取的事件名称或标识。（含自定义事件）      |
| extra        | string     | 否     | {"currency": "USD", "value": 19.99}    | 事件的额外参数。如果对应的事件需要传递额外参数放在本字段中，服务器将会透传至facebook广告平台。         |
##关于是否需要传递额外参数请查询各广告平台的事件定义。以下是 Facebook 平台部分需要提供的额外字段的事件：
|事件名称|英文名称|必填参数|
|-----------------|-----------------|-----------------|
| 加入购物车     | AddToCart     | event_name     |
| 加入心愿单        | AddToWishlist      | event_name     |
| 完成注册       | CompleteRegistration         | event_name     |
| 订阅       | Subscribe         | event_name     |
| 结账       | Purchase         | event_name、currency、value     |
| 自定义事件       | test_event         | event_name     |

##上报json格式
###有附加extra数据格式
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
###无附加extra数据格式
```
{
  "link_id": "173081035393713",
  "event_name": "Purchase"
}
```
