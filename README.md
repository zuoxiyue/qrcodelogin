# qrcodelogin
二维码扫描登录

登录流程说明：

1.打开web登录页，选择扫码登录，调取后端生成二维码唯一标识token和二维码图片(base64)接口，展示二维码.

2.Web页面与后端(判断二维码是否扫描接口建立websocket连接)进行实时通讯，获取二维码扫描状态，及二维码是否失效，如果二维码失效则重新请求新的二维码并与后端实时通讯

3.App进行扫码,弹出确认登录界面

4.App弹出是否确认登录

①　一直未确认登录，二维码失效，web端显示二维码失效页面

②　确认登录：

1)则app携带二维码唯一标识对当前app登录用户进行授权(授权web端进行登录)
2)websocket连接会实时推送授权状态及二维码失效状态到web前端，如果授权返回并且扫描状态为已经扫描，则web前端跳转登录后主页。
3)web携带token进行无用户密码登录并返回相关所需信息

具体流程图如下：

![image](https://github.com/liunian-robert/qrcodelogin/blob/master/qrcodelogin.png)

