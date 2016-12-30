# ajaxfileupload
jquery.ajaxfileupload

jQuery的上传插件，因原版有BUG且无人维护，所以自己留在这里备用，同时我修复了些BUG。


USE:
```html
<img class="img" src="http://chisheng.oss-cn-shanghai.aliyuncs.com/chisheng/201612302e6ef0d9@!m" alt="">
<input type="hidden" id="doctor-business_license" name="Doctor[business_license]" value="201612302e6ef0d9">

<input style="display: none" type="file" id="uploadInput" name="imagefile" />
<script>
$('.img').click(function(){
    upload(this);
});
function upload(obj){
    $('#uploadInput').click().unbind('change').change(function(){
        $.ajaxFileUpload({
            url:'{$upload_url}',//用于文件上传的服务器端请求地址
            secureuri:false,//一般设置为false
            fileElementId:'uploadInput',//文件上传控件的id属性
            dataType: 'json',
            success: function (data, status)  //服务器成功响应处理函数
            {
                console.log (data);
                $(obj).attr('src', data.murl).next('input').val(data.path);
            	
            },
            error: function (data, status, e)//服务器响应失败处理函数
            {
                console.log(e);
            }
        });
    });
}
</script>
```
