# - 阶段性总结，查漏补缺
## 目录
- [js css html](#1-js-css-html)
  - [js](#11-javascript)
  - [css](#12-css)
  - [html](#13-html)
- [浏览器](#2-浏览器)
## 1.js css html
## 1.1 javascript
 - 基本数据类型
 - 内置对象
 - 基本代码规范
 - call/apply
 - Array操作
 - 字符串操作
 - this工作原理
 - 原型/原型链
 - 值的类型/内存图
 - 继承
 - 创建对象方式
 - null/undefined
 - 通用的事件监听函数
 - parseInt
 - 事件
 - 闭包
 - new操作符
 - 函数防抖/节流
   - 节流 throttle
    <p align="center">
      <img src="./img/throttle.webp" alt="节流">
    </p>
    思想：
    某些函数不可以无间断的连续重复执行。
    第一次调用，设定定时器，再指定时间间隔之后执行
    第二次调用，先清除之前的定时器，重新设置一个定时器，
    underscore.js节流源码
    <pre>
    /**
     * 返回一个节流函数，该函数的执行频率会被严格限制，
     * @param func
     * @param wait 等待时间
     * @param options 一些配置
    */
    _.throttle = function (func, wait, options) {
        // 本质上还是通过setTimeout()方法来实现间隔调用的
        // timeout标识最近一次被追踪的调用
        // context和args缓存func执行时需要的上下文，result缓存func执行的result
        var timeout, context, args, result;
        // 最近一次func被调用的时间点
        var previous = 0;
        if (!options) options = {};
        // 创建一个延后执行的函数包裹住func的执行过程， 使得func能够在
        var later = function () {
            // 执行时，刷新最近一次调用时间
            previous = options.leading === false ? 0 : _.now();
            // 清空定时器
            timeout = null;
            result = func.apply(context, args);
            if (!timeout) context = args = null;
        };
        // 返回一个throttled的函数
        var throttled = function () {
            // ----- 节流函数开始执行----
            // 我们尝试调用func时，会首先记录当前时间戳
            var now = _.now();
            // 是否是第一次调用
            if (!previous && options.leading === false) previous = now;
            // func还要等待多久才能被调用 =  预设的最小等待期-（当前时间-上一次调用的时间）
            // 显然，如果第一次调用，且未设置options.leading = false，那么remaing=0，func会被立即执行
            var remaining = wait - (now - previous);
            // 记录之后执行时需要的上下文和参数
            context = this;
            args = arguments;
            // 如果计算后能被立即执行
            if (remaining <= 0 || remaining > wait) {
                // 清除之前的“最新调用”
                if (timeout) {
                    clearTimeout(timeout);
                    timeout = null;
                }
                // 刷新最近一次func调用的时间点
                previous = now;
                // 执行func调用
                result = func.apply(context, args);
                // 如果timeout被清空了，
                if (!timeout) context = args = null;
            } else if (!timeout && options.trailing !== false) {
                // 如果设置了trailing edge，那么暂缓此次调用尝试的执行
                timeout = setTimeout(later, remaining);
            }
            return result;
        };
        // 可以取消函数的节流化
        throttled.cancel = function () {
            clearTimeout(timeout);
            previous = 0;
            timeout = context = args = null;
        };
        return throttled;
    }; 
    </pre>
   - 防抖 debounce
    <p align="center">
      <img src="./img/debounce.webp" alt="防抖">
    </p>
    underscore.js节流源码
    <pre>
    /**
     * throttle函数的防反跳版本
     * 从下面的debounce实现我们可以看到，
     * 不同于throttle，debounce不再计算remain时间，
     * 其提供的__immediate__参数类似于throttle中的对于leading-edge和trailing-edge的控制：
     *
     * - immediate === true，开启leading-edge，当可以执行时立即执行
     * - immediate === false（默认）开启trailing-edge，当可以执行时也必须延后至少wait个时间才能执行。
     *
     * 因此，debounce后的func要么立即获得响应，要么延迟一段时间才响应，
     * @param {Function} func 需要防止反跳的函数
     * @param {Number} wait 等待时间
     * @param {Boolean} immediate 是否允许立即执行，如果设置为true，那么如果之前的调用都执行完毕，本次调用可以立即执行
     *
     */
    _.debounce = function (func, wait, immediate) {
        var timeout, result;
        var later = function (context, args) {
            timeout = null;
            if (args) result = func.apply(context, args);
        };
        var debounced = restArgs(function (args) {
            // 一旦存在timeout， 意味之前尝试调用过func
            // 由于debounce只认最新的一次调用， 所以之前等待执行的func都会被终止
            if (timeout) clearTimeout(timeout);
            // 如果允许新的调用尝试立即执行，
            if (immediate) {
                // 如果之前尚没有调用尝试，那么此次调用可以立马执行，否则一定得等待之前的执行完毕
                var callNow = !timeout;
                // 刷新timeout
                timeout = setTimeout(later, wait);
                // 如果能被立即执行，立即执行
                if (callNow) result = func.apply(this, args);
            } else {
                // 否则，这次尝试调用会延时wait个时间
                timeout = _.delay(later, wait, this, args);
            }
            return result;
        });
        debounced.cancel = function () {
            clearTimeout(timeout);
            timeout = null;
        };
        return debounced;
    };
</pre>
 - 参数验证
 - 函数柯里化

 - bind函数原理
## 1.2 css
 - 盒模型
 - 水平居中/垂直居中
 - 选择器/属性继承
 - 选择器优先级
 - css3新增伪类
 - display
 - position
 - css3新特性
 - 兼容性
 - BFC规范
 - css阻塞
 - hack写法
 - 初始化css样式
 - 伪类/伪元素
## 1.3 html
 - 语义化标签
 - canvas
 - video/audio
 - localStorage/sessionStorage
 - webWorker/webSocket/Geolocation
 - iframe
 - 兼容性
## 2. 浏览器
 - 描述一个网页从请求到显示的完整过程
 - 浏览器内核
 - 浏览器内多个标签页之间的通信
 - webSocket如何兼容低浏览器
 - 跨域
 - 重排/重绘
 - 检测浏览器版本
 - 错误类型
## 5. JSON
## 6. AJAX
 - 创建ajax
 - callback类型
## 7. ECMAScript6
 - ES6 class
 - 同步/异步
## 8. 模块规范
 - CommonJS
 - AMD
 - CMD
## 9. 框架
 - MVC
 - MVVM
## 10. HTTP/HTTPS
 - 状态码
## 11. web安全
 - XSS
 - SQL注入
 - CSRF
 - 