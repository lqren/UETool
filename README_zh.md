UETool ![](https://img.shields.io/badge/platform-android-lightgrey.svg) [![License](https://img.shields.io/badge/license-MIT-000000.svg)](https://github.elenet.me/waimai/UETool/blob/master/LICENSE) 
======

![](https://github.elenet.me/waimai/UETool/blob/master/art/uet_banner.jpeg)

## 介绍

UETool 是一个各方人员（设计师、程序员、测试）都可以使用的调试工具。它可以作用于任何显示在屏幕上的 view，比如 Activity/Fragment/Dialog/PopupWindow 等等。

目前 UETool 提供以下功能：

- 移动屏幕上的任意 view，如果重复选中一个 view，将会选中其父 view
- 查看/修改常用控件的属性，比如修改 TextView 的文本内容、文本大小、文本颜色等等
- 如果你的项目里正在使用 Fresco 的 DraweeView 来呈现图片，那么 UETool 将会提供更多的属性比如图片 URI、默认占位图、圆角大小等等
- 你可以很轻松的定制任何 view 的属性，比如你想查看一些额外的业务参数
- 显示两个 view 的相对位置关系
- 显示网格栅栏，方便查看控件是否对齐

## 效果

<div>
<img width="270" height="480" src="https://github.elenet.me/waimai/UETool/blob/master/art/move_view.gif"/>

<img width="270" height="480" src="https://github.elenet.me/waimai/UETool/blob/master/art/show_image_uri.gif"/>

<br/>

<img width="270" height="480" src="https://github.elenet.me/waimai/UETool/blob/master/art/relative_position.gif"/>

<img width="270" height="480" src="https://github.elenet.me/waimai/UETool/blob/master/art/show_gridding.png"/>
</div>


## 属性列表

| Attribute | Value Sample | Editable |
| --- | --- | --- |
| Class | android.widget.LinearLayout |  |
| Id | 0x7f0d009c |  |
| ResName | btn |  |
| Clickble | TRUE |  |
| Focoused | FALSE |  |
| Width(dp) | 107 | YES |
| Height(dp) | 19 | YES |
| Alpha | 1.0 |  |
| PaddingLeft(dp) | 10 | YES |
| PaddingRight(dp) | 10 | YES |
| PaddingTop(dp) | 10 | YES |
| PaddingBottom(dp) | 10 | YES |
| Background | #90000000 <br/> #FF8F8F8F -> #FF688FDB <br/> [PICTURE] 300px*300px |  |
| **TextView** |  |  |
| Text | Hello World | YES |
| TextSize(sp) | 14 | YES |
| TextColor | #DE000000 | YES |
| IsBold | TRUE | YES |
| SpanBitmap | [PICTURE] 72px*39px | |
| DrawableLeft | [PICTURE] 51px*51px |  |
| DrawableRight | [PICTURE] 36px*36px |  |
| **ImageView** |  |  |
| Bitmap | [PICTURE] 144px*144px |  |
| ScaleType | CENTER_CROP |  |
| **DraweeView** |  |  |
| CornerRadius | 2dp |  |
| ImageURI | https://avatars2.githubusercontent.com/u/1201438?s=200&v=4 |  |
| ActualScaleType | CENTER_CROP |  |
| IsSupportAnimation | TRUE |  |
| PlaceHolderImage | [PICTURE] 300px*300px |  |
|  |  |  |


## 如何使用

### 安装依赖

```gradle
dependencies {
  debugCompile 'me.ele:uetool:1.0.12'
  releaseCompile 'me.ele:uetool-no-op:1.0.12'

  // if you want to show more attrs about Fresco's DraweeView
  debugCompile 'me.ele:uetool-fresco:1.0.12'
}
```

### 使用

#### 打开悬浮窗

```java
UETool.showUETMenu();

UETool.showUETMenu(int y);
```

#### 关掉悬浮窗

```java
UETool.dismissUETMenu();
```

#### 过滤掉你不需要选中的 View

```java
UETool.putFilterClass(Class viewClazz);

UETool.putFilterClass(String viewClassName);
```

#### 自定义实现你的 View 的属性

```java

// step 1, implements IAttrs

public class UETFresco implements IAttrs {
  @Override public List<Item> getAttrs(Element element) {

  }
}

// step 2, put in UETool

UETool.putAttrsProviderClass(Class customizeClazz);

UETool.putAttrsProviderClass(String customizeClassName);

```

## License

![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/License_icon-mit-88x31-2.svg/128px-License_icon-mit-88x31-2.svg.png)

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

