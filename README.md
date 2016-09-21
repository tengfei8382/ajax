### ajax

独立的ajax库,可单独使用,支持cors/JSONP等跨域请求

#### demo

    git clone https://github.com/rwson/ajax
    
    cd ajax
    
    cd example
    
    npm install
    
    node index.js
    
    //  开一个新的Terminal Tab,切换到server2 目录下,启动服务,模拟跨域请求
    
    cd ../server2
    
    npm install
    
    node index
    

#### Usage

    //  common script tag
    <script src="path/to/ajax.js"></script>
    <script>
        
        //  ...
        
        ajax({
            //  ...
        });
        
        //  ...
        
    </script>

    //  require.js
    require(["ajax", ....], function(ajax, ...) {
        
        //  ...
        
        ajax({
            //  ...
        });
        
        //  ...
        
    });

在ajax/example/example.js文件中可以看到完整的调用例子

#### API


属性名 | 含义 | 类型 | 默认 | 是否必须
---|---|---|---|---
url | 请求地址 | String | 当前页面的地址 | 是
method | 数据发送方式 | String | "GET" | 否
data | 要传递给后端的数据 | Object | {} | 否
headers | 请求头设置 | String | 当前页面的地址 | 是
dataType | 后端返回的数据类型 | String | "json" | 否
withCredentials | 是否允许跨域请求(如果设置了cookie,可以带cookie证书) | Boolean | false | 否
timeout | 超时时间(ms,为-1的时候表示不设置超时时间) | Number | -1 | 否
async | 是否异步 | Boolean | true | 否
context | 回调函数中的this指向 | Object | window | 否
before | 发送请求之前的回调 | FUnction | N/A | 否
success | 服务端响应成功后的回调 | Function | N/A | 否
error | 服务端响应失败后的回调 | Function | N/A | 否
abort | 服务端响应超时后的回调,设置了有效的timeout才有效 | Function | N/A | 否

- dataType的可选值有"json"、 "text"、"script"、"xml"、"jsonp"五个可选值

###### 回调函数参数

    //  before
    //  无参数
    before: function() {
    }

    //  success
    //  当dataType为"jsonp"时,xhr无效
    //  其他情况,xhr为XMLHttpRequest实例
    success: function(res, xhr) {
    }
    
    //  error
    //  此回调在dataType非"jsonp"情况下有效
    error: function(res, ex, xhr) {
    }
    
    //  abort
    //  当dataType为"jsonp"时,xhr无效
    //  其他情况,xhr为XMLHttpRequest实例
    abort: function(xhr) {}
