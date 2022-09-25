# 仅在个人学习和研究目的范围内使用此平台，禁止用于商业用途。 
# 接口文档
## Akamai
### 前言

- 要过akamai主要有两导坎：第一坎：TLS指纹 第二坎：sensor_data行为数据。

- TLS指纹是指在握手协议中发送 CLIENT HELLO 中的数据唯一标识，通过TLS指纹可以识别是否是通过正规途径进行访问。目前akamai通过白名单方式只允许部分TLS指纹能通过，只要能模拟浏览器的指纹即可通过akamai的TLS认证。

- sensor_data行为数据是指在浏览器中访问网站的相关行为，包括浏览器信息、鼠标、按键信息等等组成的行为数据，通过行为数据进行判断是否为机器人访问，只要能模拟行为数据即可通过akamai的行为认证

- ip质量：ip质量决定着行为数据的通过率，甚至部分ip被拉黑名单，无法通过。

- 并发：同一个ip同时请求的话很容易ip被禁。如果需要并发必须使用代理ip

### 版本
- 目前Akamai分两个版本2.0和1.75，目前只支持1.75


#### 💡联系客服<liberty-space@protonmail.com>注册即送1000点数，加微信好友再送5000点数


### API
#### sensor_data1.75


POST `http://api.liberty.com/akamai/v1/sensorData`

`Content-Type` application/json

> 请求参数

|属性|类型|必须|说明|
|----|----|----|----|
|app_key|String|是|注册之后获得|
|abck|String|是|cookie中_abck的值|
|ua|String|是|建议使用该userAgent|

> 请求实例
```
{
    "app_key":"cc9c18d3e263515c2c072b36a7125eecc078618f",
    "ua":"Mozilla/5.0 (Macintosh; Intel Mac OS X 11_15_7) AppleWebKit/427.16 (KHTML, like Gecko) Chrome/106.0.0.0 Safari/427.36",
    "abck":"238B9642300FA4F75CA3DC6925F6BCD9~-1~YAAQVf6Yc/AQrPqBAQAAOwsa/gjB3EW6gEF2Vz2sca3/8zIuGAGII8ysl0U2O5K4jkUHKNGR9Z+M3UVVfCEgu2Me8sJUOU26A+OPgv+fJhOFwOyOqt9n9F9YgsiBD8E+3DFqj+usABqUI5JzfXHsfiPT3+/Mf/sN9zNhWrWQXARlC6eMg7HcSP60qR4Se1xU7av5SQ8SqN+Jyw8viFKTIwYu+2Nr0n/2bogGSnWA5SEQGITlyVRmhn6dYZ4u9BhH35oJSNPegDqeT5/ieCyoH9m+hwguJag66GTcg1W7oFOwAhoEDRNcHZ4D277eshU8/GyC6qTOvmhOlFHYJgS+aojA9Rhy9B0GvOdhP0w0wOdvLhHfedDagiDM8EUQ4S6DJhR+E1+CxQ7MBrCZvUxKUjm/srCJRZ4ZYQJzZgdXVdr8K9GcaSgu~-1~-1~-1"
}
```
> 响应参数

|属性|类型|必须|说明|
|----|----|----|----|
|code|String|是|20000：成功<br/>50001：appKey认证失败<br/>51001：可用点数不足<br/><br/>40004：参数缺失|
|errMsg|String|否|异常说明|
|data|String|是|结果|

> 响应示例
```
{
    "code": "20000",
    "errMsg": "",
    "data": "7a74G7m23Vrp0o5c9355031.75-1,2,-94,-100,Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.182 Safari/537.36,uaend,12147,20030107,sr-RS,Gecko,5,0,0,0,407807,2366938,1920,1040,1920,1080,1920,969,0,,cpen:0,i1:0,dm:0,cwen:0,non:1,opc:0,fc:0,sc:0,wrc:1,isc:0,vib:1,bat:1,x11:0,x12:1,8329,.7090697168354,828716143524.5,0,loc:-1,2,-94,-131,Mozilla/5.0 (Windows;10.0.0;x86;64;) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.182 Safari/537.36-1,2,-94,-101,do_en,dm_en,t_en-1,2,-94,-105,0,-1,0,1,-1,431,1;0,0,0,1,-1,321,0;0,-1,1,1,318,-1,0;0,-1,1,1,492,277,0;-1,2,-94,-102,0,-1,0,1,-1,431,1;0,0,0,1,-1,321,0;0,-1,1,1,318,-1,0;0,-1,1,1,492,277,0;-1,2,-94,-108,-1,2,-94,-110,0,1,244,621,298;1,1,290,621,302;2,1,305,618,301;3,1,332,615,300;4,1,366,620,303;5,1,401,623,305;6,1,421,624,305;7,1,442,629,301;8,1,449,632,298;9,1,487,635,297;10,1,526,636,292;11,1,550,641,289;12,1,575,644,287;13,1,585,645,287;14,1,626,650,283;15,1,668,653,280;16,1,695,655,279;17,1,723,655,274;18,1,736,659,270;19,1,750,661,268;20,1,795,661,268;21,1,825,665,263;22,1,856,667,260;23,1,872,667,259;24,1,889,671,259;25,1,937,673,255;26,1,986,673,253;27,1,1020,677,252;28,1,1040,679,247;29,1,1061,679,244;30,1,1067,683,243;-1,2,-94,-117,-1,2,-94,-111,0,220,-1,-1,-1;-1,2,-94,-109,0,220,-1,-1,-1,-1,-1,-1,-1,-1,-1;-1,2,-94,-114,-1,2,-94,-103,-1,2,-94,-112,https://www.maersk.com.cn/-1,2,-94,-115,1,49801,32,220,220,0,50209,79885,0,1657432287049,7,17730,0,32,2955,0,0,79899,20959,0,,0,20,6620378394,30261693,PiZtE,37074,70,0,-1-1,2,-94,-106,8,2-1,2,-94,-119,-1-1,2,-94,-122,0,0,0,0,1,0,0-1,2,-94,-123,-1,2,-94,-124,-1,2,-94,-126,-1,2,-94,-127,11321144241322243122-1,2,-94,-70,-1752250632;-915298718;dis;,7,8;true;true;true;-660;true;24;24;true;false;-1-1,2,-94,-80,5633-1,2,-94,-116,3-1,2,-94,-118,92014-1,2,-94,-129,33c6f54e72ed2196a148f981eb3a5bd51bb6639069e41454a91411e89e70f64e,1,1dfd398567a532829bcf57210a322c5c284a154b08cb80216bf2badc60d20a44,Google Inc. (Intel),ANGLE (Intel, Intel(R) HD Graphics 520 Direct3D11 vs_5_0 ps_5_0, D3D11-23.20.16.5038),95f5b71fe531f867faa814bdd4050dd8057206d53ecec1163523560525884870,33-1,2,-94,-121,;24;16;2"
}
```

#### TLS

POST `http://api.liberty.com/tls/v1/parsing`

`Content-Type` application/json

> 请求参数

|属性|类型|必须|说明|
|----|----|----|----|
|app_key|String|是|注册之后获得|
|method|String|是|请求方式：get、post|
|url|String|是|目标地址|
|params|String|是|参数, 没有传空对象, eg. {}|
|data|String|是|请求数据, 没有传空对象, eg. {}|
|headers|String|是|请求头信息, 没有传空对象, eg. {}|
|proxies|String|是|代理|

> 请求实例
```
{
    "app_key":"cc9c18d3e263515c2c072b36a7125eecc078618f",
    "method":"get",
    "url":"http://www.xxx.com/xxx",
    "params":{},
    "data":{},
    "headers":{},
    "proxies":"http://www.xxx.com/xxx"
}
```
> 响应参数
```
{
    "code":20000,
    "data":{
        "response_headers":{
            "accept-ranges":"bytes",
            "cache-control":"no-cache",
            "content-type":"text/html; charset=utf-8",
            "date":"Sun, 18 Sep 2022 02:47:26 GMT",
            "etag":"\"62564166-170e\"",
            "last-modified":"Wed, 13 Apr 2022 03:20:06 GMT",
            "server":"nginx",
            "vary":"Accept-Encoding",
            "x-cache-lookup":"Cache Hit, Hit From Inner Cluster",
            "x-nws-log-uuid":"10720956672718696149",
            "transfer-encoding":"chunked"
        },
        "response_text":"<!DOCTYPE html>\n<html>\n\t<head>\n\t\t<meta charset=\"utf-8\" />\n\t\t<meta http-equiv=\"X-UA-Compatible\" con\"c\t\t\t\t});\n\t\t\t\t\t} catch (error) {}\n\t\t\t\t});\n\t\t\t});\n\t\t</script>\n\t</body>\n</html>\n<!--[if !IE]>|xGv00|8f85bc5ee2a463e0e5c16c474a6dd271<![endif]-->\n"
    }
}
```

## 点数说明
1. **获取点数**
    - 参与官方活动，定期活动
    - 邀请好友注册并充值。马上获得10000点数，同时获得该好友第一个月60%、第二个月40%、第三个月20%、第四个月以后永久10%的充值点数
    - 充值获取。1元=1000点（暂时不支持线上充值，可先通过转账方式充值，敬请谅解）；
2. **点数消耗**
    > 调用接口并成功返回即消耗点数，akamai接口不保证100%可通过，各个网站通过率略有差异，如果通过率低可联系客服<liberty-space@protonmail.com>。

    
    |接口|消耗点数|扣除方式|
    |----|----|----|
    |akamai1.75|90|返回成功数据|
    |tls|6|返回成功数据|

