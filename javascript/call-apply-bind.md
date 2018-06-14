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