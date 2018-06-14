 - 基本数据类型
    - undefiend
    - null
    - boolean
    - number
    - string
    - object
    - symbol
 - 内置对象
    - Array操作
    - String操作
 - 基本代码规范
 - call/apply/bind
   #### call()
    - call() 方法调用一个函数,其具有一个指定的this值和分别地提供的参数(参数的列表)。
    - 语法fun.call(thisArg, arg1, arg2, ...)
      thisArg
    在fun函数运行时指定的this值。需要注意的是，指定的this值并不一定是该函数执行时真正的this值，<b>如果这个函数处于非严格模式下，则指定为null和undefined的this值会自动指向全局对象(浏览器中就是window对象)，</b>同时值为原始值(数字，字符串，布尔值)的this会指向该原始值的自动包装对象。
    - 返回值：你调用的方法的返回值，若该方法没有返回值，则返回undefined。
   #### apply()
    - apply() 方法调用一个函数, 其具有一个指定的this值，以及作为一个数组（或类似数组的对象）提供的参数。
    - func.apply(thisArg, [argsArray])
    - 返回值：调用有指定this值和参数的函数的结果。
   call()方法的作用和 apply() 方法类似，只有一个区别，就是 call()方法接受的是若干个参数的列表，而apply()方法接受的是一个包含多个参数的数组
   #### bind()
   bind() 函数会创建一个新函数（称为绑定函数），新函数与被调函数（绑定函数的目标函数）具有相同的函数体（在 ECMAScript 5 规范中内置的call属性）。当新函数被调用时 this 值绑定到 bind() 的第一个参数，该参数不能被重写。绑定函数被调用时，bind() 也接受预设的参数提供给原函数。一个绑定函数也能使用new操作符创建对象：这种行为就像把原函数当成构造器。提供的 this 值被忽略，同时调用时的参数被提供给模拟函数
   - fun.bind(thisArg[, arg1[, arg2[, ...]]])
    thisArg
    当绑定函数被调用时，该参数会作为原函数运行时的 this 指向。当使用new 操作符调用绑定函数时，该参数无效。
   - 返回值：由指定的this值和初始化参数改造的原函数拷贝。<b>需要手动调用</b>
   - 使用场景
     - 创建绑定函数：bind() 最简单的用法是创建一个函数，使这个函数不论怎么调用都有同样的 this 值。
     - 偏函数：bind()的另一个最简单的用法是使一个函数拥有预设的初始参数。这些参数（如果有的话）作为bind()的第二个参数跟在this（或其他对象）后面，之后它们会被插入到目标函数的参数列表的开始位置，传递给绑定函数的参数会跟在它们的后面。
     - 配合setTimeout:在默认情况下，使用 window.setTimeout() 时，this 关键字会指向 window （或全局）对象。当使用类的方法时，需要 this 引用类的实例，你可能需要显式地把 this 绑定到回调函数以便继续使用实例。
   <pre>
    underscore.js
       _.bind = function (func, context) {
            if (nativeBind && func.bind === nativeBind) return nativeBind.apply(func, slice.call(arguments, 1));
            if (!_.isFunction(func)) throw new TypeError('Bind must be called on a function');
            var args = slice.call(arguments, 2);
            var bound = function () {
                return executeBound(func, bound, context, this, args.concat(slice.call(arguments)));
            };
            return bound;
        };
    _.bindAll(obj)：绑定对象 obj 的所有指定成员方法中的执行上下文到 obj
    _.bindAll = function (obj) {
        var i, length = arguments.length,
            key;
        if (length <= 1) throw new Error('bindAll must be passed function names');
        for (i = 1; i < length; i++) {
            key = arguments[i];
            obj[key] = _.bind(obj[key], obj);
        }
        return obj;
    };
    e.g.
    var button = {
        title: 'button#1',
        onClick: function() {
            console.log(this.title + ' has been clicked!');
        },
        onHover: function() {
            console.log(this.title + ' hovering!');
        }
    }
    _.bindAll(button, 'onClick', 'onHover');
    setTimeout(button.onClick, 0);
    setTimeout(button.onHover, 0);
    // => "button#1 has been clicked!"
    // => "button#1 hovering!"
   </pre>
 
 - this工作原理
   #### <b>this指向最后调用它的那个对象，没有调用的对象就是全局对象，浏览器中是window</b>
   改变this指向的方法：
   - 使用箭头函数
     箭头函数的this始终指向函数定义时的this,而不是执行时。箭头函数中没有 this 绑定，必须通过查找作用域链来决定其值，如果箭头函数被非箭头函数包含，则 this 绑定的是最近一层非箭头函数的this，否则，this 为 undefined
   - 在函数内部使用 _this = this
     保存调用函数的对象在函数内部的_this中
   - 使用apply call bind
   - new实例化一个对象
 - 原型/原型链
    <p align="center">
      <img src="./img/prototype-chain.png" alt="原型链">
    </p>
 - 值的类型/内存图
    
 - 继承
 - 创建对象方式
 - null/undefined
 - 通用的事件监听函数
 - parseInt
 - 闭包
 - new操作符
    new constructor[([arguments])]
    当代码 new Foo(...) 执行时，会发生以下事情：
    - 创建一个空对象 obj（一个继承自 constructor.prototype 的新对象）;
    - 将新创建的空对象的隐式原型指向其构造函数的显示原型。
    - 使用 call 改变 this的指向
    - 如果无返回值或者返回一个非对象值，则将 obj返回作为新对象；如果返回值是一个新对象的话那么直接直接返回该对象
 - 函数调用
    - 作为函数调用
        一个最简单的全局函数，不属于任何一个对象，就是一个函数，这样的情况浏览器中的非严格模式默认是属于全局对象window的，在严格模式，就是 undefined。 
    - 作为方法调用
       函数作为一个对象的方法被调用
    - 使用构造函数调用
        new操作符调用构造函数创建一个对象
    - 作为函数方法调用函数(apply call)
 - 函数防抖/节流
   - 节流 throttle
    <p align="center">
      <img src="./img/throttle.webp" alt="节流">
    </p>
    思想：
    某些函数不可以无间断的连续重复执行。
    第一次调用，设定定时器，再指定时间间隔之后执行
    第二次调用，先清除之前的定时器，重新设置一个定时器，
    <pre>underscore.js节流源码
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
    underscore.js防抖源码
    <pre>
    /**
     * throttle函数的防抖版本
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
    使用debounce，throttle和requestAnimationFrame优化你的事件处理程序。每种技术都略有不同，但它们都有用，互补。
    综上所述：
    防抖：将突发事件（如击键）分组为一个单一的事件。
    节流：每X毫秒保证持续的执行流量。就像每200毫秒检查一次滚动位置来触发CSS动画。
    requestAnimationFrame：节流替代品。当你的函数重新计算和渲染屏幕上的元素，并且你想保证平滑的变化或动画。注意：不支持IE9。
 - 参数验证
 - 函数柯里化