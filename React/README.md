# React Component
React components
# Getting started
## Usage  

```javascript

import FileUpload from '@components/file-upload';
      <FileUpload
        fileUrl={'xxx/xxx/demo.jpeg'}
        fileName={'demo.jpeg'}
        displayOnly={true}
        preview={true}
      /> 
```  

## Options
### fileUrl  
- Type: string
- 文件绝对路径

### fileName  
- Type: string
- 文件名

### preview  
- Type: booean
- 点击缩略图查阅大图
- 使用 [react-image-lightbox](https://github.com/frontend-collective/react-image-lightbox) 进行大图查看

### displayOnly  
- Type: booean
- 是否为纯展示的情况

### compressImg  
- Type: booean
- 是否压缩图片，*仅当`displayOnly`为`false`时候生效*
- 使用 [compressorjs](https://github.com/fengyuanchen/compressorjs) 进行压缩，默认使用0.8压缩率

### download  
- Type: booean
- 是否支持下载附件 *仅当`displayOnly`为`true`时候生效*

### onFileDelete  
- Type: function
- 点击删除按钮后的回调 *仅当`displayOnly`为`false`时候生效*

### onAfterUpload  
- Type: (url: string, name: string) => void
	- url 文件的绝对路径
	- name 文件名
- 文件上传成功的回调 *仅当`displayOnly`为`false`时候生效*

## Preview
![示例图: 编辑模式，图片附件](https://i.bmp.ovh/imgs/2019/11/20ce1d9429a1b5c7.png)  

![示例图: 预览模式，非图片附件](https://i.bmp.ovh/imgs/2019/11/f61ecc74c0b22cfe.png)

