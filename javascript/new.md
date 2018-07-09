new constructor[([arguments])]
当代码 new Foo(...) 执行时，会发生以下事情：
<pre>
    var obj = {}
    obj.__proto__ = F.prototype
    F.call(obj)
</pre>
- 创建一个空对象 obj（一个继承自 constructor.prototype 的新对象）;this指向该对象
- 将新创建的空对象的隐式原型指向其构造函数的显示原型。
- 使用 call 改变 this的指向，将F对象的this替换为obj调用F
- 如果无返回值或者返回一个非对象值，则将 obj返回作为新对象；如果返回值是一个新对象的话那么直接直接返回该对象
### 规范解释
> 1.引擎将先创建一个语言原生对象，即“{}”或“new Object”，在此我们称之为 O，然后设置其内部属性标识 [[Class]] 为“Object”。接下来，得到构造器 F 的 prototype（根据后文的意思，它可能不是一个对象）。如果 F.prototype 是对象，那么将 O 的内部 [[Prototype]] 属性指向 F.prototype。

> 2. 请注意，诸如 [[Prototype]] 等为引擎内部标识符，对我们并不可见。[[Prototype]] 正是用于给内部维护原型链，虽然在我们看来，一个对象实例无法直接回溯到其原型（然而引擎内部可以），必须通过构造器中转，即 obj.constructor.prototype。

> 3. 接着，如果 F.prototype 不是 object，那么将 O 的内部 [[Prototype]] 属性指向“the Object prototype object”（你可以参考这里）。等到 O 的 [[Prototype]] 有了自己的归属以后，引擎调用构造器 F 的 [[Call]] 内部方法，以 O 作为 this 对象，并将传入 [[Construct]] 的参数作为入口参数——如果有的话（即诸如“new Object()”最后括号内的参数）传递过去。最后，如果 [[Call]] 的返回值是对象，那么创建成功并返回此对象，否则回头重来。
<pre>
function MyObject(age) {
    this.age = age;
}

MyObject.construct = function() {
    var o = {}, Constructor = MyObject;
    o.__proto__ = Constructor.prototype;
    // FF 支持用户引用内部属性 [[Prototype]]

    Constructor.apply(o, arguments);
    return o;
};

var obj1 = new MyObject(10);
var obj2 = MyObject.construct(10);
alert(obj2 instanceof MyObject);
// true
</pre>

### 函数调用
- 作为函数调用
    一个最简单的全局函数，不属于任何一个对象，就是一个函数，这样的情况浏览器中的非严格模式默认是属于全局对象window的，在严格模式，就是 undefined。 
- 作为方法调用
   函数作为一个对象的方法被调用
- 使用构造函数调用
    new操作符调用构造函数创建一个对象
- 作为函数方法调用函数(apply call)
