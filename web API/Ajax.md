### 是什么

> Ajax 全称 Asynchronous JavaScript and XML, 即异步JS与XML. 它最早在IE5中被使用, 然后由Mozilla, Apple, Google推广开来. 典型的代表应用有 Outlook Web Access, 以及 GMail. 现代网页中几乎无ajax不欢. 前后端分离也正是建立在ajax异步通信的基础之上.标准浏览器通过XMLHttpRequest对象实现ajax功能

> new XMLHtttpRequest实例对象xhr来源追溯一下： xhr 继承自 XMLHttpRequest.prototype 继承自 XMLHttpRequestEventTarget.prototype 继承自 EventTarget.prototype 继承自 Object.prototype

### XMLHttpRequest原型属性
|属性名|类型|说明
|-|-|-
|onreadystatechange||onreadystatechange事件回调方法在readystate状态改变时触发, 在一个收到响应的ajax请求周期中, onreadystatechange 方法会被触发4次. 因此可以在 onreadystatechange 方法中绑定一些事件回调
|readyState||0	xhr.UNSENT (未初始化)	  请求已建立，未初始化。open()方法还未被调用.</br>1	xhr.OPENED(未发送)  请求已建立，未发送。	open()方法已经被调用，未调用send方法.</br>2	xhr.HEADERS_RECEIVED (已获取响应头) 请求已发送。 send()方法已经被调用, 响应头和响应状态已经返回. </br> 3	xhr.LOADING (正在下载响应体) 请求处理中。 responseText中已经获取了部分数据.</br>4	xhr.DONE (请求完成)	整个请求过程已经完毕.此时可以通过responseBody和responseText获取完整的响应数据
|response||响应内容
|responseText||响应内容文本形式
|responseType||响应类型 可取 "arraybuffer" , "blob" , "document" , "json" , and "text" 共五种类型
|responseXML||xml形式响应数据
|status||http请求状态码
|status| UTF-16 的字符串|请求状态描述
|upload|默认返回一个 XMLHttpRequestUpload 对象|可以在 upload 上添加一个事件监听来跟踪上传过程。其方法见 XMLHttpRequestEventTarget事件接口属性</br><pre>xhr.upload.onprogress = function(e){</br>var percent = 100 * e.loaded / e.total |0;</br> console.log('upload: ' + precent + '%');</br>}</pre>
|withCredentials|bool|默认false表示跨域请求中不发送cookie等，true表示cookies , authorization headers 或者TLS客户端证书 都可以正常发送和接收
|timeout|0不生效，可以转为数字的生效|用于指定ajax的超时时长. 通过它可以灵活地控制ajax请求时间的上限.

### XMLHttpRequest原型方法
|方法名|参数|返回值|说明
|-|-|-|-
|abort|-||如果请求已经被发送,则立刻中止请求.readyState 状态将被设置为 0 (UNSENT)
|getAllResponseHeaders|-|返回所有响应头信息(响应头名和值), 如果响应头还没接受,则返回null|每个HTTP报头名称和值用冒号分隔, 如key:value, 并以\r\n结束
|getResponseHeader|DOMString header|返回指定的响应头的值, 如果响应头还没被接受,或该响应头不存在,则返回null.|
|open|method.url,async||在一个已经激活的request下（已经调用open()或者openRequest()方法的request）再次调用这个方法相当于调用了abort（）方法
|overrideMimeType|DOMString mimetype||重写由服务器返回的MIME type。这个可用于, 例如，强制把一个响应流当作“text/xml”来处理和解析,即使服务器没有指明数据是这个类型。注意，这个方法必须在send()之前被调用
|send|||发送请求. 如果该请求是异步模式(默认),该方法会立刻返回. 相反,如果请求是同步模式,则直到请求的响应完全接受以后,该方法才会返回.
|setRequestHeader|header,value||xhr.setRequestHeader("Content-type", "application/json");

### XMLHttpRequestEventTarget事件接口属性

|属性名|说明
|-|-
|onloadstart|事件回调方法触发在ajax请求发送之前， 触发时机在 readyState==1 --- readyState==2之间，默认将传入一个ProgressEvent事件进度对象，该对象有3个属性，lengthComputer长度是否可计算，loaded已加载资源大小，total资源，内容总大小
|onprocess|事件回调方法在 readyState==3 状态时开始触发, 默认传入 ProgressEvent 对象, 可通过 e.loaded/e.total 来计算加载资源的进度, 该方法用于获取资源的下载进度
|onload|事件回调方法在ajax请求成功后触发, 触发时机在 readyState==4 状态之后
|onloadend|事件回调方法在ajax请求完成后触发, 触发时机在 readyState==4 状态之后(收到响应时) 或者 readyState==2 状态之后(未收到响应时)默认将传入一个ProgressEvent事件进度对象
|ontimeout|方法在ajax请求超时时触发, 通过它可以在ajax请求超时时做一些后续处理
|onerror|ajax请求出错后执行. 通常只在网络出现问题时或者ERR_CONNECTION_RESET时触发

### XHR level 1 & XHR level 2

  level1
- 仅支持文本数据传输，不支持二进制数据
- 传输数据时，没有进度提示
- 受浏览器同源策略限制，只能请求同域资源
- 没有超时机制
    
  level 2
- 支持二进制数据，可以上传文件，可以使用FormData对象管理表单
- 可以通过xhr.upload.onprogress事件回调方法获取传输进度
- 同源策略依旧生效，提供Access-Control-Allow-Origin等heades设置为* 表示允许任何域名请求从而实现跨域访问
- 可以设置timeout ontimeout，可以控制超时时长和超时后处理

### $.ajax

$.ajax是对原生ajax的封装



### 发起ajax,浏览器各线程之间的情况
<p align="center">
    <img src="../img/ajax.png" alt="ajax">
</p>
