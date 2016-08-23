[TOC]

# 1、简介 [![](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fgf.png)]() 
新浪分享插件

## 1.1 说明
调用新浪分享文字,图片.

**iOS 9 以后,为了预防APP通过非正常渠道获取用户的某些隐私信息,Apple启用了URLScheme白名单机制.**
​    
* **为了正常使用插件的所有功能还需要配置URLScheme白名单**([什么是URLScheme白名单](http://bbs.appcan.cn/forum.php?mod=viewthread&tid=29503&extra=))
* 配置白名单方法请参考[这里](http://newdocx.appcan.cn/newdocx/docx?type=1505_1291#设置urlScheme白名单)
* uexSina需要进白名单添加的URLScheme如下

```
<string>sinaweibohd</string>
<string>sinaweibo</string>
<string>sinaweibosso</string>
<string>sinaweibohdsso</string>
<string>weibosdk</string>
<string>weibosdk2.5</string>
```

* iOS App用过uexSina插件打开新浪客户端进行授权、分享过程完成后,新浪客户端通过应用自定义的UrlScheme返回到本App,并传回授权、分享结果时,需要配置UrlScheme值.通过config.xml配置插件的方法如下

```
<config desc="uexSina" type="URLSCHEME">
    <urlScheme name="uexSina" schemes="['wb407216840']"/>
</config>
```
其中'wb407216840'的'407216840'改成您自己申请到的新浪appkey,`需要是wb+appkey的形式`

## 1.2 UI展示
 ![](http://newdocx.appcan.cn/docximg/164911i2015y6i16c.png)

## 1.3 开源源码
插件测试用例与源码下载:[点击](http://plugin.appcan.cn/details.html?id=186_index) 插件中心至插件详情页 (插件测试用例与插件源码已经提供)

## 1.4 术语表
-----
Path Types

| 协议头             | Android对应路径 (其中"/sdcard/"等 同于"/storage/emulated/0/") | iOS对应路径                           |
| --------------- | ---------------------------------------- | --------------------------------- |
| res://          | widget/wgtRes/                           | widget/wgtRes                     |
| wgts://         | /storage/emulated/0/widgetone/apps/ xxx(widgetAppId)/ | /Documents/apps/xxx(widgetAppId)/ |
| wgts://         | /storage/emulated/0/widgetone/widgets/   | /Documents/widgets/               |
| file:///sdcard/ | /storage/emulated/0/                     | 无                                 |

## 1.5、平台版本支持
本插件的所有API默认支持**Android4.0+**和**iOS7.0+**操作系统.
有特殊版本要求的API会在文档中额外说明.

## 1.6、接口有效性
本插件所有API默认在插件版本**4.0.0+**可用.
在后续版本中新添加的接口会在文档中额外说明.

# 2、API概览
##  2.1 方法

### 📦 registerApp 用户授权

`uexSina.registerApp(appKey,appSecret,registerURL, callbackFunction) `

**说明:**

用户授权,用户授权后可以进行调用分享等接口,如果手机上有微博客户端,会直接调用客户端进行授权.如果没有,则开启网页让用户授权.


**参数:**

| 参数名称             | 参数类型     | 是否必选 | 说明                   |
| ---------------- | -------- | ---- | -------------------- |
| appKey           | String   | 是    | 通过开放平台注册的appKey      |
| appSecret        | String   | 是    | 通过开放平台注册的appSecret   |
| registerURL      | String   | 是    | 通过开放平台注册的registerURL |
| callbackFunction | Function | 是    | 回调函数,用来获取相关业务数据      |

**回调参数:**

```
var callbackFunction = function(data){}
```

| 参数名称 | 类型     | 说明            |
| ---- | ------ | ------------- |
| data | Object | 返回的相关数据,形式见下: |

```
var data = {
    openId: 
    token:
    code:// code 为0时表示成功, 此时openId和token会有值,1 代表失败
}
```

**示例:**
```
var appKey = "4072168402";
var appSecret = "b28223208b965d73c19fab20eab38943";
var registerUrl = "http://www.testsina.com";
uexSina.registerApp(appKey,appSecret,registerUrl, function(data) {
    alert("openId:" + data.openId + "    token:" + data.token);
});
```

### 📦 login 登录

`uexSina.login(appKey,registerUrl, callbackFunction); `

**说明:**

用户登录, 支持SSO登录.如果手机上端有微博客户端,会直接调用客户端进行登录授权.如果没有,则开启网页让用户登录授权.

**参数:**

| 参数名称             | 参数类型     | 是否必选 | 说明                           |
| ---------------- | -------- | ---- | ---------------------------- |
| appKey           | String   | 是    | 通过开放平台注册的appKey,appKey申请点击跳转 |
| registerURL      | String   | 是    | 通过开放平台注册的registerURL         |
| callbackFunction | Function | 是    | 回调函数,用来获取相关业务数据              |

**回调参数:**

```javascript
var callbackFunction = function(error, data){}

```

| 参数名称  | 类型     | 说明                             |
| ----- | ------ | ------------------------------ |
| error | Number | 0表示获取成功,非0表示获取失败               |
| data  | Object | error非0返回NULL;error为0,其数据格式如下: |

```
var data = {
    "uid": "1820127523",
    "expires_in": 1465844397060,
    "access_token": "2.00X_ELzBXB6a8E0b24b217d5CYmpKE",
    "refresh_token": "2.00X_ELzBXB6a8Ef59d49d381oDgtuC"
}
```


**示例:**

```
var appKey = "4072168403";
var registerUrl = "http://www.dotlink.com";
uexSina.login(appKey,registerUrl,function(error,data){
     if(!error){
     alert(JSON.stringify(data));
     }
});
```


### 📦 getUserInfo 获取用户基本信息

`uexSina.getUserInfo(callbackFunction); `

**说明:**

返回该用户的新浪微博相关信息,如用户名,姓别,所在地等.

**参数:**

| 参数名称             | 参数类型     | 是否必选 | 说明              |
| ---------------- | -------- | ---- | --------------- |
| callbackFunction | Function | 是    | 回调函数,用来获取相关业务数据 |

**回调参数:

```
var callbackFunction = function(data){}
```

| 参数名称 | 类型     | 说明                                       |
| ---- | ------ | ---------------------------------------- |
| data | Object | 包含用户的基本信息,信息中包含字段请参考[新浪官方文档](#http://open.weibo.com/wiki/2/users/show) |




**示例:**
```
var commonCallback = function(data) {
    alert("commonCallback:" + JSON.stringify(data));
}
uexSina.getUserInfo(commonCallback);
```

### 📦 logout 退出

`uexSina.logout(callbackFunction); `

**说明:**

注销该新浪微博帐号

**参数:**

| 参数名称             | 参数类型     | 是否必选 | 说明               |
| ---------------- | -------- | ---- | ---------------- |
| callbackFunction | Function | 是    | 回调函数,返回退出是否成功的状态 |

**回调参数:**

```
var callbackFunction = function(data){}
```

| 参数名称 | 类型     | 说明               |
| ---- | ------ | ---------------- |
| data | Number | 退出是否成功,0-成功,1-失败 |

**示例:**

```
uexSina.logout(function(data) {
    alert(data); 
});
```

### 📦 sendTextContent 分享文字

`uexSina.sendTextContent(txt, callbackFunction)`

**说明:**

分享文字

**参数:**

| 参数名称             | 参数类型     | 是否必选 | 说明               |
| ---------------- | -------- | ---- | ---------------- |
| txt              | String   | 是    | 文本内容             |
| callbackFunction | Function | 是    | 回调函数,返回分享是否成功的状态 |

**回调参数:**

```
var callbackFunction = function(data){}
```

| 参数名称 | 类型     | 说明               |
| ---- | ------ | ---------------- |
| data | Number | 分享是否成功,0-成功,1-失败 |



**示例:**

```
var txt = "中国最大的移动中间平台AppCan对新浪微博分享支持测试";
uexSina.sendTextContent(txt, function(data) {
    alert(data); // data: 0 成功, 1 失败
});
```

### 📦 sendImageContent 分享图片

`uexSina.sendImageContent(imagePath,txt, callbackFunction)`

**说明:**

如果要分享网络图片需要申请新浪微博高级权限

**参数:**

| 参数名称             | 参数类型     | 是否必选 | 说明                             |
| ---------------- | -------- | ---- | ------------------------------ |
| imagePath        | String   | 是    | 图片路径,路径协议详见CONSTANT中PathTypes. |
| txt              | String   | 是    | 文本内容                           |
| callbackFunction | Function | 是    | 回调函数,返回分享是否成功的状态               |

**回调参数:**

    var callbackFunction = function(data){}
| 参数名称 | 类型     | 说明               |
| ---- | ------ | ---------------- |
| data | Number | 分享是否成功,0-成功,1-失败 |

**示例:**

```
var content = "中国最大的移动中间平台AppCan对新浪微博分享的图片支持测试";
var realImgPath = "res://sotower.png";
uexSina.sendImageContent(realImgPath, content,function(data) {
    alert(data); 
});
```

# 3、更新历史

### iOS

API版本:`uexSina-4.0.0`

最近更新时间:`2016-06-06`

| 历史发布版本 | 更新内容                                     |
| ------ | ---------------------------------------- |
| 4.0.0  | 支持function传入                             |
| 3.0.7  | uexSina添加分享图片可以分享网络图片的功能                 |
| 3.0.6  | 替换SinaSDK3.1.1,重写授权登陆相关接口;新增login、logout、getUserInfo接口 |
| 3.0.5  | 注册回调方法名统一修改为uexSina.cbRegisterApp        |
| 3.0.4  | 增加新浪授权登录                                 |
| 3.0.3  | 取消用户新浪微博对appcan的自动关注                     |
| 3.0.2  | 统一回调方法名,统一回调参数                           |
| 3.0.1  | 添加uexSina.registerCallBack成功的回调,修复点击分享黑屏的bug |
| 3.0.0  | 新浪分享功能插件                                 |

### Android

API版本:`uexSina-4.0.0`

最近更新时间:`2016-06-06`

| 历史发布版本 | 更新内容                                     |
| ------ | ---------------------------------------- |
| 4.0.0  | 支持function传入                             |
| 3.0.13 | 修复registerApp回调不执行的问题                    |
| 3.0.12 | 修复图片路径读取的问题                              |
| 3.0.11 | 修复了分享图片不能读取wgts://格式的文件问题                |
| 3.0.10 | cbRegisterApp回调openId和token              |
| 3.0.9  | 添加login, getUserInfo, logout接口           |
| 3.0.8  | 去掉插件中的ActivityGroup,配合引擎升级               |
| 3.0.7  | 新增login登陆接口接口                            |
| 3.0.6  | 修改uexSina插件中的代码错误                        |
| 3.0.5  | 修改uexSina插件中registerCallBack和cbShare回调方法返回值:成功为0,失败为1 |
| 3.0.4  | 修复分享图片时路径解析错误问题                          |
| 3.0.3  | 修复适配3.0新引擎的问题                            |
| 3.0.2  | 修复回调数据与文档不一致的问题                          |
| 3.0.1  | 修复插件配置问题                                 |
| 3.0.0  | 新浪分享功能插件                                 |
