#Material Design Lite 学习

##Material Design

####设计语言

####材料/Material

Material Design核心:扁而不平  
`mdl-shadow--Ndp`: 声明材料阴影。 N有效值取：2/3/4/6/8/16
```
<!--为元素声明2dp的阴影-->
<any class="mdl-shadow--2dp">...</any>
```

####色彩/Color

Material Design使用19个调色板（red、pink、purple等）用来约束设计中色彩的使用。 在每个调色板中，色调为500的颜色为基准色，其他颜色是基准色在不同色调（50-900, A100-700） 下的表现。  
[Material Design完整的调色板集](http://)
`mdl-color--{palette}-{hue}`：设置背景色  
`mdl-color-text--{palette}-{hue}`：设置前景色  
```
<div class="mdl-color--red mdl-color-text--grey-50">
    this is a gray text on red background.
</div>
```

####色彩运用

* 最多使用两个调色板
  * 在一个界面中最多使用两个调色板，从*主调色板*选择最多三个色调，从*辅调色板*选择 一个强调色。  
* 为文本、图标和分割线应用透明度
  * 对于深色背景的浅色文字，最重要的文本使用87%的透明度，次重要的文本使用54%的 透明度。提示性文本，例如输入框、标签、被禁止的文字等使用26%的透明度。
  * 对于浅色背景的深色文字，最重要的文本使用100%的透明度，次重要的文本使用70%的 透明度，其他文本使用30%的透明度。
* 工具栏和状态栏
  * 工具栏和大色块应当使用调色板中色调为500的颜色为*基准色*。状态栏应当选择*调色板*中比基准色略深的色调为700的颜色。
* 使用强调色
  * 在大色块上绝对不要使用强调色，对动作按钮、开关或滑动条之类的组件应当使用*强调色*

####图标/Icon

前端样式表中使用``@font-face`引用Material Design图标字体:
```
/*icon.css*/
@font-face {
  font-family: 'Material Icons';
  font-style: normal;
  font-weight: 400;
  src: local('Material Icons'), local('MaterialIcons-Regular'),
         url(material-icons.woff2) format('woff2'),
       url(material-icons.woff) format('woff');
}

.material-icons {
  font-family: 'Material Icons';
  font-weight: normal;
  font-style: normal;
  font-size: 24px;
  line-height: 1;
  letter-spacing: normal;
  text-transform: none;
  display: inline-block;
  word-wrap: normal;
  -webkit-font-smoothing: antialiased;    
  /*text-rendering must be set for local host fonts*/
  text-rendering: optimizeLegibility;
  -moz-font-feature-settings: 'liga';
  -moz-osx-font-smoothing: grayscale;
}
```
使用图表字体，只需要应用上面定义的`material-icons`样式。  
图标大小依赖于字体大小。  
```
<!--创建笑脸图标-->
<i class="material-icons">face</i><!--使用图标名-->
<i class="material-icons">&#xE87C;</i><!--使用字体编码-->
```

####排版/Ttypography

Material Design提供了11种规格的文字样式供不同场景下排版使用。  
`mdl-typography--{name}`：声明文本排版样式。
```
<h1 class="mdl-typography--title">Hello,Material Design</h1>
<p class="mdl-typography--body-2">this is a demo</p>
```

##MDL布局组件

####布局/Layout

样式：
```
-------------------------------
|      |        header        |
|      |----------------------|
|      |                      |
|drawer|                      |
|      |        content       |
|      |                      |
|      |                      |
-------------------------------
```

布局/Layout组件按特定的HTML结构进行声明：
```
<any class="mdl-layout mdl-js-layout">
  <any class="mdl-layout__header">...</any>
  <any class="mdl-layout__drawer">...</any>
  <any class="mdl-layout__content">...</any>
</any>
```
在一个布局声明中，header等子元素不一定全部使用  
显示效果：
* 桌面--当屏幕尺寸宽度大于840px时，MDL按桌面环境应对
* 平板--当屏幕尺寸大于480px，但小于840px时，MDL按平板环境应对，比如自动隐藏header、drawer区域等
* 手机--当屏幕尺寸小于480px时，MDL按手机环境应对

配置选项：  

MDL class | 说明
--------- | ---
mdl-layout | 声明元素为布局组件  
mdl-js-layout | 为布局实现基本的行为逻辑
mdl-layout__header | 声明元素为布局头/header元素
mdl-layout__drawer | 声明元素为侧栏菜单/drawer元素
mdl-layout__content | 声明元素为布局内容/content元素
mdl-layout--fixed-drawer | 将侧栏菜单/drawer声明为固定式
mdl-layout--fixed-header | 将头部/header声明为固定式
mdl-layout--screen-only | 在小尺寸屏幕上隐藏头部/header
mdl-layout--overlay-drawer-button | 为布局添加激活侧栏菜单按钮

####头部/Header

布局组件的header由一系列header-row组成：  
```
|-----------------------------|
|         header-row          |
|-----------------------------|
|         header-row          |
|-----------------------------|
| title | spacer | navigation |
|-----------------------------|
```

配置选项：  

MDL class | 说明
--------- | ---
mdl-layout__header-row | 声明元素为行容器
mdl-layout-title | 声明元素为标题
mdl-layout-icon | 声明元素为菜单图标
mdl-layout-spacer | 声明元素自动填充行容器剩余空间
mdl-layout__header--transparent | 声明布局头为透明背景
mdl-layout__header--scroll | 声明布局头为可滚动
mdl-layout__header--waterfall | 对多行标题，当滚动内容时，仅现实第一行

####头部-导航/Naviation

一个典型的样式：
```
-------------------------------
| title | spacer | navigation |
-------------------------------
```

导航块由一个容器导航和若干导航链接构成：
```
<div class="mdl-layout__header-row">
  <!--导航容器-->
  <nav class="mdl-navigation">
    <!--导航链接-->
    <a href="...">link</a>
    <a href="...">link</a>
    <a href="...">link</a>
  </nav>
</div>
```  

配置选项：  

MDL class | 说明
--------- | ---
mdl-navigation | 声明元素为MDL导航组
mdl-navigation__link | 声明锚点元素为MDL导航链接

####头部-选项卡/Tabs

```
----------------------------------------
|--------------------------------------|
||                          header-row||
|--------------------------------------|
|--------------------------------------|
||| tab | tab | tab |          tab-bar||
|----|-----|-----|---------------------|
|----------|-----|---------------------|
||         |     |           tab-panel||
|----------|-----|---------------------|
|----------------|---------------------|
||               |                    ||
|----------------|---------------------|
|--------------------------------------|
||                                    ||
|--------------------------------------|
----------------------------------------
```

在布局头部可以嵌入`选项栏/tab-bar`，内容区域可以嵌入`选项面板/tab-panel`。当用户点击选项栏中的`链接/tab*`时，自动显示对应的选项面板。  
在布局头部声明选项栏，需要遵循特定的HTML结构：
```
<header class="mdl-layout__header">
  <!--声明选项栏-->
  <div class="mdl-layout__tab-bar">
    <!--声明选项，通过href绑定对应的面板，对要激活的选项声明js-active-->
    <a href="#panel-1" class="mdl-layout__tab is-active">tab-1</a>
    <a href="#panel-2" class="mdl-layout__tab">tab-2</a>
    <a href="#panel-3" class="mdl-layout__tab">tab-3</a>
  </div>
</header>
```
在布局内容区域声明选项面板，也依赖于特定的HTML结构：
```
<main class="mdl-layout__content">
  <!--声明选项面板，使用id属性指定锚点，对要初始化的面板声明is-active-->
  <div class="mdl-layout__tab-panel is-active">...</div>
  <div class="mdl-layout__tab-panel">...</div>
  <div class="mdl-layout__tab-panel">...</div>
</main>
```

配置选项：

MDL class | 说明
--------- | ---
mdl-layout__tab-bar | 声明元素为选项栏
mdl-layout__tab | 声明锚点元素为选项链接
mdl-layout__tab-panel | 声明元素为选项面板
is-active | 将选项链接/tab或选项面板/tab-panel声明为激活
mdl-layout--fixed-tabs | 将头部tab声明为固定式

####侧拉菜单/Drawer

样式：
```
--------------
|    title   |
|----------- |
|            |
| navigation |
|            |
--------------
```

侧拉菜单默认情况下是隐藏的，需要用户点击按钮

设置修饰样式类`mdl-layout--fixed-drawer`强制显示侧拉菜单（小尺寸屏幕下总是隐藏的）
```
<div class="mdl-layout  mdl-layout--fixed-drawer">
  <div class="mdl-layout__drawer">...</div>
</div>
```
侧拉菜单中也可使用导航，这时所有的链接自动按垂直方向排列：
```
<div class="mdl-layout__drawer">
  <nav class="mdl-navigation">
    <a href="..." class="mdl-navigation__link">link 1</a>
    <a href="..." class="mdl-navigation__link">link 2</a>
  </nav>
</div>
```

配置选项：

MDL class | 说明
--------- | ---
mdl-layout__drawer | 声明元素为侧栏菜单/drawer组件
mdl-layout-title | 声明元素为标题
mdl-navigation | 声明元素为MDL导航组
mdl-navigation__link | 声明锚点元素为MDL导航链接
mdl-layout--fixed-drawer | 将侧栏菜单/drwaer声明为固定式

##MDL 容器组件

####单行页脚/Mini footer

MDL的`单行页脚/Mini footer`组件以单行水平方式组织所有的信息：
```
----------------------------------------
| left-section           right-section |
|----------------------  --------------|
|| logo | link-list   |  | social-bin ||
|----------------------  --------------|
----------------------------------------
```

单行页脚同样采用flexbox布局，将整行分隔为左右两种区域，并以空格填充剩余的空间：
```
<footer class="mdl-mini-footer">
  <div class="mdl-mini-footer--left-section">...</div>
  <div class="mdl-mini-footer--right-section">...</div>
</footer>
```
`left-section`总是向左对齐，`right-section`总是向右对齐。单行页脚内可以放置多个`right-section`与`left-section`  
在每个区域内，MDL预定义了两种交互元素：链接和社交按钮。  
`链接/link-list`样式应用在列表元素`url`上，自动将列表成员水平排列：
```
<div class="mdl-mini-footer--left-section">
  <ul class="mdl-mini-footer--link-list">
    <li><a href="...">link 1</a></li>
    <li><a href="...">link 2</a></li>
    <li><a href="...">link 3</a></li>
  </ul>
</ul>
```
`社交按钮/social-btn`样式将元素修饰为36px正方大小的容器，可以设置其背景图片来构造图标式按钮。  

配置选项：

MDL class | 说明
--------- | ---
mdl-mini-footer | 声明元素为单行页脚组件
mdl-mini-footer--left-section | 声明元素为左区域容器
mdl-mini-footer--right-section | 声明元素为右区域容器
mdl-logo | 声明元素为logo区
mdl-mini-footer--link-list | 声明元素为链接容器
mdl-mini-footer--social-btn | 声明元素为36px大小的方块区域

####多行页脚/Mega footer

MDL的`多行页脚/Mega footer`组件可以包含多个垂直排列的区域。
```
----------------------------------------
|--------------------------------------|
||                                    || top-section
|--------------------------------------|
|                                      |
|--------------------------------------|
||--------------------- --------------||
|||        | |        | | header    |||| middle-section
||| drop-down-section | |------------|||
|||        | |        | | link-list ||||
||--------------------- -------------|||
|--------------------------------------|
|                                      |
|--------------------------------------|
||--left-section--------right-section-|| bottom-section
||| logo | link-list | | social-btn  |||
||-------------------- ---------------||
|--------------------------------------|
----------------------------------------
```
`单行页脚/Mini footer`组件相当于仅适用`多行页脚/Mega footer`组件的`bottom-section`区域  
当声明为`mdl-mega-footer--link-list`样式的列表元素出现在`drop-down-section`区域时，其列表项是垂直排列的  

配置选项：

MDL class | 说明
--------- | ---
mdl-mega-footer | 声明元素为多行页脚组件
mdl-mega-footer--top-section | 声明元素为顶部区域
mdl-mega-footer--middle-section | 声明元素为中部区域
mdl-mega-footer--bottom-section | 声明元素为底部区域
mdl-mega-footer--left-section | 声明元素在容器内居左
mdl-mega-footer--right-section | 声明元素在容器内居右
mdl-mega-footer--drop-down-section | 声明元素为垂直内容区
mdl-mega-footer--link-list | 声明元素为链接容器
mdl-mega-footer--heading | 声明元素为标题
mdl-logo | 声明元素为logo区
mdl-mega-footer-social-btn | 声明元素为36px正方大小

####栅格/Grid

MDL的`栅格/Grid`是响应式的，根据屏幕尺寸大小，自动地分隔行宽：
* 桌面（>840px）-12个单元格
* 平板（480px~840px）-8个单元格
* 手机（<480px）-4个单元格

可使用`mdl-cell--N-col`样式声明单元格的宽度：
```
<div class="mdl-grid">
  <div class="mdl-cell mdl-cell--4-col">...</div>
  <div class="mdl-cell mdl-cell--4-col">...</div>
  <div class="mdl-cell mdl-cell--4-col">...</div>
</div>
```
不同分辨率下，示例栅格将呈现如下：
```
----------------------------------
|---------- ---------- ----------| 桌面
||        | |        | |        ||
||        | |        | |        ||
|---------- ---------- ----------|
----------------------------------
------------------- 平板 手机 -----------
|-------- --------|          |---------|
||      | |      ||          ||       ||
|-------- --------|          |---------|
|--------         |          |---------|
||      |         |          ||       ||
|--------         |          |---------|
-------------------          |---------|
                             ||       ||
                             |---------|
                             -----------
```
若希望在任何情况下，示例栅格总是显示为相同的列数，可以声明单元格在不同环境下的样式：
```
<div class="mdl-grid">
  <div class="mdl-cell mdl-cell--6-col-desktop mdl-cell--4-col-table mdl-cell--2-col-phone">...</div>
  <div class="mdl-cell mdl-cell--6-col-desktop mdl-cell--4-col-table mdl-cell--2-col-desktop">...</div>
</div>
```
在同一行的各单元格，默认情况下总是`拉伸/stretch`其高度（采用同一行中最高单元格的高度），可以使用`mdl-cell--bottom`样式使单元格不拉伸，并将其底部对齐  
与之类似，`mdl-cell--top`使单元格顶部对齐，`mdl-cell--middle`使单元格居中对齐
```
<div class="mdl-grid">
  <!--顶部对齐-->
  <div class="mdl-cell mdl-cell--top">...</div>
  <!--居中对齐-->
  <div class="mdl-cell mdl-cell-middle">...</div>
  <!--底部对齐-->
  <div class="mdl-cell mdl-cell--bottom">...</div>
</div>
```

配置选项：

MDL class | 说明
--------- | ---
mdl-grid | 将元素声明为grid组件
mdl-cell | 将元素声明为grid组件的单元格cell
mdl-cell--N-col | 设置单元格宽为N（1-12），默认为4，可选
mdl-cell--N-col-desktop | 在桌面环境下设置单元格宽为N（1-8），可选
mdl-cell--N-col-tablet | 在平板环境下设置单元格宽为N（1-8），可选
mdl-cell--N-col-phone	| 在手机环境下设置单元格宽为N（1-4），可选
mdl-cell--hide-desktop | 在桌面环境下隐藏该单元格，可选
mdl-cell--hide-tablet | 在平板环境下隐藏该单元格，可选
mdl-cell--hide-phone | 在手机环境下隐藏该单元格，可选
mdl-cell--stretch | 在垂直方向拉伸单元格以充满父元素，这是单元格的默认值
mdl-cell--top | 在垂直方向单元格顶部对齐，可选
mdl-cell--middle | 在垂直方向单元居中部对齐，可选
mdl-cell--bottom | 在垂直方向单元格底部对齐，可选

####选项卡/Tabs

MDL的`选项卡/Tabs`组件用来在多个内容间进行切换  
`选项卡/Tabs`有固定的HTML结构，由选项栏、选项面板等元素构成：
```
<!--1.声明组件-->
<div class="mdl-tabs mdl-js-tabs">
  <!--2.声明选项卡-->
  <div class="mdl-tabs__tab-bar">
    <!--声明选项，使用href属性指向选项面板，为要激活的选项应用is-active样式-->
    <a class="mdl-tabs__tab is-active" href="#panel-1">tab-1</a>
    <a class="mdl-tabs__tab" href="#panel-2">tab-2</a>
  </div>
  <!--3.声明选项面板，使用id属性声明锚点，为要显示的面板应用is-active样式-->
  <div class="mdl-tabs__panel is-active" id="panel-1">...</div>
  <div class="mdl-tabs__panel" id="panel-2">...</div>
</div>
```
可以为组件元素应用`mdl-js-ripple-effect`样式，使点击时具有水纹效果  

配置选项：

MDL class | 功能
--------- | ---
mdl-tabs | 将元素声明为tabs组件
mdl-js-tabs | 实现tabs组件的基本逻辑
mdl-tabs__tab-bar | 将元素声明为tabs组件的导航条容器
mdl-tabs__tab | 将链接元素声明为tabs组件的tab页触发器
mdl-tabs__panel | 将元素声明为tabs组件的tab页内容面板
is-active | 将tab页内容面板或tab触发器设置为活动状态
mdl-js-ripple-effect | 为tab页触发器增加点击时水纹效果，可选

####卡片/Cards

MDL的`卡片/Card`组件：
```
--------------------
|------------------|
||    title |menu|||
|------------------|
|------------------|
||    media       ||
|------------------|
|------------------|
|| supporting-text||
|------------------|
|------------------|
||    action      ||
|------------------|
--------------------
```

卡片通常具有固定的宽度（默认为330px宽，最小200px高），是一个主轴为竖向的`flex容器`。可以显示地设置其宽度和高度。    
使用`mdl-card`样式类将外层元素声明为卡片组件，使用`mdl-card__title` 等样式类将内层元素声明为标题、媒体、动作等容器：
```
<any class="mdl-card">
  <any class="mdl-card__title">...</any>
  <any class="mdl-card__media">...</any>
  <any class="mdl-card__supporting-text">...</any>
  <any class="mdl-card__actions">...</any>
  <any class="mdl-card__menu">...</any>
</any>
```
title、media、supporting-text和actions作为flex容器成员在垂直方向 上依次排列，其高度是由内容决定，或者被显式地设定。例如，很多时候，我们希望给 title区域增加背景图片以增强感染力，那么将照片设置为title区域的背景之后，还需要 设置title区域的高度：
```
<div class="mdl-card">
    <div class="mdl-card__title" style="background:url(/course/55adae643ad79a1b05dcbf77/img/bg.jpg) no-repeat;backgroud-size:cover;height:150px;">
        ...
    </div>
</div>
```
menu块被设置为绝对定位，总是居于卡片组件的`右上角`。

配置选项：

MDL class | 说明
--------- | ---
mdl-card | 应用在外层容器，声明元素为卡片
mdl-card--border | 为区域增加顶部边框，应用于actions区域和title区域
mdl-shadow--Ndp | 为卡片增加N（2～8）dp的阴影，应用在外层容器
mdl-card__title | 声明容器为卡片标题区域，应用在内层容器
mdl-card__title-text | 为卡片子标题设置和使的样式，应用在卡片标题区域的和
～h6
mdl-card__subtitle-text | 为卡片子标题设置和使的样式
mdl-card__media | 声明容器为卡片媒体区域，应用在内层容器
mdl-card__supporting-text | 声明容器为卡片正文区域，应用在内层容器
mdl-card__actions | 声明容器为卡片政委区域，应用在内层容器
mdl-card__menu | 声明元素为卡片菜单按钮区
mdl-card--expand | 声明区域的flex-grow为1,使容器自动增长以填充卡片剩余空间

##MDL 交互组件

####徽章/Badge

使用徽章：为宿主元素添加mdl-badge样式类，然后在data-badge中设置 徽章内容，如：
```
<any class="mdl-badge" data-badge="1">...</any>
```

配置选项：

MDL class | 说明
--------- | ---
mdl-badge	| 声明当前元素为MDL徽章组件
mdl-badge--no-background | 声明徽章组件不使用背景色
data-badge | 徽章组件使用宿主元素上这个属性值来设置显示内容

####提示框/Tooltip

在MDL中，为一个元素添加Tooltip的步骤如下：
```
<!--1. 为宿主元素定义一个id -->
<button id="test">TEST</button>
<!--2. 声明一个tooltip组件，使用*for*属性绑定到宿主元素上-->
<div class="mdl-tooltip" for="test">这个按钮没什么用;-(</div>
```

配置选项：

MDL class | 说明
--------- | ---
mdl-tooltip	| 声明元素为MDL提示框组件
mdl-tooltip--large | 为MDL提示框组件应用大字体（14px）

####按钮/Button

MDL按钮的显示类型包括：flat, raised, fab, mini-fab, icon. 这些类型 都可以设置为浅灰或彩色，也可以禁止。fab, mini-fab和icon类型的按钮通常 使用一个小图像而不是文字来表征其功能。  
使用按钮组件很简单，为button元素声明mdl-button、mdl-js-button及 其他可选的修饰样式类即可：
```
<!--缺省的扁平/flat按钮-->
<button class="mdl-button mdl-js-button">Save</button>
<!--凸起/raised按钮-->
<button class="mdl-button mdl-js-button mdl-button--raised">Save</button>
<!--浮动动作/FAB按钮-->
<button class="mdl-button mdl-js-button mdl-button--fab">Save</button>
<!--迷你浮动动作/MINI-FAB按钮-->
<button class="mdl-button mdl-js-button mdl-button--fab mdl-button--mini-fab">Save</button>
<!--彩色凸起/raised按钮-->
<button class="mdl-button mdl-js-button mdl-button--raised mdl-button--colored">Save</button>
<!--具有点击动效的凸起/raised按钮-->
<button class="mdl-button mdl-js-button mdl-button--raised mdl-js-ripple-effect">Save</button>
```

配置选项：

MDL的按钮/Button组件是标准HTML元素button的增强版本。

MDL class | 说明
--------- | ---
mdl-button | 将元素声明为MDL按钮组件
mdl-js-button | 为按钮添加基本的行为逻辑
mdl-button--raised | 为按钮应用凸起效果
mdl-button--fab | 将按钮设置为圆形，直径56px
mdl-button--mini-fab | 将fab按钮设置为原型，直径40px
mdl-button--icon | 为按钮应用图标效果，直径32px
mdl-button--colored | 为按钮应用色彩，使用强调色
mdl-button--primary | 为按钮应用基准色
mdl-button--accent | 为按钮应用强调色
dml-js-ripple-effect | 为点击动作应用水文效果

####菜单/Menus

使用`mdl-menu`样式类声明菜单，使用`mdl-menu__item`样式类声明菜单项：
```
<any class="mdl-menu mdl-js-menu">
    <any class="mdl-menu__item">...</any>
    <any class="mdl-menu__item">...</any>
</any>
```

配置选项：

MDL class | 说明
--------- | ---
mdl-button | 声明元素为按钮组件
mdl-js-button | 为按钮组件添加基本逻辑
mdl-button--icon | 使按钮使配图标显示
material-icons | 声明元素为图标
mdl-menu | 声明元素为菜单组件
mdl-menu__item | 声明元素为菜单项
mdl-js-ripple-effect | 为点击动作添加水文效果
mdl-menu--top-left | 在按钮之上显示菜单，菜单左边框与按钮对齐
mdl-menu--top-right | 在按钮之上显示菜单，菜单右边框与按钮对齐
mdl-menu--bottom-left | 在按钮之下显示菜单，菜单左边框与按钮对齐
mdl-menu--bottom-right | 在按钮之下显示菜单，菜单右边框与按钮对齐

####滑动条/Sliders

MDL的滑动条/slider组件是HTML5新增元素range input的增强版本。

为range input元素应用样式类mdl-slider 和mdl-js-slider即可使用MDL的滑动条：
```
<input type="range" min="0" max="100" value="25" class="mdl-slider mdl-js-slider">
```
使用range input元素的min和max属性来设定值的范围，使用value属性来 设置滑动条的初始值

配置选项：

MDL class | 说明
--------- | ---
mdl-slider | 声明元素为滑动条组件
mdl-js-slider	| 为滑动条添加基本的行为逻辑

####复选按钮/Checkbox

MDL的`复选按钮/Checkbox`组件是标准HTML元素`checkbox input`的增强版本。复选按钮组件包含一个标签和一个开关选择按钮  

样式：
```
<!--1.声明组件容器-->
<label class="mdl-checkbox" for="sample">
  <!--2.为checkbox input元素应用mdl样式类-->
  <input type="checkbox" class="mdl-checkbox__input" id="sample">
  <!--为标签元素应用mdl样式类-->
  <span class="mdl-checkbox__label">标签</span>
</label>
```
可以使用`checkbox input`元素的`checked`属性设置复选按钮组件的初始选中状态

配置选项：

MDL class | 说明
--------- | ---
mdl-checkbox | 声明元素为复选按钮
mdl-js-checkbox | 为复选按钮添加基本的行为逻辑
mdl-checkbox__input | 为组件的input子元素使用此样式
mdl-checkbox__label | 为组件的label子元素使用此样式
mdl-js-ripple-effect | 为点击动作添加水纹效果

####单选按钮/Radio button

MDL的单选按钮/RadioButton组件是标准HTML元素radio input的增强版本。 单选按钮组件包含一个标签和一个开关选择按钮

样式:
```
<!--1.声明组件容器-->
<label class="mdl-radio mdl-js-radio">
  <!--2.为input元素应用mdl样式类-->
  <input type="radio" class="mdl-radio__button" name="options" value="1">
  <!--为label子元素应用mdl样式类-->
  <span class="mdl-radio__label">选项1</span>
</label>
<!--选项2-->
<label class="mdl-radio mdl-js-radio">
  <input type="radio" class="mdl-radio__button" name="options" value="2">
  <span class="mdl-radio__label">选项2</span>
</label>
```
和复选按钮类似，使用radio input元素的checked属性设置单选按钮的选中状态

配置选项：

MDL class | 说明
--------- | ---
mdl-radio	| 声明元素为单选按钮
mdl-js-radio | 为单选按钮添加基本的行为逻辑
mdl-radio__button	| 为input元素声明此样式
mdl-radio__label | 为label元素声明此样式
mdl-js-ripple-effect | 为点击动作应用水纹效果

####图标开关/Progress

MDL的图标开关/IconToggle组件是标准HTML元素checkbox input的增强版本。

样式：
```
<!--1.声明容器组件-->
<label class="mdl-icon-toggle mdl-js-icon-toggle">
  <!--2.为checkbox input元素应用mdl样式类-->
  <input type="checkbox" class="mdl-icon-toggle__input">
  <!--3.为图标元素应用mdl样式类-->
  <i class="mdl-icon-toggle__label material-icons">format_bold</i>
</label>
```

配置选项：

MDL class | 说明
--------- | ---
mdl-icon-toggle | 声明元素为图标开关
mdl-js-icon-toggle | 为图标开关添加基本的行为逻辑
mdl-icon-toggle__input | 为input元素声明此样式
mdl-icon-toggle__label | 为label元素声明此样式
mdl-js-ripple-effect | 为点击动作添加水纹效果

####进度条/Progress bar

MDL的进度条/progress bar组件用来提供后台活动的可视化反馈

样式：
```
<any class="mdl-progress mdl-js-progress"></any>
<!--提供用户进度完成的具体百分比-->
<any class="mdl-progress mdl-js-progress mdl-progress__indeterminate"></any>
<!--需要显示进度百分比，需要使用挂接在DOM对象上的MaterialProgress变量的setProgress()方法-->
var el = document.querySelector("#p1");
//setProgress()方法接受一个0～100的值
el.MaterialProgress.setProgress(80);
<!--若需要同时显示一个视频流的缓冲及播放情况，可以使用MaterialProgress变量的setBuffer()方法，这个方法将对未缓冲的部分播放一个动画来表达缓冲效果-->
var el = document.querySelector("#p1");
//setBuffer()方法接受一个0~100的值
el.MaterialProgress.setBuffer(80);
```

配置选项：

MDL class | 说明
--------- | ---
mdl-progress | 声明元素为进度条组件
mdl-js-progress	| 为进度条组件添加基本的行为逻辑
mdl-progress__indeterminate	| 为元素应用动画效果，可选

####等待指示器/Spinner

MDL的等待指示器/spinner组件是等待图标的增强版本，它使用一个边框色彩动态变化 的圆框，清晰地向用户传达作业已经开始、还未完成的状况

样式：
```
<any class="mdl-spinner mdl-js-spinner"></any>
<!--spinner默认是隐藏的，为其应用is-active样式进行激活-->
<any class="mdl-spinner mdl-js-spinner is-active"></any>
```

配置选项:

MDL class	| 说明
mdl-spinner	| 声明元素为spinner组件
mdl-js-spinner | 为spinner增加基本的行为逻辑
is-active	| 显示spinner组件并激活动画
mdl-spinner--single-color	| 只使用单一色彩

####文本输入/Text Field

MDL的文本输入/Text Field组件是对标准HTMLtext input元素的封装

样式：
```
<!--1.声明组件-->
<div class="mdl-textfield mdl-js-textfield">
  <!--2.声明组件的input元素-->
  <input type="text" class="mdl-textfield__input">
  <!--3.声明组件的label元素-->
  <label class="mdl-textfield__label">Your Name</label>
  <!--4.声明组件的error元素-->
  <span class="mdl-textfield__error">Error!</span>
</div>

<!--error元素默认是隐藏的，用来向用户反馈输入的错误。可以为input元素设置 pattern属性（这是HTML5的新特性），当用户的输入与pattern指定的正则 表达式不符时，将显示error元素-->
<input type="text" pattern="-?[0-9]*(\.[0-9]+)?">

<!--默认情况下，当用户开始输入时，标签将消失。可以为组件应用mdl-textfield--floating-label 样式开启浮动标签模式-->
<!--用户输入时，标签将浮动在输入行上方-->
<div class="mdl-textfield mdl-js-textfield mdl-textfield--floating-label">...</div>
<!--也可以将input元素换成textarea元素，这样将允许多行输入-->
<div class="mdl-textfield mdl-js-textfield">
    <!--使用rows属性声明行数-->
    <textarea class="mdl-textfield__input" rows="3"></textarea>
    <label class="mdl-textfield__label">Memo</label>
</div>
```

配备选项：

MDL class | 说明
--------- | ---
mdl-textfield | 声明元素为文本输入组件
mdl-js-textfield | 为文本组件添加基本的行为逻辑
mdl-textfield__input | 为input元素应用此样式
mdl-textfield__label | 为label元素应用此样式
mdl-textfield--floating-label | 为文本输入组件应用浮动标签效果
mdl-textfield__error | 声明span元素为MDL错误信息容器

####文本输入-动态展开式

一种常见的文本输入模式具有一个按钮，点击这个按钮将展开输入框，如果 没有输入内容，那么当输入框失去焦点时将自动隐藏

样式：
```
<!--1.使用expandable样式类声明动态展开的文本输入组件-->
<div class="mdl-textfield mdl-js-textfield mdl-textfield--expandable">
  <!--2.声明出发按钮，使用for属性绑定到input元素-->
  <button class="mdl-button mdl-js-button" for="kw_inp">search</button>
  <!--3.声明文本输入框容器-->
  <div class="mdl-textfield--expandable-holder">
    <input type="text" class="mdl-textfield__input" id="kw_inp">
    <!--5.声明label元素-->
    <label class="mdl-textfield__label">keywords</label>
  </div>
</div>
```

配置选项：

MDL class | 说明
--------- | ---
mdl-textfield--expandable | 声明元素为可展开文本输入组件
mdl-input__expandable_holder | 声明元素为文本输入元素的容器

####数据表/Data table

MDL的数据表/Data table组件用来呈现密集的数据集

样式：
```
<table class="mdl-data-table mdl-js-data-table">
  <thead></thead>
  <tbody></tbody>
</table>
```

配置选项

MDL class | 说明
--------- | ---
mdl-data-table | 声明元素为数据表组件
mdl-js-data-table | 为数据表添加基本的行为逻辑
mdl-data-table--selectable | 为数据表的每一条记录添加复选按钮，应用在table元素上
mdl-data-table__cell--non-numeric | 声明单元格内容非数字，使单元格文字左对齐
