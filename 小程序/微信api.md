
<!-- MarkdownTOC -->

- JSON配置
  - app.json小程序全局配置
    - pages 设置页面路径
    - window 设置默认页面的窗口表现
      - navigationBarBackgroundColor 导航栏背景颜色
      - navigationBarTextStyle 导航栏标题颜色
      - navigationBarTitleText 导航栏标题文字内容
      - navigationStyle String 导航栏样式 \(微信版本 6.6.0\)
      - backgroundColor 窗口的背景色
      - backgroundTextStyle 下拉 loading 的样式
      - backgroundColorTop 顶部窗口的背景色 \(微信版本 6.5.16\)
      - backgroundColorBottom 底部窗口的背景色 \(微信版本 6.5.16\)
      - enablePullDownRefresh 是否开启下拉刷新
      - onReachBottomDistance 页面上拉触底事件触发时距页面底部距离
    - tabBar 设置底部 tab 的表现
      - color tab上的文字默认颜色
      - selectedColor tab上的文字选中时的颜色
      - backgroundColor tab的背景色
      - borderStyle tabbar上边框的颜色
      - list tab 的列表
      - position
    - networkTimeout 设置网络超时时间
    - debug 设置是否开启 debug 模式
  - page.json
  - project.config.json
- WXML 视图层
  - 组件\(标签\)
    - 视图容器
      - view    视图容器
      - scroll-view 可滚动视图容器
      - swiper  滑块视图容器
      - movable-area 可移动视图容器
    - 基础内容
      - icon    图标
      - text    文字
      - progress    进度条
    - 表单
      - button  按钮
      - form    表单
      - input   输入框
      - checkbox    多项选择器
      - radio   单项选择器
      - picker  列表选择器
      - picker-view 内嵌列表选择器
      - slider  滚动选择器
      - switch  开关选择器
      - label   标签
    - 导航
      - navigator 应用链接
    - 多媒体
      - audio   音频
      - image   图片
      - video   视频
    - 地图
      - map 地图
    - 画布
      - canvas 画布
  - 模版处理
    - 数据绑定
    - 列表渲染
    - 条件渲染
    - 模版template
  - 事件
    - 事件绑定
    - 事件对象
      - BaseEvent 基础事件对象属性
      - CustomEvent 自定义事件对象属性
      - TouchEvent 触摸事件对象属性列表（继承 BaseEvent）
      - type 事件的类型
      - timeStamp 页面打开到触发事件所经过的毫秒数
      - target 触发事件的源组件
      - currentTarget 事件绑定的当前组件
      - touches 当前停留在屏幕上的触摸点\(数组\)
      - changedTouches 有变化的触摸点
      - detail 自定义事件所携带的数据
  - 文件引用
    - import
    - include
  - 自定义组件 Component
    - 创建自定义组件
    - 使用自定义组件
    - slot节点
    - 组件样式
    - 外部样式类
    - 组件构造器
    - 组件事件
- WXS
  - module属性
- WXSS
  - 样式导入
- JS 逻辑层
  - App.js 启动js
    - onLaunch   生命周期函数--监听小程序初始化
    - onShow 生命周期函数--监听小程序显示
      - onLaunch, onShow 参数
    - onHide 生命周期函数--监听小程序隐藏
    - onError错误监听函数
    - onPageNotFound 页面不存在监听函数
      - 参数
    - 其他  开发者可以添加任意的函数或数据到 Object 参数中，用 this 可以访问
  - 场景值
  - 注册页面
    - 参数
      - 生命周期
      - 页面事件处理
  - 页面路由
    - 页面栈
    - getCurrentPages\(\)
    - Page.prototype.route
    - Page.prototype.setData\(\)
  - 模块化
- 一个页面加载的过程
  - 过程
- 小程序API
  - 网络
    - wx.request 发起请求
    - 开放接口
      - 登录
      - 用户信息

<!-- /MarkdownTOC -->


## JSON配置

### app.json小程序全局配置

eg:

```
{
  "pages": [
    "pages/index/index",
    "pages/logs/index"
  ],
  "window": {
    "navigationBarTitleText": "Demo"
  },
  "tabBar": {
    "list": [{
      "pagePath": "pages/index/index",
      "text": "首页"
    }, {
      "pagePath": "pages/logs/logs",
      "text": "日志"
    }]
  },
  "networkTimeout": {
    "request": 10000,
    "downloadFile": 10000
  },
  "debug": true
}
```

#### pages 设置页面路径
String Array

> - 必填
- 数组，数组每一项为字符串("路径+文件名")
- 不需要文件后缀，会自动寻找.json，.js，.wxml，.wxss四个文件

#### window 设置默认页面的窗口表现
Object 

![示意图](https://mp.weixin.qq.com/debug/wxadoc/dev/image/config.jpg?t=2018413)

##### navigationBarBackgroundColor 导航栏背景颜色

> - 类型：HexColor
- 默认值：#000000

##### navigationBarTextStyle 导航栏标题颜色

> - 类型：String
- 默认值：white
- 仅支持 black/white 

##### navigationBarTitleText 导航栏标题文字内容   

> - 类型：String

##### navigationStyle String 导航栏样式 (微信版本 6.6.0)

> - 类型：String
- 默认值：default
- 仅支持 default/custom，custom 模式可自定义导航栏，只保留右上角胶囊状的按钮

##### backgroundColor 窗口的背景色

> - 类型：HexColor
- 默认值：#ffffff

##### backgroundTextStyle 下拉 loading 的样式

> - 类型：String
- 默认值：dark
- 仅支持 dark/light

##### backgroundColorTop 顶部窗口的背景色 (微信版本 6.5.16)

> - 类型：String
- 默认值：#ffffff
- 仅 iOS 支持

##### backgroundColorBottom 底部窗口的背景色 (微信版本 6.5.16)

> - 类型：String
- 默认值：#ffffff
- 仅 iOS 支持

##### enablePullDownRefresh 是否开启下拉刷新

> - 类型：Boolean
- 默认值：false

##### onReachBottomDistance 页面上拉触底事件触发时距页面底部距离
> - 类型：Number
- 默认值：50
- 单位：px

#### tabBar 设置底部 tab 的表现
Objec

![tabBar](https://mp.weixin.qq.com/debug/wxadoc/dev/image/tabbar.png?t=2018413)

##### color tab上的文字默认颜色

> - 类型：HexColor
- 必填

##### selectedColor tab上的文字选中时的颜色

> - 类型：HexColor
- 必填

##### backgroundColor tab的背景色

> - 类型：HexColor
- 必填

##### borderStyle tabbar上边框的颜色

> - 类型：String
- 默认值：black
- 仅支持 black/white

##### list tab 的列表

> - 类型：Array
- 必填
- 只能配置最少2个、最多5个 tab，tab 按数组的顺序排序。

- pagePath 页面路径

> - 必填
- 必须在 pages 中先定义

- text tab 上按钮文字

> - 必填

- iconPath 图片路径

> - icon 大小限制为40kb，建议尺寸为 81px * 81px
- 当 postion 为 top 时，此参数无效，不支持网络图片

- selectedIconPath 选中时的图片路径

> - icon 大小限制为40kb，建议尺寸为 81px * 81px
- 当 postion 为 top 时，此参数无效，不支持网络图片

##### position

> - 类型：String
- 默认值：bottom
- 可选值 bottom、top


#### networkTimeout 设置网络超时时间
Object

> - 数据类型：Number
- 单位：毫秒
- 默认值：60000

- request wx.request的超时时间

- connectSocket wx.connectSocket的超时时间

- uploadFile wx.uploadFile的超时时间

- downloadFile wx.downloadFile的超时时间

#### debug 设置是否开启 debug 模式

Boolean

### page.json

- 配置每一个页面

- 只能设置 app.json 中的 window 配置项的内容

- 页面中配置项会覆盖 app.json 的 window 中相同的配置项

- 无需写 window 这个键

eg:

```
{
  "navigationBarBackgroundColor": "#ffffff",
  "navigationBarTextStyle": "black",
  "navigationBarTitleText": "微信接口功能演示",
  "backgroundColor": "#eeeeee",
  "backgroundTextStyle": "light"
}
```

### project.config.json

## WXML 视图层

### 组件(标签)

- block 块标签

> <block/> 并不是一个组件，它仅仅是一个包装元素，不会在页面中做任何渲染，只接受控制属性。

#### 视图容器

##### view    视图容器

- hover-class String  none    指定按下去的样式类。当 hover-class="none" 时，没有点击态效果    

- hover-stop-propagation  Boolean false   指定是否阻止本节点的祖先节点出现点击态 1.5.0

- hover-start-time    Number  50  按住后多久出现点击态，单位毫秒 

- hover-stay-time Number  400 手指松开后点击态保留时间，单位毫秒

##### scroll-view 可滚动视图容器

- scroll-x    Boolean false   允许横向滚动

- scroll-y    Boolean false   允许纵向滚动

- upper-threshold Number  50  距顶部/左边多远时（单位px），触发 scrolltoupper 事件

- lower-threshold Number  50  距底部/右边多远时（单位px），触发 scrolltolower 事件

- scroll-top  Number      设置竖向滚动条位置

- scroll-left Number      设置横向滚动条位置

- scroll-into-view    String      值应为某子元素id（id不能以数字开头）。设置哪个方向可滚动，则在哪个方向滚动到该元素

- scroll-with-animation   Boolean false   在设置滚动条位置时使用动画过渡

- enable-back-to-top  Boolean false   iOS点击顶部状态栏、安卓双击标题栏时，滚动条返回顶部，只支持竖向

- bindscrolltoupper   EventHandle     滚动到顶部/左边，会触发 scrolltoupper 事件

- bindscrolltolower   EventHandle     滚动到底部/右边，会触发 scrolltolower 事件

- bindscroll  EventHandle     滚动时触发，event.detail = {scrollLeft, scrollTop, scrollHeight, scrollWidth, deltaX, deltaY}

##### swiper  滑块视图容器

##### movable-area 可移动视图容器

#### 基础内容

##### icon    图标

##### text    文字

##### progress    进度条

#### 表单

##### button  按钮

##### form    表单

##### input   输入框

##### checkbox    多项选择器

##### radio   单项选择器

##### picker  列表选择器

##### picker-view 内嵌列表选择器

##### slider  滚动选择器

##### switch  开关选择器

##### label   标签

#### 导航

##### navigator 应用链接

#### 多媒体

##### audio   音频

##### image   图片

##### video   视频

#### 地图

##### map 地图

#### 画布

##### canvas 画布

### 模版处理

#### 数据绑定

- 简单绑定

```
<view> {{message}} </view>
```

```
Page({
  data: {
    message: 'Hello MINA!'
  }
})
```

- 组件属性

> 双引号+双大括号

```
<view id="item-{{id}}"> </view>
```

```
Page({
  data: {
    id: 0
  }
})
```

- 控制属性

> 双引号+双大括号

```
<view wx:if="{{condition}}"> </view>
```

```
Page({
  data: {
    condition: true
  }
})
```

- 关键字

```
<checkbox checked="{{false}}"> </checkbox>
```

#### 列表渲染

> 默认数组的当前项的下标变量名默认为 index，数组当前项的变量名默认为 item

```
<view wx:for="{{array}}"> {{index}} {{item}} </view>
```

```
Page({
  data: {
    array: [1, 2, 3, 4, 5]
  }
})
```

> - 使用 wx:for-item 可以指定数组当前元素的变量名
- 使用 wx:for-index 可以指定数组当前下标的变量名

```
<view wx:for="{{array}}" wx:for-index="idx" wx:for-item="itemName">
  {{idx}}: {{itemName.message}}
</view>
```

#### 条件渲染

```
<view wx:if="{{view == 'WEBVIEW'}}"> WEBVIEW </view>
<view wx:elif="{{view == 'APP'}}"> APP </view>
<view wx:else="{{view == 'MINA'}}"> MINA </view>
```

#### 模版template

```
<!-- 定义模版 -->
<template name="staffName">
  <view>
    FirstName: {{firstName}}, LastName: {{lastName}}
  </view>
</template>

<!-- 使用模版 -->
<!-- ...：展开对象staffA -->
<template is="staffName" data="{{...staffA}}"></template>
<template is="staffName" data="{{...staffB}}"></template>
<template is="staffName" data="{{...staffC}}"></template>
```

```
Page({
  data: {
    staffA: {firstName: 'Hulk', lastName: 'Hu'},
    staffB: {firstName: 'Shang', lastName: 'You'},
    staffC: {firstName: 'Gideon', lastName: 'Lin'}
  }
})
```

### 事件

- touchstart  手指触摸动作开始    

- touchmove   手指触摸后移动 

- touchcancel 手指触摸动作被打断，如来电提醒，弹窗  

- touchend    手指触摸动作结束    

- tap 手指触摸后马上离开   

- longpress   手指触摸后，超过350ms再离开，如果指定了事件回调函数并触发了这个事件，tap事件将不被触发

- longtap 手指触摸后，超过350ms再离开（推荐使用longpress事件代替） 

- transitionend   会在 WXSS transition 或 wx.createAnimation 动画结束后触发 

- animationstart  会在一个 WXSS animation 动画开始时触发 

- animationiteration  会在一个 WXSS animation 一次迭代结束时触发   

- animationend    会在一个 WXSS animation 动画完成时触发 

- touchforcechange    在支持 3D Touch 的 iPhone 设备，重按时会触发

#### 事件绑定

bind/catch + 事件名称 eg: bindtap、catchtouchstart

> - bind 不阻止冒泡
- catch 阻止冒泡

#### 事件对象

eg:

```
{
"type":"tap",
"timeStamp":895,
"target": {
  "id": "tapTest",
  "dataset":  {
    "hi":"WeChat"
  }
},
"currentTarget":  {
  "id": "tapTest",
  "dataset": {
    "hi":"WeChat"
  }
},
"detail": {
  "x":53,
  "y":14
},
"touches":[{
  "identifier":0,
  "pageX":53,
  "pageY":14,
  "clientX":53,
  "clientY":14
}],
"changedTouches":[{
  "identifier":0,
  "pageX":53,
  "pageY":14,
  "clientX":53,
  "clientY":14
}]
}

```

##### BaseEvent 基础事件对象属性

- type    String  事件类型

- timeStamp   Integer 事件生成时的时间戳

- target  Object  触发事件的组件的一些属性值集合

- currentTarget   Object  当前组件的一些属性值集合

##### CustomEvent 自定义事件对象属性

- detail  Object  额外的信息

##### TouchEvent 触摸事件对象属性列表（继承 BaseEvent）

- touches Array   触摸事件，当前停留在屏幕中的触摸点信息的数组

- changedTouches  Array   触摸事件，当前变化的触摸点信息的数组

##### type 事件的类型

##### timeStamp 页面打开到触发事件所经过的毫秒数

##### target 触发事件的源组件

- id  String  事件源组件的id

- tagName String  当前组件的类型

- dataset Object  事件源组件上由data-开头的自定义属性组成的集合

##### currentTarget 事件绑定的当前组件

- id  String  当前组件的id

- tagName String  当前组件的类型

- dataset Object  当前组件上由data-开头的自定义属性组成的集合

eg:

```
<!-- data-小写-小写 -->
<view data-alpha-beta="1" data-alphaBeta="2" bindtap="bindViewTap"> DataSet Test </view>
```

```
// dataset.驼峰

// - 会转为驼峰写法
// 大写会转为小写

Page({
  bindViewTap:function(event){
    event.currentTarget.dataset.alphaBeta === 1 // - 会转为驼峰写法
    event.currentTarget.dataset.alphabeta === 2 // 大写会转为小写
  }
})
```

##### touches 当前停留在屏幕上的触摸点(数组)

> touches数组中的每一项为一个Touch对象，canvas对应的为CanvasTouch对象

Touch

- identifier  Number  触摸点的标识符

- pageX, pageY    Number  距离文档左上角的距离，文档的左上角为原点 ，横向为X轴，纵向为Y轴

- clientX, clientY    Number  距离页面可显示区域（屏幕除去导航条）左上角距离，横向为X轴，纵向为Y轴

CanvasTouch

- identifier  Number  触摸点的标识符 

- x, y    Number  距离 Canvas 左上角的距离，Canvas 的左上角为原点 ，横向为X轴，纵向为Y轴


##### changedTouches 有变化的触摸点

> changedTouches 数据格式同 touches。 表示有变化的触摸点，如从无变有（touchstart），位置变化（touchmove），从有变无（touchend、touchcancel）。

##### detail 自定义事件所携带的数据
自定义事件所携带的数据，如表单组件的提交事件会携带用户的输入，媒体的错误事件会携带错误信息，详见组件定义中各个事件的定义。

> 点击事件的detail 带有的 x, y 同 pageX, pageY 代表距离文档左上角的距离。

### 文件引用

#### import

```
<!-- item.wxml -->
<template name="item">
  <text>{{text}}</text>
</template>
```

```
<import src="item.wxml"/>
<template is="item" data="{{text: 'forbar'}}"/>
```

> 作用域
C import B，B import A，在C中可以使用B定义的template，在B中可以使用A定义的template，但是C不能使用A定义的template。

#### include

include 可以将目标文件**除了** `<template/> <wxs/>` 外的整个代码引入，相当于是拷贝到 include 位置。

```
<!-- header.wxml -->
<view> header </view>
<!-- footer.wxml -->
<view> footer </view>
```

```
<!-- index.wxml -->
<include src="header.wxml"/>
<view> body </view>
<include src="footer.wxml"/>
```

### 自定义组件 Component

#### 创建自定义组件

> **component.json**中声明

```
{
  "component": true
}
```

>  **component.wxml**

```
<view class="inner">
  {{innerText}}
</view>
```

```
Component({
  properties: {
    // 这里定义了innerText属性，属性值可以在组件使用时指定
    innerText: { 
      type: String,
      value: 'default value',
    }
  },
  data: {
    // 这里是一些组件内部数据
    someData: {}
  },
  methods: {
    // 这里是一个自定义方法
    customMethod: function(){}
  }
})
```

#### 使用自定义组件

> **page.json**中声明

```
{
  "usingComponents": {
    "component-tag-name": "path/to/the/custom/component"
  }
}
```

> **page.wxml**

```
<view>
  <!-- 以下是对一个自定义组件的引用，指定inner-text -->
  <component-tag-name inner-text="Some text"></component-tag-name>
</view>
```

> WXML节点标签名只能是小写字母、中划线和下划线的组合，所以自定义组件的标签名也只能包含这些字符。
自定义组件也是可以引用自定义组件的，引用方法类似于页面引用自定义组件的方式（使用 usingComponents 字段）。
自定义组件和使用自定义组件的页面所在项目根目录名不能以“wx-”为前缀，否则会报错。

#### slot节点

> component.wxml

```
<view class="wrapper">
  <view>这里是组件的内部节点</view>
  <slot></slot>
</view>
```

> page.wxml

```
<view>
  <component-tag-name>
    <!-- 这部分内容将被放置在组件 <slot> 的位置上 -->
    <view>这里是插入到组件slot中的内容</view>
  </component-tag-name>
</view>
```

- 多个slot节点

> component.js

```
Component({
  options: {
    multipleSlots: true // 在组件定义时的选项中启用多slot支持
  },
  properties: { /* ... */ },
  methods: { /* ... */ }
})
```

> component.wxml

```
<view class="wrapper">
  <slot name="before"></slot>
  <view>这里是组件的内部细节</view>
  <slot name="after"></slot>
</view>
```

> page.wxml

```
<view>
  <component-tag-name>
    <!-- 这部分内容将被放置在组件 <slot name="before"> 的位置上 -->
    <view slot="before">这里是插入到组件slot name="before"中的内容</view>
    <!-- 这部分内容将被放置在组件 <slot name="after"> 的位置上 -->
    <view slot="after">这里是插入到组件slot name="after"中的内容</view>
  </component-tag-name>
</view>
```

#### 组件样式

组件可以指定它所在节点的默认样式，使用 :host 选择器（需要包含基础库 1.7.2 或更高版本的开发者工具支持）。

```
:host {
  color: yellow;
}
```

#### 外部样式类

在 Component 中用 externalClasses 定义段定义若干个外部样式类。这个特性从小程序基础库版本 1.9.90 开始支持。

```
Component({
  externalClasses: ['my-class']
})
```

```
<custom-component class="my-class">这段文本的颜色由组件外的 class 决定</custom-component>
```

#### 组件构造器

- properties
组件的对外属性，是属性名到属性设置的映射表，属性设置中可包含三个字段， type 表示属性类型、 value 表示属性初始值、 observer 

- data
组件的内部数据，和 properties 一同用于组件的模版渲染

- methods
组件的方法，包括事件响应函数和任意的自定义方法

- behaviors
类似于mixins和traits的组件间代码复用机制

- created
组件生命周期函数，在组件实例进入页面节点树时执行，注意此时不能调用 setData

- attached
组件生命周期函数，**在组件实例进入页面节点树时执行**

- ready
组件生命周期函数，**在组件布局完成后执行，此时可以获取节点信息（使用 SelectorQuery ）**

- moved
组件生命周期函数，**在组件实例被移动到节点树另一个位置时执行**

- detached
组件生命周期函数，**在组件实例被从页面节点树移除时执行**

- relations
组件间关系定义

- externalClasses
组件接受的外部样式类

- options
一些组件选项

#### 组件事件

- 创建事件

> page.wxml

```
<!-- 当自定义组件触发“myevent”事件时，调用“onMyEvent”方法 -->
<component-tag-name bindmyevent="onMyEvent" />
<!-- 或者可以写成 -->
<component-tag-name bind:myevent="onMyEvent" />
```

> page.js

```
Page({
  onMyEvent: function(e){
    e.detail // 自定义组件触发事件时提供的detail对象
  }
})
```

- 触发事件

> component.wxml

```
<!-- 在自定义组件中 -->
<button bindtap="onTap">点击这个按钮将触发“myevent”事件</button>
```

> component.js

```
Component({
  properties: {}
  methods: {
    onTap: function(){
      var myEventDetail = {} // detail对象，提供给事件监听函数
      var myEventOption = {} // 触发事件的选项
      this.triggerEvent('myevent', myEventDetail, myEventOption)
    }
  }
})
```

## WXS

WeiXin Script，小程序的一套脚本语言，结合 WXML，可以构建出页面的结构。

> WXS 代码可以编写在 wxml 文件中的 <wxs> 标签内，或以 .wxs 为后缀名的文件内。

> <wxs> 模块只能在定义模块的 WXML 文件中被访问到。使用 <include> 或 <import> 时，<wxs> 模块不会被引入到对应的 WXML 文件中。
<template> 标签中，只能使用定义该 <template> 的 WXML 文件中定义的 <wxs> 模块。

eg:

```
<!--wxml-->
<wxs module="m1">
var msg = "hello world";

module.exports.message = msg;
</wxs>

<view> {{m1.message}} </view>
```

### module属性
规则

- 首字符必须是：`字母（a-zA-Z）`，`下划线（_）`

- 剩余字符可以是：`字母（a-zA-Z）`，`下划线（_）`， `数字（0-9）`

## WXSS

> 尺寸单位：rpx
eg:规定屏幕宽为750rpx。如在 iPhone6 上，屏幕宽度为375px，共有750个物理像素，则750rpx = 375px = 750物理像素，1rpx = 0.5px = 1物理像素。

- app.wxss

- page.wxss

### 样式导入

```
/** common.wxss **/
.small-p {
  padding:5px;
}
```

```
/** app.wxss **/
@import "common.wxss";
.middle-p {
  padding:15px;
}
```

## JS 逻辑层

### App.js 启动js

App.js onLaunch 事件

```
App({
  onLaunch: function () {
    // 小程序启动之后 触发
  }
})
```

> getApp()
全局的 getApp() 函数可以用来获取到小程序实例。
- App() 必须在 app.js 中注册，且不能注册多个。
- 不要在定义于 App() 内的函数中调用 getApp() ，使用 `this` 就可以拿到 app 实例。
- **不要在 onLaunch 的时候调用 getCurrentPages()**，此时 page 还没有生成。
- 通过 getApp() 获取实例之后，不要私自调用生命周期函数。

参数

#### onLaunch   生命周期函数--监听小程序初始化

> 当小程序初始化完成时，会触发 onLaunch（全局只触发一次）

#### onShow 生命周期函数--监听小程序显示

> 当小程序启动，或从后台进入前台显示，会触发 onShow

##### onLaunch, onShow 参数

- path 打开小程序的路径

> - 数据类型：String 

- query 打开小程序的query

> - 数据类型：Object 

- scene 打开小程序的场景值

> - 数据类型：Number 

- shareTicket获取更多转发信息

> - 数据类型：String 

- referrerInfo 当场景为由从另一个小程序或公众号或App打开时，返回此字段

> - 数据类型：Object 

- referrerInfo.appId 来源小程序或公众号或App的appId

> - 数据类型：String
- 1020  公众号 profile 页相关小程序列表    返回来源公众号 appId
- 1035  公众号自定义菜单    返回来源公众号 appId
- 1036  App 分享消息卡片  返回来源应用 appId
- 1037  小程序打开小程序    返回来源小程序 appId
- 1038  从另一个小程序返回   返回来源小程序 appId
- 1043  公众号模板消息 返回来源公众号 appId

- referrerInfo.extraData 来源小程序传过来的数据，scene=1037或1038时支持

> - 数据类型：Object 

#### onHide 生命周期函数--监听小程序隐藏

> 当小程序从前台进入后台，会触发 onHide

#### onError错误监听函数

> 当小程序发生脚本错误，或者 api 调用失败时，会触发 onError 并带上错误信息

#### onPageNotFound 页面不存在监听函数

> 当小程序出现要打开的页面不存在的情况，会带上页面信息回调该函数

##### 参数
- path

> -数据类型：String
- 不存在页面的路径

- query

> -数据类型：Object
- 打开不存在页面的 query

- isEntryPage

> -数据类型：Boolean
- 是否本次启动的首个页面（例如从分享等入口进来，首个页面是开发者配置的分享页面）


#### 其他  开发者可以添加任意的函数或数据到 Object 参数中，用 this 可以访问

### 场景值


### 注册页面

```
Page({
  data: { // 参与页面渲染的数据
    logs: []
  },
  onLoad: function () {
    // 页面渲染后 执行
    this.setData({
      text: 'Set some data for updating view.'
    }, function() {
      // this is setData callback
    })
  },
  clickMe: function() {
    this.setData({msg: "HHH"})
  }
})
```

> Page() 函数用来注册一个页面，Page: 页面构造器

#### 参数

- data    Object  页面的初始数据

> **参数内容在页面加载时会进行一次深拷贝**，需考虑数据大小对页面加载的开销

![page的生命周期](https://mp.weixin.qq.com/debug/wxadoc/dev/image/mina-lifecycle.png?t=2018412)

##### 生命周期

- onLoad  Function    生命周期函数--监听页面加载

> 一个页面只会调用一次

- onReady Function    生命周期函数--监听页面初次渲染完成

> 一个页面只会调用一次
对界面的设置如wx.setNavigationBarTitle请在onReady之后设置

- onShow  Function    生命周期函数--监听页面显示 

> 每次打开页面都会调用一次

- onHide  Function    生命周期函数--监听页面隐藏

> 当navigateTo/底部tab切换时调用

- onUnload    Function    生命周期函数--监听页面卸载

> 当redirectTo/navigateBack的时候调用

##### 页面事件处理

- onPullDownRefresh   Function    监听用户下拉动作

> - 需要在app.json的window选项中或页面配置中开启`enablePullDownRefresh`
- 当处理完数据刷新后，`wx.stopPullDownRefresh`可以停止当前页面的下拉刷新

- onReachBottom   Function    监听用户上拉触底

> - 可以在app.json的window选项中或页面配置中设置触发距离onReachBottomDistance
- 在触发距离内滑动期间，本事件只会被触发一次

- onShareAppMessage   Function    监听用户用户点击右上角转发

> - 只有定义了此事件处理函数，右上角菜单才会显示“转发”按钮
- 此事件需要 return 一个 Object，用于自定义转发内容

> 自定义转发内容
- title   转发标题    当前小程序名称
- path    转发路径    当前页面 path ，必须是以 / 开头的完整路径

```
Page({
  onShareAppMessage: function () {
    return {
      title: '自定义转发标题',
      path: '/page/user?id=123'
    }
  }
})
```

- onPageScroll    Function    页面滚动触发

> 参数：scrollTop   Number   页面在垂直方向已滚动的距离（单位px）

- onTabItemTap    Function    当前是 tab 页时，点击 tab 时触发

- 其他  Any 开发者可以添加任意的函数或数据到 object 参数中，在页面的函数中用 this 可以访问


### 页面路由

#### 页面栈

- 初始化 新页面入栈  

>触发时机：小程序打开的第一个页面
路由后页面：onLoad, onShow

- 打开新页面   新页面入栈  

> 触发时机：调用 API `wx.navigateTo` 或使用组件 `<navigator open-type="navigateTo"/>` 
路由前页面：onHide
路由后页面：onLoad, onShow

- 页面重定向   当前页面出栈，新页面入栈

> 调用 API `wx.redirectTo` 或使用组件 `<navigator open-type="redirectTo"/>`
路由前页面：onUnload
路由后页面：onLoad, onShow

- 页面返回    页面不断出栈，直到目标返回页，新页面入栈

> 触发时机：调用 API `wx.navigateBack` 或使用组件`<navigator open-type="navigateBack">`或用户按左上角返回按钮
路由前页面：onUnload
路由后页面：onShow

- 重加载 页面全部出栈，只留下新的页面

> 触发时机：调用 API `wx.reLaunch` 或使用组件 `<navigator open-type="reLaunch"/>`
路由前页面：onUnload
路由后页面：onLoad, onShow

- Tab 切换  页面全部出栈，只留下新的 Tab 页面

> 触发时机：调用 API `wx.switchTab` 或使用组件 `<navigator open-type="switchTab"/>` 或用户切换 Tab

> Tab 切换对应的生命周期（以 A、B 页面为 Tabbar 页面，C 是从 A 页面打开的页面，D 页面是从 C 页面打开的页面为例）：
> 当前页面    路由后页面   触发的生命周期（按顺序）
A   A   Nothing happend
A   B   A.onHide(), B.onLoad(), B.onShow()
A   B（再次打开） A.onHide(), B.onShow()
C   A   C.onUnload(), A.onShow()
C   B   C.onUnload(), B.onLoad(), B.onShow()
D   B   D.onUnload(), C.onUnload(), B.onLoad(), B.onShow()
D（从转发进入）    A   D.onUnload(), A.onLoad(), A.onShow()
D（从转发进入）    B   D.onUnload(), B.onLoad(), B.onShow()

---

> - navigateTo, redirectTo 只能打开非 tabBar 页面。
- switchTab 只能打开 tabBar 页面。
- reLaunch 可以打开任意页面。
- 页面底部的 tabBar 由页面决定，即只要是定义为 tabBar 的页面，底部都有 tabBar。
- 调用页面路由带的参数可以在目标页面的onLoad中获取。

#### getCurrentPages()

getCurrentPages() 函数用于获取当前页面栈的实例，以数组形式按栈的顺序给出，第一个元素为首页，最后一个元素为当前页面。

#### Page.prototype.route

route 字段可以获取到当前页面的路径。

> 基础库 1.2.0 开始支持，低版本需做兼容处理

- 兼容处理

`wx.getSystemInfo` 或者 `wx.getSystemInfoSync` 获取到小程序的基础库版本号。
`wx.canIUse('xxx')` 详情 来判断是否可以在该基础库版本下直接使用对应的API或者组件

#### Page.prototype.setData()

setData 函数用于将数据从逻辑层发送到视图层（异步），同时改变对应的 this.data 的值（同步）。

> 直接修改 this.data 而不调用 this.setData 是无法改变页面的状态的，还会造成数据不一致。
单次设置的数据不能超过1024kB。

### 模块化

- 导出 module.exports

```
// common.js
function sayHello(name) {
  console.log(`Hello ${name} !`)
}

module.exports.sayHello = sayHello
```

- 导入 require('path/xxx.js')

> require 暂时不支持绝对路径

```
var common = require('common.js')
Page({
  helloMINA: function() {
    common.sayHello('MINA')
  },
})
```

## 一个页面加载的过程

文件结构

- main.js

- main.json

- main.wxml

- main.wxss

### 过程

1. 微信客户端会先根据 main.json 配置生成一个界面，定义顶部的颜色和文字。

2. 紧接着客户端就会装载这个页面的 WXML 结构和 WXSS 样式。

3. 最后客户端会装载 main.js。

## 小程序API

### 网络

#### wx.request 发起请求

```
wx.request({
  url: 'test.php',
  data: {
     x: '' ,
     y: ''
  },
  header: {
      'content-type': 'application/json' // 默认值
  },
  success: function(res) {
    console.log(res.data)
  }
})
```

#### 开放接口

##### 登录

- wx.login(res)  获取临时登录凭证

##### 用户信息

- wx.getUserInfo(res) 获取用户信息















