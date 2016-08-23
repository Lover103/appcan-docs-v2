/*
Sort: 1
Toc: 1
*/

[TOC]
# 1、简介 [![](http://appcan-download.oss-cn-beijing.aliyuncs.com/%E5%85%AC%E6%B5%8B%2Fgf.png)]() <ignore>
列表插件
## 1.1、说明<ignore>
Listview下拉列表,封装Listview扩展功能,AppCan官方 jssdk进一步对其扩展,封装了Listview列表组件:通过配合的样式,使开发者在界面中可以快速完成列表控件的开发
optionList带操作选项的列表组件:实现列表项可向左滑动后右侧显示隐藏内容,点击可进行自定义操作
## 1.2、UI展示<ignore>
 ![](http://newdocx.appcan.cn/docximg/134401c2015r6g16s.jpg)
## 1.3、开源源码<ignore>
插件测试用例与源码下载:[点击](http://plugin.appcan.cn/details.html?id=317_index) 插件中心至插件详情页 (插件测试用例与插件源码已经提供)

# 2、API概览<ignore>

## 2.1、方法<ignore>
### 📦 open 打开listview

`uexListView.open(params);`

**说明:**

在界面的指定位置显示listview.

**参数:**

```
var params = {
    x:,//必选,x坐标
    y:,//必选,y坐标
    w:,//必选,宽度
    h://必选,高度
}
```

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    var params = {
        "x": 0,
        "y": 100,
        "w":250,
        "h":400
    };
    uexListView.open(JSON.stringify(params));
```
### 📦 close 关闭listview视图

`uexListView.close();`

**说明:**

关闭listview视图

**参数:**

  无

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    uexListView.close();
```

### 📦 setItems 设置listview列表项数据

`uexListView.setItems(params);`

**说明:**

设置listview列表项数据,首次加载setItems必须在open之前
图片路径支持 wgt:// wgts:// res:// file://  路径协议详见[CONSTANT](http://newdocx.appcan.cn/newdocx/docx?type=978_975#Path Types "CONSTANT")中 PathTypes 

**参数:**

  params:(String类型) 必选listview每一个条目数据的集合.该字符串为JSON格式.如下:

```
var params = {
    "listItems":[//必选,listview列表项数据数组
        {
            "image":,//必选,列表项头像
            "placeholderImg":,//可选,头像占位图片
            "title":,//必选,标题
            "subtitle":,//必选,子标题
            "rightBtnImg":,//可选,右侧按钮图片.(暂不支持)
            "titleSize":,//可选,标题字体大小
            "titleColor":,//可选,标题字体颜色
            "subtitleSize":,//可选,子标题字体大小
            "subtitleColor":,//可选,子标题字体颜色
            "selectedBackgroundColor":,//可选,选中背景色
            "backgroundColor":,//可选,背景色
            "height"://可选,列表项高度
        }
    ],
    "rightSwipeOptionItem":{//可选,左滑右边的按钮
        "backgroundColor":,//可选,按钮所在列表项背景色
        "optionBtn":[//必选,左右按钮数据数组
            {
                "btnIndex":,//必选,按钮唯一标识
                "text":,//必选,按钮文本
                "textColor":,//可选,按钮文本颜色
                "textSize":,//可选,按钮文本大小
                "bgColor"://可选,按钮背景色
            }
        ]
    },
    "leftSwipeOptionItem":{//可选,右滑左边的按钮
        "backgroundColor":,//可选,按钮所在列表项背景色
        "optionBtn":[//必选,左右按钮数据数组
            {
                "btnIndex":,//必选,按钮唯一标识
                "text":,//必选,按钮文本
                "textColor":,//可选,按钮文本颜色
                "textSize":,//可选,按钮文本大小
                "bgColor"://可选,按钮背景色
            }
        ]
    }
};
```

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    var params = {
        "listItems":[
            {
                "image": "res://icon.png",
                "placeholderImg":"res://icon.png",
                "title": "标题",
                "subtitle":"子标题",
                "rightBtnImg": "res://ac_title_btn_hov.png",
                "titleSize": 10,
                "titleColor":"#006000",
                "subtitleSize": 10,
                "subtitleColor":"#000000",
                "selectedBackgroundColor":"#006000",
                "backgroundColor":"#FFFFFF",
                "height":100
            }
        ],
        "rightSwipeOptionItem":{
            "backgroundColor":"#ffffff",
            "optionBtn":[
                {
                    "btnIndex": "1",
                    "text": "分享",
                    "textColor":"#ffffff",
                    "textSize":10,
                    "bgColor":"#6F00D2"
                }
            ]
        },
        "leftSwipeOptionItem":{
            "backgroundColor":"#ffffff",
            "optionBtn":[
                {
                    "btnIndex": "1",
                    "text": "分享",
                    "textColor":"#ffffff",
                    "textSize":10,
                    "bgColor":"#6F00D2"
                }
            ]
        }
    };
    uexListView.setItems(JSON.stringify(params));
```
### 📦 deleteItemsAt 删除指定位置的数据

`uexListView.deleteItemsAt(params);`

**说明:**

删除指定位置的数据

**参数:**

  params:(String类型) 必选listview列表项索引的数组.该字符串为JSON格式,如下:

```
var params = {
    "itemIndex":[]//必选,列表项的位置索引集合
};
```

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    var params = {
        "itemIndex":[0, 1]
    };
    uexListView.deleteItemsAt(JSON.stringify(params));
```

### 📦 insertItemAt 插入数据到指定位置

`uexListView.insertItemAt(params);`
图片路径支持 wgt:// wgts:// res:// file://  路径协议详见[CONSTANT](http://newdocx.appcan.cn/newdocx/docx?type=978_975#Path Types "CONSTANT")中 PathTypes 

**说明:**

插入数据到指定位置

**参数:**

  params:(String类型) 必选要插入listview数据的集合.该字符串为JSON格式,如下:

```
var params ={
    "itemIndex":1,//必选,要插入的位置索引
    "item":{//必选,数据
        "image": ,//必选,列表项头像
        "placeholderImg":,//可选,头像占位图片
        "title":,//必选,标题
        "subtitle":,//必选,子标题
        "rightBtnImg":",//可选,右侧按钮图片.(暂不支持)
        "titleSize":,//可选,标题字体大小
        "titleColor":,//可选,标题字体颜色
        "subtitleSize":,//可选,子标题字体大小
        "subtitleColor":,//可选,子标题字体颜色
        "selectedBackgroundColor":,//可选,选中背景色
        "backgroundColor":,//可选,背景色
        "height"://可选,列表项高度
    }
};
```

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    var params ={
        "itemIndex":1,
        "item":{
            "image": "res://icon.png",
            "placeholderImg":"res://1Normal.png",
            "title": "标题",
            "subtitle":"子标题",
            "rightBtnImg": "res://ac_title_btn_hov.png",
            "titleSize": 10,
            "titleColor":"#006000",
            "subtitleSize": 10,
            "subtitleColor":"#000000",
            "selectedBackgroundColor":"#006000",
            "backgroundColor":"#FFFFFF",
            "height":100
        }
    };
    uexListView.insertItemAt(JSON.stringify(params));
```
### 📦 appendItems 加载数据

`uexListView.appendItems(params)`
图片路径支持 wgt:// wgts:// res:// file://  路径协议详见[CONSTANT](http://newdocx.appcan.cn/newdocx/docx?type=978_975#Path Types "CONSTANT")中 PathTypes 

**说明:**

加载数据到listview尾部

**参数:**

  params:(String类型) 必选要插入listview列表项数据的集合.该字符串为JSON格式,如下:

```
var params = {
    "listItems":[//必选,listview列表项数据数组
        {
            "image":,//必选,列表项头像
            "placeholderImg":,//可选,头像占位图片
            "title":,//必选,标题
            "subtitle":,//必选,子标题
            "rightBtnImg":,//可选,右侧按钮图片.(暂不支持)
            "titleSize":,//可选,标题字体大小
            "titleColor":,//可选,标题字体颜色
            "subtitleSize":,//可选,子标题字体大小
            "subtitleColor":,//可选,子标题字体颜色
            "selectedBackgroundColor":,//可选,选中背景色
            "backgroundColor":,//可选,背景色
            "height"://可选,列表项高度
        }
    ]
};
```

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    var params = {
        "listItems":[
            {
                "image": "res://icon.png",
                "placeholderImg":"res://1Normal.png",
                "title": "标题",
                "subtitle":"子标题",
                "rightBtnImg": "res://ac_title_btn_hov.png",
                "titleSize": 20,
                "titleColor":"#006000",
                "subtitleSize": 10,
                "subtitleColor":"#000000",
                "selectedBackgroundColor":"#006000",
                "backgroundColor":"#FFFFFF",
                "height":100
            }
        ]
    };
    uexListView.appendItems(JSON.stringify(params));
```
### 📦 reloadItems 刷新数据

`uexListView.reloadItems(params)`
图片路径支持 wgt:// wgts:// res:// file://  路径协议详见[CONSTANT](http://newdocx.appcan.cn/newdocx/docx?type=978_975#Path Types "CONSTANT")中 PathTypes 

**说明:**

刷新listview,清除当前数据,加载新数据

**参数:**

 params:(String类型) 必选要刷新数据的集合.该字符串为JSON格式,如下:
```
var params = {
    "listItems":[//必选,listview列表项数据数组
        {
            "image":,//必选,列表项头像
            "placeholderImg":,//可选,头像占位图片
            "title":,//必选,标题
            "subtitle":,//必选,子标题
            "rightBtnImg":,//可选,右侧按钮图片.(暂不支持)
            "titleSize":,//可选,标题字体大小
            "titleColor":,//可选,标题字体颜色
            "subtitleSize":,//可选,子标题字体大小
            "subtitleColor":,//可选,子标题字体颜色
            "selectedBackgroundColor":,//可选,选中背景色
            "backgroundColor":,//可选,背景色
            "height"://可选,列表项高度
        }
    ]
};
```

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    var params = {
        "listItems":[
            {
                "image": "res://icon.png",
                "placeholderImg":"res://1Normal.png",
                "title": "标题",
                "subtitle":"子标题",
                "rightBtnImg": "res://ac_title_btn_hov.png",
                "titleSize": 20,
                "titleColor":"#006000",
                "subtitleSize": 10,
                "subtitleColor":"#000000",
                "selectedBackgroundColor":"#006000",
                "backgroundColor":"#FFFFFF",
                "height":100
            }
        ]
    };
    uexListView.reloadItems(JSON.stringify(params));
```

### 📦 setItemSwipeType 设置侧滑类型

`uexListView.setItemSwipeType(type);`

**说明:**

  设置listview侧滑类型.
  

**参数:**

 
|  参数名称 | 参数类型  | 是否必选  |  说明 |
| ----- | ----- | ----- | ----- |
| type | Number | 是 | 侧滑类型值,取值范围参考[SwipeType](#SwipeType) |

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    uexListView.setItemSwipeType(2);
```

### 📦 setPullRefreshHeader 设置下拉刷新样式

`uexListView.setPullRefreshHeader(params);`

**说明:**

设置listview下拉刷新样式.
图片路径支持 wgt:// wgts:// res:// file://  路径协议详见[CONSTANT](http://newdocx.appcan.cn/newdocx/docx?type=978_975#Path Types "CONSTANT")中 PathTypes 

**参数:**

```
var params ={
    PullRefreshHeaderStyle:{//必选,下拉刷新样式集合
        "arrowImage":,//可选,下拉图片
        "backGroundColor":,//可选,下拉背景色
        "textColor":,//可选,字体颜色
        "textFontSize":,//可选,字体大小
        "pullRefreshNormalText":,//必选,下拉时文本
        "pullRefreshPullingText":,//必选,松开时文本
        "pullRefreshLoadingText":,//必选,加载中文本
        "isShowUpdateDate"://必选,是否显示更新日期(0:不显示,1:显示).安卓和ios格式不一样
    }
};
```

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    var params ={
        PullRefreshHeaderStyle:{
            "arrowImage":"res://1Normal.png",
            "backGroundColor":"#e2e7ed",
            "textColor":"#576c89",
            "textFontSize":20,
            "pullRefreshNormalText":"下拉可以刷新",
            "pullRefreshPullingText":"松开即可刷新",
            "pullRefreshLoadingText":"加载中...",
            "isShowUpdateDate":1
        }
    };
    uexListView.setPullRefreshHeader(JSON.stringify(params));
```

### 📦 setPullRefreshFooter 设置上拉加载样式

`uexListView.setPullRefreshFooter(params);`

**说明:**

设置listview上拉加载样式.
图片路径支持 wgt:// wgts:// res:// file://  路径协议详见[CONSTANT](http://newdocx.appcan.cn/newdocx/docx?type=978_975#Path Types "CONSTANT")中 PathTypes 

**参数:**

  params:(String类型) 必选加载样式的集合.该字符串为JSON格式,如下:

```
var params ={
    PullRefreshFooterStyle:{//必选,上拉加载样式集合
        "arrowImage":,//可选,上拉图片
        "backGroundColor":,//可选,上拉背景色
        "textColor":,//可选,字体颜色
        "textFontSize":,//可选,字体大小
        "pullRefreshNormalText":,//必选,上拉时文本
        "pullRefreshPullingText":,//必选,松开时文本
        "pullRefreshLoadingText":,//必选,加载中文本
        "isShowUpdateDate"://必选,是否显示日期(0:不显示,1:显示).
    }
};
```

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    var params ={
        PullRefreshFooterStyle:{
            "arrowImage":"res://1Normal.png",
            "backGroundColor":"#e2e7ed",
            "textColor":"#576c89",
            "textFontSize":13,
            "pullRefreshNormalText":"上拉加载更多",
            "pullRefreshPullingText":"松开即可加载更多",
            "pullRefreshLoadingText":"加载中...",
            "isShowUpdateDate":1
        }
    };
    uexListView.setPullRefreshFooter(JSON.stringify(params));
```
## 2.2、监听方法<ignore>

### 📦 onItemClick 点击列表项的监听方法

`uexListView.onItemClick(itemIndex);`

**说明:**

点击列表项的监听方法.

**参数:**

|参数名称|参数类型|是否必选|说明|
|-----|-----|-----|-----|
|itemIndex|Number|是|被点击列表项的索引|

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    uexListView.onItemClick = function(itemIndex){
        alert("onItemClick:" + itemIndex);
    };
```

### 📦 onLeftOptionButtonInItem 点击左边按钮的监听方法

`uexListView.onLeftOptionButtonInItem(itemIndex,optionBtnIndex);`

**说明:**

点击左边按钮的监听方法.

**参数:**

|参数名称|参数类型|是否必选|说明|
|-----|-----|-----|-----|
|itemIndex|Number|是|被点击按钮所在列表项的索引|
|optionBtnIndex|Number|是|被点击按钮的索引|

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    uexListView.onLeftOptionButtonInItem = function(itemIndex, optionBtnIndex){
        alert("onLeftOptionButtonInItem:" + itemIndex + "," + optionBtnIndex);
    };
```

### 📦 onRightOptionButtonInItem 点击右边按钮的监听方法

`uexListView.onRightOptionButtonInItem(itemIndex,optionBtnIndex);`

**说明:**

点击右边按钮的监听方法.

**参数:**

|参数名称|参数类型|是否必选|说明|
|-----|-----|-----|-----|
|itemIndex|Number|是|被点击按钮所在列表项的索引|
|optionBtnIndex|Number|是|被点击按钮的索引|

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    uexListView.onRightOptionButtonInItem = function(itemIndex, optionBtnIndex){
        alert("onRightOptionButtonInItem:" + itemIndex + "," + optionBtnIndex);
    };
```

### 📦 ontPullRefreshHeaderListener 下拉刷新的监听方法

`uexListView.ontPullRefreshHeaderListener(status);`

**说明:**

下拉刷新的监听方法.

**参数:**

|参数名称|参数类型|是否必选|说明|
|-----|-----|-----|-----|
|status|Number|是|刷新状态码(0:开始刷新,1:刷新中,２:刷新完成)|

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    uexListView.ontPullRefreshHeaderListener = function(status){
        alert("ontPullRefreshHeaderListener:" + status);
    };
```

### 📦 ontPullRefreshFooterListener 上拉加载的监听方法

`uexListView.ontPullRefreshFooterListener(status);`

**说明:**

上拉加载的监听方法

**参数:**

|参数名称|参数类型|是否必选|说明|
|-----|-----|-----|-----|
|status|Number|是|刷新状态码(0:开始刷新,1:刷新中,２:刷新完成)|

**平台支持:**

Android2.2+
iOS6.0+

**版本支持:**

3.0.0+

**示例:**

```
    uexListView.ontPullRefreshFooterListener = function(status){
        alert("ontPullRefreshFooterListener:" + status);
    };
```

# 3、更新历史<ignore>

### iOS<ignore>

API版本:`uexListView-3.0.7`

最近更新时间:`2015-12-26`

| 历史发布版本 | 更新内容 |
| ----- | ----- |
| 3.0.7 | 添加IDE支持 |
| 3.0.6 | 未满全屏时去掉多余的行 |
| 3.0.5 | 修复关闭窗口后再次打开界面会卡死的问题 |
| 3.0.4 | 删除接口与Android做统一处理 |
| 3.0.3 | 修复调用删除接口无效的bug |
| 3.0.2 | 修复加载图片大小不统一的bug |
| 3.0.1 | 修复上拉加载时内容加载太快,右滑时出现红色 背景的bug |
| 3.0.0 | Listview下拉列表,封装Listview扩展功能 |

### Android<ignore>

API版本:`uexListView-3.0.10`

最近更新时间:`2016-4-16`

| 历史发布版本 | 更新内容 |
| ----- | ----- |
| 3.0.10 | 删除universalimageloader源码 |
| 3.0.9 | 修复plugin.xml |
| 3.0.8 | 添加自定义布局相关接口 |
| 3.0.7 | 修复listview加载网络图片显示不正常的问题 |
| 3.0.6 | 修复listview侧滑按钮显示不正常的问题 |
| 3.0.5 | 修复listview不能随页面关闭的问题 |
| 3.0.4 | 更新适配机型使用的方法 |
| 3.0.3 | 修复点击打开,再点击删除 插件崩溃的问题, 修复左滑或右滑list时不只显示一个删除和一个分享的问题 |
| 3.0.2 | 修复list条目不足时不能上拉加载的问题 |
| 3.0.1 | 修复下拉刷新内容不正确的问题, 修复list列表中的图标不及时刷新的问题, 修复删除后再次打开无反应的问题 |
| 3.0.0 | Listview下拉列表,封装Listview扩展功能 |
# 4、附录<ignore>

### SwipeType<ignore>

|  type | 说明  |
| ----- | ----- |
| 0 | 可以向右滑动 |
| 1 | 可以向左滑动 |
| 2 | 左右都可以滑动 |
| 3 | 左右都不能滑动 |

