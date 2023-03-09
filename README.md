# APISpace 介绍
**本 API 服务由 [APISpace（apispace.com）](https://www.apispace.com/?utm_source=github&utm_term=whxx) 提供。**

APISpace 是 Eolink 旗下专业的 API 开放与交易平台，为广大企业以及个人开发者提供多维度、全方位的API接口，覆盖短信验证、天气查询、快递物流、OCR文字识别等海量 API 服务，帮助用户快速获取数据，降低获取数据的成本和难度，提升开发效率。

APISpace 提供15种开发语言的代码示例，分别是：
- Java(OK HTTP)
- HTTP
- cURL
- 微信小程序
- PHP(pecl_http)、PHP(cURL)
- Python(http.client)、Python(Requests)
- JavaScript(Jquery AJAX)、JavaScript(XHR)
- NodeJS(Native)、NodeJS(Request)
- Ruby(Net:Http)
- Shell(Httpie)、Shell(cUrl)

# 尾号限行
提供已知所有执行限行政策的共计65个大城市（800+个区域）未来15天的机动车尾号限行数据查询，包括限行区域、限行规则等。如后续有新增城市加入限行阵营，本接口将第一时间更新。

**使用该产品前，您需要通过 [https://www.apispace.com/eolink/api/456456/introduction](https://www.apispace.com/eolink/api/5345645/introduction?utm_source=github&utm_term=whxx) 申请API服务**

本文档末尾提供了 Python(Requests) 的调用代码示例，可以前往文档末尾查看。

更多代码示例：[https://www.apispace.com/eolink/api/5345645/guidence/](https://www.apispace.com/eolink/api/5345645/guidence/?utm_source=github&utm_term=whxx)

**该产品拥有以下APIs：**
1. 尾号限行
2. 国内城市列表

### 限行城市

全国65个限行城市及其下辖区域的地理信息，包含截止目前实行尾号限行政策的所有城市。

北京：北京
天津：天津
重庆：重庆 
甘肃：兰州 
广东：肇庆 
广西：柳州 
贵州：贵阳 
吉林：长春 
江苏：徐州 
山东：聊城 
湖北：武汉 
浙江：宁波、杭州 
江西：南昌、吉安 
内蒙古：呼伦贝尔、锡林郭勒、通辽 
四川：德阳、绵阳、成都、自贡 
陕西：汉中、渭南、铜川、宝鸡、咸阳、西安 
黑龙江：七台河、佳木斯、伊春、大庆、绥化、哈尔滨 
山西：忻州、晋中、长治、阳泉、晋城、运城、太原、临汾 
河北：唐山、张家口、秦皇岛、廊坊、石家庄、保定、沧州、邢台、邯郸 
河南：驻马店、南阳、濮阳、郑州、鹤壁、安阳、许昌、开封、平顶山、漯河、三门峡、洛阳、焦作、新乡


### 相关附件

在使用尾号限行接口时，需要用到列表中的areacode进行数据调取，也可以根据列表中的geocode做分发处理。

-   [限行城市列表](https://easy-open-link.feishu.cn/wiki/wikcnKc7quwTJilUu8CLhAgTjVe)


### 返回示例

以 尾号限行 为例

```
{
    "status": 0,
    "result": {
        "location": {
            "areacode": "101010100",        //城市ID
            "name": "北京",                //城市中文名
            "country": "中国",                //所属国家中文名
            "path": "北京,北京市,北京市,中国"            //行政区划路径
        },
        "traffic": {
            "limitArea": "五环路以内路段（不含五环路）",  //限行区域
            "limitRule": "北京市暂未恢复实行尾号限行政策",  //限行规则
            "limits": [
                {
                    "date": "2020-04-26",        //日期
                    "number": "W",                //限行尾号，W不限行，S双号限行，D单号限行
                },
                    ……            //其它日期限行信息
            ]
        }
    }
}
```

### Python(Requests) 调用代码示例
这里以 尾号限行API 为例
```
import requests

url = "https://eolink.o.apispace.com/5345645/lives_geo/v001/xianxing"

payload = {"days" : "1","areacode" : "101010100"}

headers = {
    "X-APISpace-Token":"",
    "Authorization-Type":"apikey"
}

response=requests.request("GET", url, params=payload, headers=headers)

print(response.text)

```
