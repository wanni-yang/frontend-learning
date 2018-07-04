### 是什么

> 所有非箭头函数中都可用的局部变量，可以通过arguments[下标]去访问函数参数，是一个类数组对象，只有length属性和索引元素

<pre>
Array.prototype.slice.call(arguments) or
[].slice.call(arguments) or
Array.from(arguments) or
[...arguments]将arguments对象转为真正的数组
<b>性能好一些的</b>可以通过遍历arguments对象来构造一个新的数组
arguments.length === 1 ? [arguments[0]] : Array.call(null,arguments)
</pre>

### 属性

- length
  
  arguments.length可以确定传递给函数参数的个数，函数签名（MyObject.prototype.myFunction(value)）中参数数量用Function.length
  
- callee
  
  指向当前执行的函数

### 用法
 
 - 函数内部使用参数
 - 定义连接字符串的函数
 
 <pre>
 /**
 参数：只是声明了用来连接字符串的字符
 /
 function selfJoin(separator){
    var args = [].slice.call(arguments,1);
    return args.join(separator);
 }
 selfJoin(',','mie','qc','ss');
 </pre>

- 定义创建HTML列表

  <pre>
   /**
   参数：只是声明了列表类型
   /
   function list(type){
      var listhtml = "<" +type+"l><li";
      var args = [].slice.call(arguments,1);
      listhtml += args.join('<li></li>');
      listhtml += "</li></"+ type+"l>";

      return listhtml;
   }
   var listHTML = list("u", "One", "Two", "Three");
  </pre>
 
 - 与剩余参数、默认参数和解构赋值参数结合使用
 
 > 在严格模式下，剩余参数、默认参数和解构赋值参数的存在不会改变 arguments对象的行为，但是当非严格模式中的函数没有包含剩余参数、默认参数和解构赋值，
 那么arguments对象中的值会跟踪参数的值（反之亦然）
