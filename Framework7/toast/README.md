# toast 基于Framework7

### 使用方法

* 引入framework7.toast.js
* 初始化Framework，例如 `var myApp = new Framework7({ ... })`
* `myApp.toast( message, callback, options )`

### 相关参数

     @param text String 展示的文字内容
     @param onClose function 关闭后触发回调
     @param options Object 配置参数
     @param options.duration Number 延迟时间
     @param options.clickClose Boolean 是否允许点击关闭提示