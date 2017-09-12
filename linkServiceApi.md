# LinkService API 对接文档


<br>
> 描述

```
通过api将视频的标题，关键字等内容传递给LinkService，LinkService匹配到相关的广告内容返回给媒体。
```

> 接口

http://ls.lkme.cc/linkservice/api/materials

> 请求方式

GET

> 示例

http://ls.lkme.cc/linkservice/api/materials?linkedmeKey=7e289a2484f4368dbafbd1e5c7d06903&title=秋天养生应该多吃什么&keywords=小龙虾&videoLength=175&imei=869949023126053&userId=123&userAge=1&userGender=1&userTag=抽烟,喝酒,烫头,&type=0

> 返回

```json
{
    "statusCode": 200,
    "res": "成功",
    "data": [
        {
            "startTime": 20,
            "endTime": 40,
            "windowImage": "https://linkservice.oss-cn-beijing.aliyuncs.com/467a0a1973b9b5d7b9376e65247b0050_final.png",
            "windowId": "123_1_227",
            "uriScheme": "bdwm://native?pageName=search&keyword=小龙虾",
            "packageName": "com.baidu.lbs.waimai",
            "apkUrl": "http://down.waimai.bdimg.com/1a/a5f4420c8707a4ce60e465a8a69f531b.d/BaiduWaimai.apk",
            "appstoreUrl": "https://itunes.apple.com/cn/app/%E7%99%BE%E5%BA%A6%E5%A4%96%E5%8D%96-%E7%BE%8E%E9%A3%9F%E8%AE%A2%E9%A4%90%E5%93%81%E8%B4%A8%E7%94%9F%E6%B4%BB-%E8%B6%85%E5%B8%82%E6%B0%B4%E6%9E%9C%E5%AE%89%E5%85%A8%E5%88%B0%E5%AE%B6/id911686788?mt=8",
            "h5Url": ""
        }
    ]
}
```

> 参数说明

| 字段 | 类型 | 是否必填 | 描述 |
| --- | --- | --- | --- |
| linkedmeKey | String | Required  | 媒体方标识 |
| adPositionId | String | Required  | 广告位 |
| title | String | Required  | 视频标题 |
| keywords | String | Required  | 视频关键字 |
| videoLength | String | Required  | 视频时长 |
| imei | String | Required (Android)|<div>安卓设备的imei原值，如果是Android系统则必填</div>|
| idfa | String | Required (iOS) |  <div>苹果设备的idfa原值，如果是iOS系统则必填</div>|
| type | Int | Required |  <div>0\. 橱窗广告</div><div>1\. Banner广告</div><div>2\. 贴片广告</div>|
| userId | String | optional | 媒体方给用户的标识 |
| userAge | String | optional | 出生年月日，例：19910102 |
| userGender  | String | optional | 性别：</br>M男性</br>F：女性</br>O：未知</br>(不填写默认为O) |
| userTag | String | optional | 用户兴趣爱好等，用逗号分割 |
| randomOne | String | optional | "1":随机获取一条广告 不传该参数正常获取广告 |






> 描述

```
上报广告状态（如展示，点击，唤起等）
```

> 接口

http://ls.lkme.cc/linkservice/uploadstatus

> 请求方式

GET

> 示例

http://ls.lkme.cc/linkservice/uploadstatus?video_id=1&window_id=1_1_1&idfa=123-abc&status=14&app_key=123

> 返回

```json
{
    "statusCode": 200,
    "res": "成功",
    "data": null
}
```


| 字段 | 类型 | 是否必须 | 备注 |
| --- | --- | --- | --- |
| linkedmeKey | String | Required | 媒体方Key |
| windoID | String | Required | 标识广告位 |
| status | String |Required  | 展示广告，status值为11</br>点击广告，status值为12</br>唤起APP，status值为13 </br>点击广告，没有唤起APP，status值为14</br>点击广告，去下载APP，status值为15 |



