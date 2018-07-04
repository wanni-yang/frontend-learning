### 是什么

> Object构造函数为给定值创建一个对象包装器。如果给定值是 null 或 undefined，将会创建并返回一个空对象，否则，将返回一个与给定值对应类型的对象。
当以非构造函数形式被调用时，Object 等同于 new Object()。


### 参数

- nameValuePair1,nameValuePair2,...nameValuePairN 成对的名称（字符串）与值（任何值），其中名称通过冒号与值分隔。
- value 任何值

### 构造函数属性

|属性名|说明
|-|-
|length|值为1
|prototype|

### 构造函数方法

|方法名|参数|返回值|说明
|-|-|-|-
|assign()|target, ...sources|目标对象|通过复制一个或多个对象来创建一个新的对象,只会拷贝源对象自身的并且可枚举的属性到目标对象
|create()|proto,propertiesObject or undefined|一个新对象，带着指定的原型对象和属性|使用指定的原型对象和属性创建一个新对象,如果propertiesObject参数不是 null 或一个对象，则抛出一个 TypeError 异常
|defineProperty()|obj,prop,decriptor| 被传递给函数的对象|给对象添加一个属性并指定该属性的配置
|defineProperties()|obj,props|传递给函数的对象|给对象添加多个属性并分别指定它们的配置
|entries()|obj|数组|返回给定对象自身可枚举属性的[key, value]数组
|freeze()|obj|被冻结的对象|冻结对象：其他代码不能删除或更改任何属性
|getOwnPropertyDescription()|obj,prop|属性描述符对象 or undefined|返回对象指定的属性配置
|getOwnPropertyNames()|obj|在给定对象上找到的属性对应的字符串数组|返回一个数组，它包含了指定对象所有的可枚举或不可枚举的属性名但不包括Symbol值作为名称的属性
|getOwnPropertySymbols()|obj|在给定对象自身上找到的所有 Symbol 属性的数组|返回一个数组，它包含了指定对象自身所有的符号属性
|getPrototypeOf()|obj|给定对象的原型。如果没有继承属性，则返回 null|返回指定对象的原型对象Object.getPrototypeOf(Object)不是Object.prototype
|is()|value1,value2|true or false|比较两个值是否相同。所有 NaN 值都相等（这与==和===不同）两个值都是 undefined两个值都是 null两个值都是 true 或者都是 false两个值是由相同个数的字符按照相同的顺序组成的字符串两个值指向同一个对象两个值都是数字并且都是正零 +0都是负零 -0都是 NaN都是除零和 NaN 外的其它同一个数字
|isExtensible()|obj|true or false|判断对象是否可扩展
|isFrozen()|obj|true or false|判断对象是否已经冻结
|isSealed()|obj|true or false|判断对象是否已经密封
|keys()|obj|一个表示给定对象的所有可枚举属性的字符串数组|返回一个包含所有给定对象自身<b>可枚举</b>属性名称的数组
|values()|obj|一个包含对象自身的所有可枚举属性值的数组|返回给定对象自身可枚举值的数组
|preventExtensions()|obj|已经不可扩展的对象|防止对象的任何扩展
|seal()|obj|被密封的对象|防止其他代码删除对象的属性
|setPrototypeOf()|obj,prototype or null||设置对象的原型（即内部[[Prototype]]属性）。

> 一个属性描述符是一个记录，由下面属性当中的某些组成的 value,writable,get,set,configurable,enumerable

<pre>
  var o, d;

  o = { get foo() { return 17; } };
  d = Object.getOwnPropertyDescriptor(o, "foo");
  // d {
  //   configurable: true,
  //   enumerable: true,
  //   get: /*the getter function*/,
  //   set: undefined
  // }
</pre>

### 原型对象属性

|属性名|说明
|-|-
|length|值为1
|constructor|特定的函数，用于创建一个对象的原型

### 原型对象方法

|方法名|参数|返回值|说明
|-|-|-|-
|hasOwnPropertype|prop|true or false|返回一个布尔值 ，表示某个对象是否含有指定的属性，而且此属性非原型链继承的
|isPrototypeOf|obj|true or false|返回一个布尔值，表示指定的对象是否在本对象的原型链中
|propertyIsEnumberale|prop|true or false|判断指定属性是否可枚举,通过原型链继承的属性除外
|toLocalString|-|表示该对象的字符串|
|toString|-|表示该对象的字符串|返回对象的字符串表示
|valueOf|-|该对象的原始值|返回指定对象的原始值
