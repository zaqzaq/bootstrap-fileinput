bootstrap-fileinput
===================

[![Bower version](https://badge.fury.io/bo/bootstrap-fileinput.svg)](http://badge.fury.io/bo/bootstrap-fileinput)
[![Latest Stable Version](https://poser.pugx.org/kartik-v/bootstrap-fileinput/v/stable)](https://packagist.org/packages/kartik-v/bootstrap-fileinput)
[![License](https://poser.pugx.org/kartik-v/bootstrap-fileinput/license)](https://packagist.org/packages/kartik-v/bootstrap-fileinput)
[![Packagist Downloads](https://poser.pugx.org/kartik-v/bootstrap-fileinput/downloads)](https://packagist.org/packages/kartik-v/bootstrap-fileinput)
[![Monthly Downloads](https://poser.pugx.org/kartik-v/bootstrap-fileinput/d/monthly)](https://packagist.org/packages/kartik-v/bootstrap-fileinput)

# 扩展 支持 跨域 上传 文件

## 需要 引入的 文件
   `<link href="css/fileinput.min.css" media="all" rel="stylesheet" type="text/css" />`
   
   `<link href="css/bootstrap3.css" media="all" rel="stylesheet" type="text/css" /> //针对bootstrap 2+ 版本`
   
   `<script src="js/fileinput.js" type="text/javascript"></script>`
    
   `<script src="js/locales/zh.js" type="text/javascript"></script>`
   
   `<script src="js/jquery.iframe-transport.js" type="text/javascript"></script>`
    
## html UI节点    
   `<input id="filePicker" type="file" class="file-loading" title="选择图片">`
   
## JS DEMO 上传文件
    $("input[type='file']").fileinput({
        language : 'zh',
        uploadUrl: uploadUrl,
        initialPreview: initialPreviewArray,
        initialPreviewAsData: true,
        initialPreviewFileType: 'image',
        overwriteInitial: true,
        ajaxSettings:{
            extraData:{
                redirect:location.origin+"/fileinput/cors/result.html"
            }
        },
        allowedFileExtensions : ['jpg', 'png','gif','jpeg','bmp'],
        allowedFileTypes: ['image'],
        showUpload: false,
        slugCallback: function(filename) {//选择后未上传前 回调方法
            return filename.replace('(', '_').replace(']', '_');
        }
    }).on("fileuploaded", function(event, data){//上传成功事件
        console.log("上传成功")
        console.log(data.response)
    });

## 上传服务器后台 关键代码
   `String retVal=Urlencode.encode(returnJson);`
   
   `response.sendRedirect(redirect+"?\"retVal\"")`
   
   `注：redirect 为前台的入参回调url ,returnJson 上传后返回的消息`
   
### 贴上 修改 动态修改 fileinput 配置属性 的demo代码
   `$("input[type='file']").data('fileinput').options.uploadUrl=“xxx.xx” //将上传的路径修改成xxx.xx`
   
   
