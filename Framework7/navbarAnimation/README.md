# navbarAnimation 基于Framework7

### 使用方法

* 引入framework7.navbarAnimation.js
* 在初始化Framework7的时候，配置插件参数，例如
 
     `var myApp = new Framework7 ({
         navbarAnimation:true
     })`

* 在 `.page` 元素上，添加class `tmod-transparent-navbar`
* 例如 `<div class="page toolbar-fixed tmod-transparent-navbar" data-page="p-index">`

### 相关参数

     @param end Number 滚动到xx像素高度时候，navbar 100%填充颜色
     @param start Number 从xx像素高度开始填充颜色