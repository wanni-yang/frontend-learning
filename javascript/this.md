#### <b>this指向最后调用它的那个对象，没有调用的对象就是全局对象，浏览器中是window</b>
   改变this指向的方法：
   - 使用箭头函数
     箭头函数的this始终指向函数定义时的this,而不是执行时。箭头函数中没有 this 绑定，必须通过查找作用域链来决定其值，如果箭头函数被非箭头函数包含，则 this 绑定的是最近一层非箭头函数的this，否则，this 为 undefined
   - 在函数内部使用 _this = this
     保存调用函数的对象在函数内部的_this中
   - 使用apply call bind
   - new实例化一个对象