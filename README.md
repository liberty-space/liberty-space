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


#### **sensor_data1.75（接口）**
💡[点击进入【liberty】][1]注册即送1000点数，加微信好友再送5000点数

[1]: http://www.baidu.com
POST `http://api.liberty.com/akamai/v1/sensorData`

`Content-Type` application/json

> 请求参数

|属性|类型|必须|说明|
|----|----|----|----|
|appid|String|是|注册之后获得|
|abck|String|是|cookie中_abck的值|
|siteUrl|String|是|使用网站。必须携带https://|

> 请求实例
```
{
    "appid":"cc9c18d3e263515c2c072b36a7125eecc078618f",
    "abck":"238B9642300FA4F75CA3DC6925F6BCD9~-1~YAAQVf6Yc/AQrPqBAQAAOwsa/gjB3EW6gEF2Vz2sca3/8zIuGAGII8ysl0U2O5K4jkUHKNGR9Z+M3UVVfCEgu2Me8sJUOU26A+OPgv+fJhOFwOyOqt9n9F9YgsiBD8E+3DFqj+usABqUI5JzfXHsfiPT3+/Mf/sN9zNhWrWQXARlC6eMg7HcSP60qR4Se1xU7av5SQ8SqN+Jyw8viFKTIwYu+2Nr0n/2bogGSnWA5SEQGITlyVRmhn6dYZ4u9BhH35oJSNPegDqeT5/ieCyoH9m+hwguJag66GTcg1W7oFOwAhoEDRNcHZ4D277eshU8/GyC6qTOvmhOlFHYJgS+aojA9Rhy9B0GvOdhP0w0wOdvLhHfedDagiDM8EUQ4S6DJhR+E1+CxQ7MBrCZvUxKUjm/srCJRZ4ZYQJzZgdXVdr8K9GcaSgu~-1~-1~-1",
    "siteUrl":"https://ip:port/..."
}
```
