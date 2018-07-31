# 后端技术白皮书
此文档详细讲解了 成都大熊猫繁育研究基地电子游览地图 项目 后端开发中的相关规范.

## 简要概括
成都大熊猫繁育基地电子游览地图后端API项目, 简称PandaMapAPI, 是将服务器后台数据与客户端交换的媒介.

## 项目详情

|类别|信息|注解|
|-|-|-|
|项目名称|PandaMapAPI|-|
|使用语言|PHP|PHP提供了一个简单且易部署的解决方案. 鉴于园区官网使用的既是Nginx + PHP方案, 此API使用PHP将会更加容易部署|

## 公共API定义
**获取地图数据**  
URL: /API/V001/getMapInfo.php  
方法: POST  
键值: 无  
返回值类型: JSON  
返回值:  

```json
{
    "succeed": true,
    "errorInfo": {
        "errCode": 0,
        "errDescription": "No error"
    },
    "mapJPGEncode": "base64",
    "mapJPG": "XXX==(Base64数据)",
    "venues": [
        {
            "displayName": "XX馆",
            "currentDensity": 100,
            "crowdedLevel": 1,
        },
        {
            "displayName": "XX馆",
            "currentDensity": 200,
            "crowdedLevel": 2,
        }
    ]
}
```

## API中返回值类型定义
### crowdedLevel
crowdedLevel是拥挤程度的数字表现, 其中:  
0 - 绿色, 不拥挤  
1 - 蓝色, 正常流量  
2 - 橙色, 稍有拥挤  
3 - 红色, 爆满  