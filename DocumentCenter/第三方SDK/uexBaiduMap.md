/*
Sort: 1
Toc: 1
*/


[TOC]

# 1、简介 [![](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fgf.png)]() <ignore>
提供百度地图的相关相关功能.用户可以使用该插件在网页上嵌入一张地图,并实现对地图的基本操作, 例如放大缩小,移动,点击,隐藏,显示.另外还提供了定位功能,搜索功能,路线规划功能,地理编码功能 .
## 1.1、说明<ignore>
安卓&iOS插件已支持**config.xml文件**配置AK.
>注:IDE插件因为涉及到百度方面的ID与Key暂时无法使用,此插件之前需要进行config.xml相关配置,具体使用点击查看:[附录](http://newdocx.appcan.cn/newdocx/docx?type=1384_975 "百度地图插件接入指引")----->百度地图插件接入指引

## 1.2、UI展示<ignore>
 ![](http://newdocx.appcan.cn/docximg/153918c2015z6c16q.png)
## 1.3、公告<ignore>
安卓百度定位sdk升级,配合安卓打包服务升级,插件已经跟新至最新版本,已经公测通过,请使用最新版本(已支持config.xml文件配置AK)
> 旧版uexBaiduMap 插件已经下架,官方不再维护,如需使用,请[跳转](http://bbs.appcan.cn/forum.php?mod=viewthread&tid=25876 "跳转")到详细官方通告

## 1.4、开源源码<ignore>
[点击](http://plugin.appcan.cn/details.html?id=281_index)插件中心至插件详情页(插件测试用例与插件源码已经提供)

## 1.5、平台版本支持<ignore>
本插件的所有API默认支持**Android4.0+**和**iOS7.0+**操作系统.  
有特殊版本要求的API会在文档中额外说明.

## 1.6、接口有效性<ignore>
本插件所有API默认在插件版本**4.0.0+**可用.  
在后续版本中新添加的接口会在文档中额外说明.

# 2、API概览<ignore>
## 2.1、方法<ignore>
### 📦 open 打开地图

`uexBaiduMap.open(x,y,width,height,longitude,latitude, callbackFunction)`

**说明**

在界面的指定位置显示地图, 成功显示地图后会回调`callbackFunction`

**参数**

| 参数名称             | 参数类型   | 是否必选 | 说明       |
| ---------------- | ------ | ---- | -------- |
| x                | Number | 是    | x坐标      |
| y                | Number | 是    | y坐标      |
| width            | Number | 是    | 地图宽度     |
| height           | Number | 是    | 地图高度     |
| longitude        | Number | 是    | 地图中心点经度  |
| latitude         | Number | 是    | 地图中心点纬度  |
| callbackFunction | 函数     | 否    | 地图打开后的回调 |

* x,y,width,height 的单位均为px
* (x,y)表示地图左上角的坐标


**示例**

```
uexBaiduMap.open(10,100,480,640,"116.309","39.977", function(){
	console.log('------->open success');
});
```

### 📦 close 关闭地图

`uexBaiduMap.close()`

**说明**

关闭地图

**参数**

无

**示例**

```
uexBaiduMap.close();
```
### 📦 hideMap 隐藏地图 

`uexBaiduMap.hideMap()`

**说明**

隐藏地图

**参数**

无

**示例**

```
uexBaiduMap.hideMap();
```

### 📦 showMap 显示地图

`uexBaiduMap.showMap()`

**说明**

显示地图

**参数**

无

**示例**

```
uexBaiduMap.showMap();
```

### 📦 setMapType 设置地图的类型

`uexBaiduMap.setMapType(type)`

**说明**

设置地图的类型

**参数**

| 参数名称 | 参数类型   | 是否必选 | 说明                   |
| ---- | ------ | ---- | -------------------- |
| type | Number | 是    | 地图的类型(1-标准地图,2-卫星地图) |

**示例**

```
uexBaiduMap.setMapType(1);
```

### 📦 setTrafficEnabled 开启或关闭交通图 

`uexBaiduMap.setTrafficEnabled(type)`

**说明**

开启或关闭交通图

**参数**

| 参数名称 | 参数类型   | 是否必选 | 说明        |
| ---- | ------ | ---- | --------- |
| type | Number | 是    | 0-关闭,1-开启 |

**示例**

```
uexBaiduMap.setTrafficEnabled(1);
```

### 📦 setCenter 设置地图的中心点

`uexBaiduMap.setCenter(longitude,latitude)`

**说明**

设置地图的中心点经纬度,地图会移动使此点成为地图的中心点

**参数**

| 参数名称      | 参数类型   | 是否必选 | 说明    |
| --------- | ------ | ---- | ----- |
| longitude | Number | 是    | 中心点经度 |
| latitude  | Number | 是    | 中心点纬度 |

**示例**

```
uexBaiduMap.setCenter(121.481,31.227);
```

### 📦 getCenter 得到地图的中心点

`uexBaiduMap.getCenter()`

**说明**

得到当前地图的中心点经纬度

**参数**
无

**返回值**

获取成功后,返回值是JSON对象,格式如下:
```
{
	longitude:,
	latitude:
}
```
如果失败,返回null

**示例**

```
var data = uexBaiduMap.getCenter();
alert('data:' + JSON.stringify(data));
```


### 📦 setZoomLevel 设置地图的比例级别

`uexBaiduMap.setZoomLevel(zoomLevel)`

**说明**

设置地图的比例级别

**参数**

| 参数名称      | 参数类型   | 是否必选 | 说明              |
| --------- | ------ | ---- | --------------- |
| zoomLevel | Number | 是    | 地图的缩放级别 范围:3~19 |


**示例**

```
uexBaiduMap.setZoomLevel(10);
```

### 📦 zoomIn 放大一个地图级别

`uexBaiduMap.zoomIn()`

**说明**

放大一个地图级别

**参数**

无 

**示例**

```
uexBaiduMap.zoomIn();
```

### 📦 zoomOut 缩小一个地图级别 

`uexBaiduMap.zoomOut()`

**说明**

缩小一个地图级别

**参数**

无


**示例**

```
uexBaiduMap.zoomOut();
```

### 📦 rotate 旋转地图

`uexBaiduMap.rotate(angle)`

**说明**

旋转地图

**参数**

| 参数名称  | 参数类型   | 是否必选 | 说明                                |
| ----- | ------ | ---- | --------------------------------- |
| angle | Number | 是    | 旋转地图的角度,旋转角范围:-180~180,单位:度,逆时针旋转 |


**示例**

```
uexBaiduMap.rotate(90);
```
### 📦 overlook 俯视地图 

`uexBaiduMap.overlook(angle)`

**说明**

俯视地图

**参数**

| 参数名称  | 参数类型   | 是否必选 | 说明                      |
| ----- | ------ | ---- | ----------------------- |
| angle | Number | 是    | 俯视地图的角度,俯角范围:-45~0,单位:度 |


**示例**

```
uexBaiduMap.overlook(-30);
```

### 📦 setZoomEnable 开启或关闭缩放 

`uexBaiduMap.setZoomEnable(type)`

**说明**

开启或关闭缩放

**参数**

| 参数名称 | 参数类型   | 是否必选 | 说明        |
| ---- | ------ | ---- | --------- |
| type | Number | 是    | 0-关闭,1-开启 |

**示例**

```
uexBaiduMap.setZoomEnable(1);
```

### 📦 setRotateEnable 开启或关闭旋转 

`uexBaiduMap.setRotateEnable(type)`

**说明**

开启或关闭旋转

**参数**

| 参数名称 | 参数类型   | 是否必选 | 说明        |
| ---- | ------ | ---- | --------- |
| type | Number | 是    | 0-关闭,1-开启 |


**示例**

```
uexBaiduMap.setRotateEnable(1);
```

### 📦 setCompassEnable 开启或关闭指南针

`uexBaiduMap.setCompassEnable(type)`

**说明**

开启或关闭指南针

**参数**

| 参数名称 | 参数类型   | 是否必选 | 说明        |
| ---- | ------ | ---- | --------- |
| type | Number | 是    | 0-关闭,1-开启 |


**示例**

```
uexBaiduMap.setCompassEnable(1);
```

### 📦 setScrollEnable 开启或关闭平移

`uexBaiduMap.setScrollEnable(type)`

**说明**

开启或关闭平移

**参数**

| 参数名称 | 参数类型   | 是否必选 | 说明        |
| ---- | ------ | ---- | --------- |
| type | Number | 是    | 0-关闭,1-开启 |


**示例**

```
uexBaiduMap.setScrollEnable(1);
```
### 📦 setOverlookEnable 开启或关闭俯视 

`uexBaiduMap.setOverlookEnable(type)`

**说明**

开启或关闭俯视

**参数**

| 参数名称 | 参数类型   | 是否必选 | 说明        |
| ---- | ------ | ---- | --------- |
| type | Number | 是    | 0-关闭,1-开启 |


**示例**

```
uexBaiduMap.setOverlookEnable(1);
```
### 📦 addMarkersOverlay 添加标注

`uexBaiduMap.addMarkersOverlay(json);`

**说明**

添加标注

**参数**

| 参数名称 | 参数类型 | 是否必选 | 说明                            |
| ---- | ---- | ---- | ----------------------------- |
| json | Json | 是    | 添加到地图的标注信息的集合.该字符串为JSON格式.如下: |

```javascript
var json=[
	{
		longitude:,//(必选)经度 
		latitude:,//(必选)纬度 
		icon:,//(可选)标注图标路径,支持类型:"res://""http://" 
		bubble:{//(可选)自定义弹出气泡 
			 title:,//(必选)自定义弹出气泡标题
			 bgImage://(可选)自定义弹出气泡背景图片,格式:res://btn.png 
		} 
	}
] 
		
```
各字段含义如下:

| 参数        | 参数类型   | 是否必选 | 说明                            |
| --------- | ------ | ---- | ----------------------------- |
| longitude | Number | 是    | 经度                            |
| latitude  | Number | 是    | 纬度                            |
| icon      | String | 否    | 标注图标路径,支持类型:"res://""http://" |
| bubble    | String | 否    | 自定义弹出气泡                       |
| title     | String | 是    | 自定义弹出气泡标题                     |
| bgImage   | String | 否    | 自定义弹出气泡背景图片,格式:res://btn.png  |

**返回值**

返回marker对象组成的一个数组,如果添加失败返回为空

**示例**

```javascript
var data = [
	{
		longitude:"116.400244",
		latitude:"39.963175",
		icon:"http://www.iconpng.com/png/mapmarkers/marker_inside_azure.png",
 		bubble:{
			title:"title1"
 		}
	},
	{
		longitude:"116.369199",
		latitude:"39.942821",
		bubble:{
			title:"title2",
			bgImage:"res://btn.png"
		}
	},
	{
		longitude:"116.404",
		latitude:"39.915",
		icon:"http://www.iconpng.com/png/mapmarkers/marker_inside_azure.png",
		bubble:{
			title:"title3",
			bgImage:"res://btn.png"
		}
	}
];
var dataStr = JSON.stringify(data);
var markers=uexBaiduMap.addMarkersOverlay(dataStr);
if(!markers){
	alert("添加失败");
}
 
 
```
### 📦 setMarkerOverlay 更新设置标注信息

`uexBaiduMap.setMarkerOverlay(marker,markerInfo);`

**说明**

更新设置标注信息

**参数**

| 参数         | 参数类型   | 是否必选 | 说明                                       |
| ---------- | ------ | ---- | ---------------------------------------- |
| marker     | Object | 是    | [addMarkersOverlay](# addMarkersOverlay 添加标注)接口返回的marker对象 |
| markerInfo | String | 是    | 标注信息,json格式                              |

```
var markerInfo={
	longitude:,//标注经度
	latitude:,//标注纬度
	icon://标注图标
	bubble:{//气泡设置
		title:,//气泡标题
		bgImage://气泡背景图片
		}
	}
```

**示例**

```
var markerInfo =
	{
		bubble: {
			bgImage: "res://btn.png",
			title: "这是标题"
		},
		latitude: "39.021514",
		longitude: "116.232323"
		
	};
var jsonStr=JSON.stringify(markerInfo);
var marker = ;//addMarkersOverlay接口返回的marker对象
uexBaiduMap.setMarkerOverlay(marker, jsonStr);
 
```

### 📦 showBubble 显示标注气泡 

`uexBaiduMap.showBubble(marker);`

**说明**

显示指定标注气泡,地图上仅有一个标注气泡显示,其他标注气泡将被隐.

**参数**

| 参数     | 参数类型   | 是否必选 | 说明                                       |
| ------ | ------ | ---- | ---------------------------------------- |
| marker | Object | 是    | [addMarkersOverlay](# addMarkersOverlay 添加标注)接口返回的marker对象 |


**示例**

```
var marker = ;//addMarkersOverlay接口返回的marker对象
uexBaiduMap.showBubble(marker);
```
### 📦 hideBubble 隐藏标注气泡 

`uexBaiduMap.hideBubble();`

**说明**

当前显示的标注气泡将被隐藏.

**参数**

无 



**示例**

```
uexBaiduMap.hideBubble();
```
### 📦 addDotOverlay 添加点覆盖物 

`uexBaiduMap.addDotOverlay(dotInfo);`

**说明**

添加点覆盖物

**参数**

| 参数名称    | 参数类型   | 是否必选 | 说明                         |
| ------- | ------ | ---- | -------------------------- |
| dotInfo | String | 是    | 添加到地图上的圆点信息.该字符串为JSON格式如下: |

```
var dotInfo={
	fillColor:,
	radius:,
	longitude:,
	latitude:
}
```

各字段含义如下

| 参数        | 参数类型   | 是否必须 | 说明                         |
| --------- | ------ | ---- | -------------------------- |
| fillColor | String | 是    | 圆点颜色,支持格式:"#000","#000000" |
| radius    | Number | 是    | 圆点半径,单位:像素                 |
| longitude | Number | 是    | 圆点经度                       |
| latitude  | Number | 是    | 圆点纬度                       |

**返回值**

返回overlay覆盖物对象,如果添加失败返回为空

**示例**

```
var dotInfo={
	fillColor:"#990033",
	longitude:"116.400244",
	latitude:"39.963175",
	radius:"50"
};
var jsonStr=JSON.stringify(dotInfo);
var overlay=uexBaiduMap.addDotOverlay(jsonStr);
if(!overlay){
	alert("添加失败");
}
```
### 📦 addPolylineOverlay 添加折线覆盖物

`uexBaiduMap.addPolylineOverlay(polylineInfo);`

**说明**

添加折线覆盖物

**参数**

| 参数名称         | 参数类型   | 是否必选 | 说明                       |
| ------------ | ------ | ---- | ------------------------ |
| polylineInfo | String | 是    | 添加到地图上的折线信息.该字符串为JSON格式: |

```
var polylineInfo={
	fillColor:,
	lineWidth:,
	property:
		[
			{
				longitude:"116.357428",
				latitude:"39.93923
			},
			{
				longitude:"116.347428",
				latitude:"39.89923"
			}
		]
	}
```

各字段含义如下

| 参数        | 参数类型   | 是否必须 | 说明                         |
| --------- | ------ | ---- | -------------------------- |
| fillColor | String | 是    | 折线颜色,支持格式:"#000","#000000" |
| lineWidth | Number | 是    | 折线线宽,单位:像素                 |
| property  | Array  | 是    | 连接点经纬度集合                   |
| longitude | Number | 是    | 连接点经度                      |
| latitude  | Number | 是    | 连接点纬度                      |

**返回值**

返回overlay覆盖物对象,如果添加失败返回为空

**示例**

```
var polylineInfo=
	{
	fillColor:"#990033",
	lineWidth:"10.0",
	property:
		[
			{
				longitude:"116.357428",
				latitude:"39.93923"
			},
			{
				longitude:"116.401394",
				latitude:"39.942821"
			},
			{
				longitude:"116.347428",
				latitude:"39.89923"
			}
		]
	};
var jsonStr=JSON.stringify(polylineInfo);
var overlay=uexBaiduMap.addPolylineOverlay(jsonStr);
if(!overlay){
	alert("添加失败");
}
```

### 📦 addArcOverlay 添加弧形覆盖物 

`uexBaiduMap.addArcOverlay(arcInfo);`

**说明**

添加弧形覆盖物

**参数**

| 参数名称    | 参数类型   | 是否必选 | 说明                       |
| ------- | ------ | ---- | ------------------------ |
| arcInfo | String | 是    | 添加到地图上的弧形信息.该字符串为JSON格式: |

```
var arcInfo={
	strokeColor:,
	lineWidth:,
	startLongitude:,
	startLatitude:,
	centerLongitude:,
	centerLatitude:,
	endLongitude:,
	endLatitude:
}
```

各字段含义如下

| 参数              | 参数类型   | 是否必须 | 说明                       |
| --------------- | ------ | ---- | ------------------------ |
| strokeColor     | String | 是    | 颜色,支持格式:"#000","#000000" |
| lineWidth       | Number | 是    | 线宽                       |
| startLongitude  | Number | 是    | 起点经度                     |
| startLatitude   | Number | 是    | 起点纬度                     |
| centerLongitude | Number | 是    | 中点经度                     |
| centerLatitude  | Number | 是    | 中点纬度                     |
| endLongitude    | Number | 是    | 终点经度                     |
| endLatitude     | Number | 是    | 终点纬度                     |

**返回值**

返回overlay覆盖物对象,如果添加失败返回为空

**示例**

```
var data={
	centerLatitude:"39.942821",
	centerLongitude:"116.369199",
	endLatitude:"39.906965",
	endLongitude:"116.401394",
	lineWidth:"2.0",
	startLatitude:"39.963175",
	startLongitude:"116.400244",
	strokeColor:"#990033"
};
var jsonStr=JSON.stringify(data)
var overlay=uexBaiduMap.addArcOverlay(jsonStr); 
if(!overlay){
	alert("添加失败");
}
```

### 📦 addCircleOverlay 添加圆形覆盖物 
> `uexBaiduMap.addCircleOverlay(circleInfo);`

**说明**

添加圆形覆盖物

**参数**

| 参数名称       | 参数类型   | 是否必选 | 说明                         |
| ---------- | ------ | ---- | -------------------------- |
| circleInfo | String | 是    | 添加到地图上的圆形覆盖物信息.该字符串为JSON格式 |

```
var circleInfo={
	longitude:,
	latitude:,
	radius:"1000",
	fillColor:"#4169E1",
	strokeColor:"#990033",
	lineWidth:"4"
}
```

各字段含义如下

| 参数          | 参数类型   | 是否必须 | 说明                         |
| ----------- | ------ | ---- | -------------------------- |
| radius      | Number | 是    | 半径,单位:米                    |
| fillColor   | String | 是    | 填充颜色,支持格式:"#000","#000000" |
| strokeColor | String | 是    | 边框颜色,支持格式:"#000","#000000" |
| lineWidth   | Number | 是    | 边框宽度                       |
| longitude   | Number | 是    | 圆心经度                       |
| latitude    | Number | 是    | 圆心纬度                       |

**返回值**

返回overlay覆盖物对象,如果添加失败返回为空

**示例**

```
var data={
	fillColor:"#4169E1",
	latitude:"39.915",
	lineWidth:"4",
	longitude:"116.404",
	radius:"1000",
	strokeColor:"#990033"
};
var jsonStr=JSON.stringify(data);
var overlay=uexBaiduMap.addCircleOverlay(jsonStr); 
if(!overlay){
	alert("添加失败");
}
```

### 📦 addPolygonOverlay 添加几何图形覆盖物 

`uexBaiduMap.addPolygonOverlay(polygonInfo);`

**说明**

添加几何图形覆盖物

**参数**

| 参数名称        | 参数类型   | 是否必选 | 说明                           |
| ----------- | ------ | ---- | ---------------------------- |
| polygonInfo | String | 是    | 添加到地图上的集合图形信息的集合.该字符串为JSON格式 |

```
var polygonInfo={
	fillColor:,
	strokeColor:,
	lineWidth:,
	property:
		[
			{
			longitude:,
			latitude:
			},
		]
}
```

各字段含义如下

| 参数          | 参数类型   | 是否必须 | 说明                         |
| ----------- | ------ | ---- | -------------------------- |
| fillColor   | String | 是    | 填充颜色,支持格式:"#000","#000000" |
| strokeColor | String | 是    | 边框颜色,支持格式:"#000","#000000" |
| lineWidth   | Number | 是    | 边框宽度                       |
| property    | Array  | 是    | 连接点经纬度数组                   |
| longitude   | Number | 是    | 连接点经度                      |
| latitude    | Number | 是    | 连接点纬度                      |

**返回值**

返回overlay覆盖物对象,如果添加失败返回为空

**示例**

```
var data={
	fillColor:"#990033",
	lineWidth:"2.0",
	property:[
		{
			latitude:"39.93923",
			longitude:"116.357428"
		},
		{
			latitude:"39.91923",
			longitude:"116.327428"
		},
		{
			latitude:"39.89923",
			longitude:"116.347428"
		},
		{
			latitude:"39.89923",
			longitude:"116.367428"
		}
	],
	strokeColor:"#990033"
};
var jsonStr=JSON.stringify(data)
var overlay=uexBaiduMap.addPolygonOverlay(jsonStr); 
if(!overlay){
	alert("添加失败");
}
```

### 📦 addGroundOverlay 添加地形图图层覆盖物 

`uexBaiduMap.addGroundOverlay(groundInfo);`

**说明**

添加地形图图层覆盖物

**参数**

| 参数名称       | 参数类型   | 是否必选 | 说明                            |
| ---------- | ------ | ---- | ----------------------------- |
| groundInfo | String | 是    | 添加到地图上的地形图图层信息.该字符串为JSON格式如下: |

```
var groundInfo={
	imageUrl:,
	transparency:,
	imageWidth:,
	imageHeight:,
	property:
		[
			{
				longitude:,
				latitude:
			}
		]
}
```

各字段含义如下

| 参数           | 参数类型   | 是否必须                                 | 说明                           |
| ------------ | ------ | ------------------------------------ | ---------------------------- |
| imageUrl     | String | 是                                    | 图片路径,支持格式:"http://","res://" |
| transparency | Number | 是                                    | 透明度,范围:[0.0f,1.0f]           |
| property     | Array  | 是                                    | 地理位置数组,长度为2                  |
| longitude    | Number | 是                                    | 经度                           |
| latitude     | Number | 是                                    | 纬度                           |
| imageWidth   | Number | 是(property数组长度为1时)否(property数组长度为2时) | 图片宽度,单位:米                    |
| imageHeight  | Number | 否                                    | 图片高度,单位:米                    |

**返回值**

返回overlay覆盖物对象,如果添加失败返回为空

**示例**

```
var data={
	imageHeight:"5000",
	imageUrl:"http://img0.bdstatic.com/img/image/9baf75d938553886ce515def29441ed31409109131.jpg",
	imageWidth:"10000",
	property:[
		{
			longitude:"116.380338",
			latitude:"39.92235"
		},
		{
			longitude:"116.414977",
			latitude:"39.947246"
		}
	],
	transparency:"0.8"
	};
var jsonStr=JSON.stringify(data)
var overlay=uexBaiduMap.addGroundOverlay(jsonStr);
if(!overlay){
	alert("添加失败");
}
```
### 📦 addTextOverlay 添加文字覆盖物 

`uexBaiduMap.addTextOverlay(textInfo);`

**说明**

添加文字覆盖物

**参数**

| 参数名称     | 参数类型   | 是否必选 | 说明                            |
| -------- | ------ | ---- | ----------------------------- |
| textInfo | String | 是    | 添加到地图上的文字覆盖物信息.该字符串为JSON格式如下: |

```
var textInfo = {
	bgColor:,
	fontSize:,
	fontColor:,
	text:,
	rotate:,
	longitude:,
	latitude:
}
```

各字段含义如下

| 参数        | 参数类型   | 是否必须 | 说明                              |
| --------- | ------ | ---- | ------------------------------- |
| bgColor   | String | 是    | 文字背景,支持格式:"#000","#000000"      |
| fontSize  | Number | 是    | 字体大小                            |
| fontColor | String | 是    | 字体颜色,支持格式:"#000","#000000"      |
| text      | String | 是    | 文字内容                            |
| longitude | Number | 是    | 经度                              |
| latitude  | Number | 是    | 纬度                              |
| rotate    | Number | 否    | 文字旋转角度(逆时针),旋转角范围:-180~180,单位:度 |

**返回值**

返回overlay覆盖物对象,如果添加失败返回为空

**示例**

```
var data={
	bgColor: "#FFFF00",
	fontSize: "24",
	longitude: "116.400244",
	latitude: "39.963175",
	rotate: "-30",
	text: "baidu map"
};
var jsonStr=JSON.stringify(data);
var overlay=uexBaiduMap.addTextOverlay(jsonStr);
if(!overlay){
	alert("添加失败");
}
```
### 📦 removemarkersOverlay 移除标注 

`uexBaiduMap.removemarkersOverlay(markers);`

**说明**

移除地图上对应标识的覆盖物

**参数**

| 参数      | 参数类型   | 是否必须 | 说明                           |
| ------- | ------ | ---- | ---------------------------- |
| markers | String | 是    | marker对象组成的数组结构字符串,json结构字符串 |


**示例**

```
 var markers ='[marker1, marker2]';
 uexBaiduMap.removemarkersOverlay(markers);
```

### 📦 removeOverlay 移除覆盖物 

`uexBaiduMap.removeOverlay(overlay);`

**说明**

移除地图上对应标识的覆盖物

**参数**

| 参数      | 参数类型   | 是否必须 | 说明                |
| ------- | ------ | ---- | ----------------- |
| overlay | String | 是    | 添加覆盖物返回的overlay对象 |


**示例**

```
 uexBaiduMap.removeOverlay(overlay);
```

### 📦 poiSearchInCity 城市内检索 

`uexBaiduMap.poiSearchInCity(json, callbackFunction);`

**说明**

根据单个关键字在指定城市内搜索兴趣点, 搜索完成后回调`callbackFunction`

**参数**

```
json:(String类型) 必选搜索所需要的信息.该字符串为JSON格式
var json={
	city:,
	searchKey:,
	pageNum:
}
```

各字段含义如下

| 参数        | 是否必须 | 说明    |
| --------- | ---- | ----- |
| city      | 是    | 城市    |
| searchKey | 是    | 关键字   |
| pageNum   | 是    | 结果页索引 |

**示例**

```
var data={
	city: "北京",
	searchKey: "114",
	pageNum: "0"
};
var jsonStr=JSON.stringify(data);
uexBaiduMap.poiSearchInCity(jsonStr, function(data) {
	alert(JSON.stringify(data));
});
```

`callbackFunction`的参数是JSON类型对象,其格式如下:

```
{
	totalPoiNum:,
	totalPageNum:,
	currentPageNum:,
	currentPageCapacity:,
	poiInfo:[
		{
			uid:,
			poiType:,
			phoneNum:,
			address:,
			name:,
			longitude:,
			latitude:,
			distance:,
			city:,
			postCode:
		}
	]
}
```

各字段含义如下

| 参数                  | 是否必须 | 说明                                    |
| ------------------- | ---- | ------------------------------------- |
| poiInfo             | 是    | POI信息集合                               |
| longitude           | 是    | 经度                                    |
| latitude            | 是    | 纬度                                    |
| distance            | 是    | 距离                                    |
| name                | 是    | 名称                                    |
| uid                 | 是    | 唯一标识符                                 |
| address             | 是    | 地址                                    |
| city                | 是    | 城市                                    |
| phoneNum            | 是    | 电话                                    |
| postCode            | 是    | 邮编                                    |
| poiType             | 是    | 类型(POI类型,0:普通点1:公交站2:公交线路3:地铁站4:地铁线路) |
| totalPoiNum         | 是    | 总结果数                                  |
| totalPageNum        | 是    | 总页数                                   |
| currentPageNum      | 是    | 当前页                                   |
| currentPageCapacity | 是    | 当前页的poi结果数                            |


### 📦 poiNearbySearch 周边检索 

`uexBaiduMap.poiNearbySearch(json, callbackFunction);`

**说明**

根据单个关键字在指定的中心点和半径范围内搜索兴趣点 

**参数**

```
json:(String类型) 必选搜索所需要的信息.该字符串为JSON格式
var json={
	longitude:,
	latitude:,
	radius:,
	searchKey:,
	pageNum:
}
```

各字段含义如下

| 参数        | 是否必须 | 说明      |
| --------- | ---- | ------- |
| longitude | 是    | 经度      |
| latitude  | 是    | 纬度      |
| radius    | 是    | 半径值,单位米 |
| searchKey | 是    | 关键字     |
| pageNum   | 是    | 结果页索引   |


**示例**

```
 var data ={
	longitude: "116.309",
	latitude: "39.977",
	radius: "1000",
	searchKey: "电影院",
	pageNum: "0"
	};
var jsonStr=JSON.stringify(data);
uexBaiduMap. poiNearbySearch (jsonStr, function(data) {
	alert(JSON.stringify(data));
});
```

`callbackFunction`的参数是JSON类型对象, 其格式同`poiSearchInCity`中的回调数据格式一致


### 📦 poiBoundSearch 区域检索

`uexBaiduMap.poiBoundSearch(json, callbackFunction);`

**说明**

根据单个关键字在指定的矩形区域内搜索兴趣点

**参数**

```
json:(String类型) 必选搜索所需要的信息.该字符串为JSON格式
var json={
	searchKey:,
	pageNum:,
	northeast:{
		longitude:,
		latitude:
	},
	southwest:{
		longitude:,
		latitude:
	}
}
```

各字段含义如下

| 参数        | 是否必须 | 说明    |
| --------- | ---- | ----- |
| searchKey | 是    | 关键字   |
| pageNum   | 是    | 结果页索引 |
| northeast | 是    | 东北点   |
| southwest | 是    | 西南点   |
| longitude | 是    | 经度    |
| latitude  | 是    | 纬度    |


**示例**

```
var data={
	searchKey: "电影院",
	pageNum: "0",
	northeast: {
		longitude: "116.326664",
		latitude: "39.991418"
	},
	southwest: {
		longitude: "116.312705",
		latitude: "39.981730"
	}
};
var jsonStr=JSON.stringify(data);
uexBaiduMap.poiBoundSearch(jsonstr, function(data) {
	alert(JSON.stringify(data));
});
```

`callbackFunction`的参数是JSON类型对象, 其格式同`poiSearchInCity`中的回调数据格式一致


### 📦 busLineSearch 公交线路检索

`uexBaiduMap.busLineSearch(json, callbackFunction);`

**说明**

根据公交线路编号在指定城市范围内搜索公交线路详情, 搜索完成后执行回调函数`callbackFunction`

**参数**

```
json:(String类型) 必选索所需要的信息.该字符串为JSON格式.
var json={
	city:,
	busLineName:
}
```

各字段含义如下

| 参数          | 是否必须 | 说明   |
| ----------- | ---- | ---- |
| city        | 是    | 城市   |
| busLineName | 是    | 公交名  |

`callbackFunction`中的参数类型是JSON对象,格式如下:

```
{
	busLineName:,
	busCompany:,
	startTime:,
	endTime:,
	busStation:[
		{
			title:"史各庄(辛庄桥西)",
			longitude:116.297604,
			latitude:40.099629
		}
	]
}
```

各字段含义如下

| 参数          | 是否必须 | 说明       |
| ----------- | ---- | -------- |
| busLineName | 是    | 公交线路名称   |
| busCompany  | 是    | 公交线路所属公司 |
| startTime   | 是    | 首班时间     |
| endTime     | 是    | 末班时间     |
| busStation  | 是    | 站点信息列表   |
| longitude   | 是    | 站点的经度    |
| latitude    | 是    | 站点的纬度    |
| title       | 是    | 站点的名称    |


**示例**

```
var data={
	city: "北京",
	busLineName: "114"
};
var jsonStr=JSON.stringify(data);
uexBaiduMap.busLineSearch(jsonStr, function(data) {
	alert(JSON.stringify(data));
});
```

### 📦 removeBusLine 清除公交线路

`uexBaiduMap.removeBusLine();`

**说明**

清除公交线路

**参数**

无

**示例**

```
uexBaiduMap.removeBusLine(); 
```

### 📦 preBusLineNode 显示上一个公交站点 

`uexBaiduMap.preBusLineNode();`

**说明**

显示公交线路中当前站点的上一个站点,起始站点无效, 该方法仅Android支持.

**参数**

无


**示例**

```
uexBaiduMap.preBusLineNode();
```

### 📦 nextBusLineNode 显示下一个公交站点 

`uexBaiduMap.nextBusLineNode();`

**说明**

显示公交线路中当前站点的下一个站点,终点站点无效,该方法仅Android支持.

**参数**

无


**示例**

```
uexBaiduMap.nextBusLineNode(); 
```

### 📦 searchRoutePlan 规划并显示路线 

`uexBaiduMap.searchRoutePlan(json);`

**说明**

根据起点和终点信息搜索并显示路线,信息可以用city和name结合模糊描述,也可以用longitude和latitude结合精确描述,在start和end里面可以出现任意一种结合方式.

**参数**

```
json:(String类型) 必选规划路线所需要的信息.该字符串为JSON格式.
var json={
	type:,
	start:{
		city:,
		name:,
		longitude:,
		latitude:
	},
	end:{
		city:,
		name:,
		longitude:,
		latitude:
	}
}
```
各字段含义如下

| 参数        | 是否必须 | 说明                  |
| --------- | ---- | ------------------- |
| type      | 是    | 路线类型:0-驾车;1-公交;2-步行 |
| start     | 是    | 起点信息,JSON格式         |
| end       | 是    | 终点信息,JSON格式         |
| city      | 否    | 城市,必须与name合用        |
| name      | 否    | 地址                  |
| longitude | 否    | 经度,必须与latitude合用    |
| latitude  | 否    | 纬度                  |

callbackFunction的参数是errorCode, 其数据含义如下:

| 错误码  | 说明               |
| ---- | ---------------- |
| 0    | 检索结果正常返回         |
| 1    | 检索词有岐义           |
| 2    | 检索地址有岐义          |
| 3    | 该城市不支持公交搜索       |
| 4    | 不支持跨城市公交         |
| 5    | 没有找到检索结果         |
| 6    | 起终点太近            |
| 7    | key错误            |
| 8    | 网络连接错误           |
| 9    | 网络连接超时           |
| 10   | 还未完成鉴权,请在鉴权通过后重试 |
| 11   | 室内图ID错误          |
| 12   | 室内图检索楼层错误        |

**返回值**

成功返回这条路线规划对象,失败为空

**示例**

```
var data = {
	type: "0",
	start: {
		city: "北京",
		name: "天安门"
	},
	end:{
		city: "北京",
		name: "百度大厦",
		longitude: "116.307827",
		latitude: "40.056957"
	}
};
var jsonStr=JSON.stringify(data);
var req=uexBaiduMap.searchRoutePlan(jsonStr);
if(!req){
	alert("规划失败");
}
```

### 📦 preRouteNode 显示上一个线路节点 

`uexBaiduMap.preRouteNode();`

**说明**

显示线路规划中当前节点的上一个节点,起始节点无效,该方法仅Android支持.

**参数**

无

**示例**

```
 uexBaiduMap.preRouteNode(); 
```

### 📦 removeRoutePlan 清除线路规划 

`uexBaiduMap.removeRoutePlan(req);` 

**说明**

清除线路规划

**参数**

| 参数   | 参数类型   | 是否必须 | 说明                                       |
| ---- | ------ | ---- | ---------------------------------------- |
| req  | Object | 是    | 这条路线规划对象,由[searchRoutePlan](# searchRoutePlan 规划并显示路线)返回 |


**示例**

```
var req=...;//这条路线规划对象, searchRoutePlan返回
 uexBaiduMap.removeRoutePlan(req);
```

### 📦 nextRouteNode 显示下一个线路节点

`uexBaiduMap.nextRouteNode();`

**说明**

 显示线路规划中当前节点的下一个节点,终点节点无效,该方法仅Android支持.

**参数**

无


**示例**

```
 uexBaiduMap.nextRouteNode();
```
### 📦 geocode 地理编码 

`uexBaiduMap.geocode(json, callbackFunction)`

**说明**

根据地址获取经纬度信息, 执行完成后,回调`callbackFunction`.

**参数**

```
json:(String类型) 必选地址该字符串为JSON格式
var json={
	city:,
	address:
}
```

各字段含义如下

| 参数      | 是否必须 | 说明   |
| ------- | ---- | ---- |
| city    | 是    | 城市   |
| address | 是    | 地址   |

`callbackFunction`的参数是JSON对象, 其数据格式如下:
```
{
    longitude:,
    latitude:
}
```

**示例**

```
var data=
{
	city: "北京",
	address: "东长安街33号"
};

uexBaiduMap.geocode(jsonstr, function(data) {
	alert(JSON.stringify(data));
});
```

### 📦 reverseGeocode 反地理编码 

`uexBaiduMap.reverseGeocode(json, callbackFunction)`

**说明**

根据经纬度获取地址信息, 执行完成后回调`callbackFunction`.

**参数**

```
json:(String类型) 必选经纬度该字符串为JSON格式.如下{longitude:"116.307827",latitude:"40.056957"}
```

各字段含义如下

| 参数        | 是否必须 | 说明   |
| --------- | ---- | ---- |
| longitude | 是    | 经度   |
| latitude  | 是    | 纬度   |

`callbackFunction`的参数是JSON对象,其数据格式如下:
```
{
	address://地理位置信息
}
```

**示例**

```
var data={
	longitude: "116.307827",
	latitude: "40.056957"
};
var jsonStr=JSON.stringify(data);
uexBaiduMap.reverseGeocode(jsonStr, function(data) {
	alert(data.address);
});
```

### 📦 getCurrentLocation 获取当前位置 

`uexBaiduMap.getCurrentLocation(callbackFunction)`

**说明**

获取当前的位置信息,仅定位一次,执行完成后回调`callbackFunction`.

**参数**

`callbackFunction`函数的参数是JSON对象,其数据格式如下:

```
{
    longitude:, //经度
    latitude:,  //纬度
    timestamp:  //时间,格式如"2014-11-2217:46:37"
}
```


**示例**

```
 uexBaiduMap.getCurrentLocation(function(data){
	 alert(JSON.stringify(data));
 }); 
```

### 📦 startLocation 开始连续定位 

`uexBaiduMap.startLocation()` 

**说明**

开始连续定位

**参数**

 无 


**示例**

```
 uexBaiduMap.startLocation(); 
```

### 📦 stopLocation 停止连续定位 

`uexBaiduMap.stopLocation()`

**说明**

停止连续定位

**参数**

 无 


**示例**

```
 uexBaiduMap.stopLocation(); 
```

### 📦 setMyLocationEnable 显示或隐藏用户位置 

`uexBaiduMap.setMyLocationEnable(type)`

**说明**

显示或隐藏用户位置

**参数**

| 参数   | 参数类型   | 是否必须 | 说明                   |
| ---- | ------ | ---- | -------------------- |
| type | Number | 是    | 显示或隐藏用户位置(0-隐藏,1-显示) |

**示例**

```
 uexBaiduMap.setMyLocationEnable(1); 
```

### 📦 setUserTrackingMode 设置跟踪模式 

`uexBaiduMap.setUserTrackingMode(mode)`

**说明**

设置定位时的跟踪模式

**参数**

| 参数   | 参数类型   | 是否必须 | 说明                                      |
| ---- | ------ | ---- | --------------------------------------- |
| mode | Number | 是    | 跟踪模式(0-----普通定位模式,1-----跟随模式,2-----罗盘模式 |


**示例**

```
 uexBaiduMap.setUserTrackingMode(0); 
```

### 📦 zoomControlsEnabled 显示或隐藏缩放控件 

`uexBaiduMap.zoomControlsEnabled(mode)`

**说明**

显示或隐藏缩放控件

**参数**

| 参数   | 参数类型   | 是否必须 | 说明              |
| ---- | ------ | ---- | --------------- |
| mode | Number | 是    | 控件状态(0—隐藏,1—显示) |

**示例**

```
uexBaiduMap.zoomControlsEnabled(0) 
```

### 📦 getDistance 计算两点之间的距离 

`uexBaiduMap.getDistance(lat1,lon1,lat2,lon2)`

**说明**

通过经纬度计算两点之间的距离,返回值是Number类型

**参数**

| 参数   | 参数类型   | 是否必须 | 说明      |
| ---- | ------ | ---- | ------- |
| lat1 | Number | 是    | 第一个坐标纬度 |
| lon1 | Number | 是    | 第一个坐标经度 |
| lat2 | Number | 是    | 第二个坐标纬度 |
| lon2 | Number | 是    | 第二个坐标经度 |


**示例**

```
var distance = uexBaiduMap.getDistance(lat1,lon1,lat2,lon2);
```

## 2.2、监听方法<ignore>

### 📦 onMapClickListener 点击地图的监听方法 

`uexBaiduMap.onMapClickListener(data)`

**参数**

```
data:(String类型) 必选 经纬度,该字符串为JSON格式
var data={
	longitude:,
	latitude:
}
```

各字段含义如下

| 参数        | 是否必须 | 说明   |
| --------- | ---- | ---- |
| longitude | 是    | 经度   |
| latitude  | 是    | 纬度   |


### 📦 onMapDoubleClickListener 双击地图的监听方法

`uexBaiduMap.onMapDoubleClickListener(data)`

**参数**

同onMapClickListener


### 📦 onMapLongClickListener 长按地图的监听方法 

`uexBaiduMap.onMapLongClickListener(data)`

**参数**

同onMapClickListener


### 📦 onMapStatusChangeListener 地图状态改变的监听方法

`uexBaiduMap.onMapStatusChangeListener(json);`

**参数**

```
var json = {
	center: { // 地图中心点改变时返回值,回调改变后的中心点坐标
		longitude:, //经度
		latitude:  //纬度
	},
	zoom:{ // 地图缩放级别改变时返回值,回调改变前后的缩放级别
		oldZoom:, // 地图状态改变前的缩放级别
		newZoom: // 地图状态改变后的缩放级别
	}
	overlook: {//地图倾斜度改变时返回值,回调改变前后的倾斜度
		oldOverlook:, // 地图状态改变前的倾斜度
		newOverlook: // 地图状态改变后的倾斜度
	},
	northeast: {//地图东北角坐标改变时返回值,回调改变后的东北角坐标值
		longitude:, // 经度
		latitude: // 纬度
	},
	southwest: {//地图西南角坐标改变时返回值,回调改变后的西南角坐标值
		longitude:, // 经度
		latitude: // 纬度
	},
	rotate: {//地图旋转角度改变时返回值,回调改变前后的旋转角度
		oldRotate:, // 地图状态改变前的旋转角度
		newRotate: // 地图状态改变后的旋转角度
	}
}
```


**示例**

```
uexBaiduMap.onMapStatusChangeListener = function(data){
	alert(data);
}
```
### 📦 onMarkerClickListener 点击标注的监听方法 

`uexBaiduMap.onMarkerClickListener(markerId)`

**参数**

| 参数       | 参数类型   | 是否必须 | 说明    |
| -------- | ------ | ---- | ----- |
| markerId | Number | 是    | 标注的ID |


**示例**

```
uexBaiduMap.onMarkerClickListener = function(data){
	alert(data);
}
```
### 📦 onMarkerBubbleClickListener 点击标注气泡的监听方法

`uexBaiduMap.onMarkerBubbleClickListener(markerId)`

**参数**

| 参数       | 参数类型   | 是否必须 | 说明    |
| -------- | ------ | ---- | ----- |
| markerId | Number | 是    | 标注的ID |


**示例**

```
uexBaiduMap.onMarkerBubbleClickListener = function(data){
	alert(data);
}
```

### 📦 onSDKReceiverError 初始化地图时,key非法、网络错误时的监听方法

`uexBaiduMap.onSDKReceiverError(data)`

**参数**

```
data:(String类型) 必选 失败信息  该字符串为JSON格式
var data={
	errorInfo://失败信息
}
```

**示例**

```
uexBaiduMap.onSDKReceiverError = function(data){
	alert(data);
}
```
### 📦 onReceiveLocation 开始定位后的监听方法 

`uexBaiduMap.onReceiveLocation(data)`

**参数**

```
data:(String类型) 必选 位置信息该字符串为JSON格式
var data={
	longitude:,
	latitude:,
	timestamp:
}
```

各字段含义如下

| 参数        | 是否必须 | 说明                         |
| --------- | ---- | -------------------------- |
| longitude | 是    | 经度                         |
| latitude  | 是    | 纬度                         |
| timestamp | 是    | 时间戳 "2014-11-2217:46:37"格式 |

**示例**

```
uexBaiduMap.onReceiveLocation = function(data){
	alert(data);
}
```

### 📦 onSearchRoutePlan 线路规划搜索结果的监听

`uexBaiduMap.onSearchRoutePlan(id)`

**参数**

 id:(Number类型) 必选 线路规划id.

### 📦 onZoomLevelChangeListener 缩放级别改变时,获取缩放级别和中心点的监听方法 

`uexBaiduMap.onZoomLevelChangeListener(level,latitude,longitude)`

**参数**

```
level:(Number类型) 必选 缩放级别
latitude:(Number类型) 必选 中心点纬度
longitude:(Number类型) 必选 中心点经度
```

**示例**

```
uexBaiduMap.onZoomLevelChangeListener = function(data){
	alert(data);
}
```

# 3、更新历史<ignore>

### iOS<ignore>

API版本:`uexBaiduMap-4.0.0`

最近更新时间:`2016-6-13`

| 历史发布版本 | 更新内容                                     |
| ------ | ---------------------------------------- |
| 4.0.0  | 支持function传入                             |
| 3.1.17 | 修复removemarkersOverlay接口传不当参数会闪退的问题      |
| 3.1.16 | 增加对多种类型参数的识别,支持3.3引擎                     |
| 3.0.15 | 修改插件,使其支持config配置APIKey                  |
| 3.0.14 | 删去info.plist                             |
| 3.0.13 | 国际化                                      |
| 3.0.12 | 修复onMapLongClickListener回调结果异常的bug       |
| 3.0.11 | 修改uexBaiduMap.plist文件NSLocation WhenInUseUsageDescription字段对应value 的类型为字符串 |
| 3.0.10 | 新增onMarkerClickListener和onMarker BubbleClickListener监听方法 |
| 3.0.9  | 增加onZoomLevelChangeListener地图缩放 级别 改变时,获取缩放级别和中心点的监听 |
| 3.0.8  | 增加隐藏地图hideMap和显示地图showMap的接 口            |
| 3.0.7  | 修复onMapClickListener和onMapDoubleClick Listener的回调错误, 添加cbOpen方法,添加onSearchRoutePlan方法 |
| 3.0.6  | 修复手势问题                                   |
| 3.0.5  | 修复新SDK定位失败问题                             |
| 3.0.4  | 更新百度地图iOS_SDK_2.6.0                      |
| 3.0.3  | 修复公交路线搜索失败的问题                            |
| 3.0.2  | 修复cbPoiSearchResult接口回调信息不完整问题           |
| 3.0.1  | 与安卓统一回调接口的参数                             |
| 3.1.0  | 百度地图iOS_SDK_2.5.0                        |

### Android<ignore>

API版本:`uexBaiduMap-4.0.0`

最近更新时间:`2016-06-13`

| 历史发布版本 | 更新内容                                     |
| ------ | ---------------------------------------- |
| 4.0.0  | 支持function传入                             |
| 3.2.37 | 更新SDK,增加getCenter得到地图中心点方法               |
| 3.2.36 | 优化了getDistance的算法,使用新版本SDK自带工具类DistanceUtil进行计算,使计算值更为精准 |
| 3.2.35 | 更新SDK后appkey验证广播机制改变,由于onSDKReceiverError回调只为前端开发者所提供,所以使用Toast替代 |
| 3.2.34 | 修复了getCurrentLocation必须open才能使用的问题;修复了地理编码、反地理编码必须open才能使用的问题 |
| 3.2.33 | 更新SDK版本,将百度地图所有库导入                       |
| 3.2.32 | 增加了getDistance得到两点间直线距离方法,在回调方法cbPoiSearchResult中增加distance字段,返回距离;修复了文档中cbGetDistance代码case说明不对的问题 |
| 3.2.31 | 增加了,当不打开地图View时,也可以调用poi搜索功能(目前支持城市检索,周边检索,区域检索),修复了打开地图再关闭地图,搜索poi无效的问题 |
| 3.2.30 | 修复了前端调用open方法时传入小数时抛出NumberFormatException的问题 |
| 3.2.29 | 修复了持续定位时cbCurrentLocation回调不生效的问题        |
| 3.2.28 | 修复open接口传入的中心点不生效的问题                     |
| 3.2.27 | 修改插件,使其支持config配置APIKey                  |
| 3.2.26 | 去掉插件中的ActivityGroup,配合引擎升级               |
| 3.1.25 | 国际化                                      |
| 3.1.24 | 修改百度地图中引用的jar包,解除与百度导航插件之间的打包冲突问题        |
| 3.1.23 | 修复地理编码接口当地址错误时程序崩溃的问题                    |
| 3.1.22 | 修复加入百度地图插件后uexLocation.openLocation()中的onchange事件不能使用问题 |
| 3.1.21 | 规避百度地图SDK的BitmapDescriptorFactory中fromView方法重复调用crash问题 |
| 3.1.20 | 修复点击路径规划中的起终点标注时,应用崩溃的问题                 |
| 3.1.19 | 解决百度地图上箭头不转动的问题                          |
| 3.1.18 | 增加onMapStatusChangeListener监听方法监听地图状态改变,以及添加标注时增加气泡属性 |
| 3.0.17 | 修复打开百度地图闪黑屏问题                            |
| 3.0.16 | 增加onMarkerClickListener和onMarkerBubbleClickListener接口 |
| 3.0.15 | 增加onZoomLevelChangeListener地图缩放级别改变时,获取缩放级别和中心点的监听 |
| 3.0.14 | 增加zoomControlsEnabled显示或隐藏缩放控件           |
| 3.0.13 | 增加hideMap(隐藏地图)和showMap(显示地图)的接口         |
| 3.0.12 | 修改添加相同url标注,标注不显示的问题                     |
| 3.0.11 | 修改cbOpen和onSearchRoutePlan的JS回调方式        |
| 3.0.10 | 增加加载地图完成的cbOpen回调和线路规划搜索结果返回时的监听onSearchRoutePlan |
| 3.0.9  | 移动插件包中的定位jar包和so文件至引擎中                   |
| 3.0.8  | 修改在百度地图窗口打开新窗口报错问题                       |
| 3.0.7  | 修改获取当前位置时返回结果错误问题                        |
| 3.0.6  | 增加setUserTrackingMode接口                  |
| 3.0.5  | 修改点击显示线路和添加标注按钮无反应问题                     |
| 3.0.4  | 修改点击标注空指针异常问题                            |
| 3.0.3  | 修改地理编码和反地理编码JSON回调方法名称                   |
| 3.0.2  | 添加标注支持网络图片的功能                            |
| 3.0.1  | 增加清除公交线路和清除线路规划接口                        |
| 3.0.0  | 百度地图插件,封装最新的百度地图API                      |
