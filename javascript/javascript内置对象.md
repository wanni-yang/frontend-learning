### 全局属性

- Infinity

> 全局变量的属性，全局变量

- NaN

> 全局对象的属性，判断一个值是不是NaN用Number.isNaN() or isNaN()函数。

- undefined

> undefined是全局对象的一个属性,是全局作用域的一个变量.一个没有被赋值的变量的类型是undefined;如果方法或者是语句中操作的变量没有被赋值，则会返回undefined;一个函数如果没有使用return语句指定返回值，就会返回一个undefined值。

- null

> 值null是一个字面量，是表示缺少的标示，表示变量没有指向任何对象，也可以理解为尚未创建的对象。当返回类型是对象，但是没有关联值得时候用到null

### 全局函数属性

> 全局函数可以直接调用

- eval()
- isFinite()
- isNaN()
- parseFloat()
- parseInt()
- decodeURI()
- encodeURI()

### 基本对象

> 定义或者使用其他对象的基础

|对象名|说明
|-|-
|Object|Object构造函数为给定值创建一个对象包装器
|Function|创建一个新的Function对象[detail](https://github.com/wanni-yang/frontend-learning/blob/master/javascript/%E5%87%BD%E6%95%B0/%E5%86%85%E7%BD%AE%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95.md)
|Boolean|是一个布尔值的对象包装器,参数值为 0、-0、null、false、NaN、undefined、 document.all或者空字符串（""），则生成的 Boolean 对象的值为 false。当 Boolean 对象用于条件语句的时候（译注：意为直接应用于条件语句），任何不是 undefined 和 null 的对象，包括值为 false 的 Boolean 对象，都会被当做 true 来对待。
|Symbol|是一种基本数据类型
|Error|
|Number|Number 对象由 Number() 构造器创建
|Date|
|Math|具有数学常数和函数的属性和方法。不是一个函数对象。
|String|String 全局对象是一个用于字符串或一个字符序列的构造函数[detail](https://github.com/wanni-yang/frontend-learning/blob/master/javascript/String.md)
|RegExp|RegExp 构造函数创建了一个正则表达式对象，用于将文本与一个模式匹配

### 可索引的集合对象 

> 对象表示按照索引值来排序的数据集合，包括数组和类型数组，以及类数组结构的对象

|对象名|说明
|-|-
|Array|用于构造数组的全局对象[detail](https://github.com/wanni-yang/frontend-learning/blob/master/javascript/%E6%95%B0%E7%BB%84/%E5%86%85%E7%BD%AE%E5%B1%9E%E6%80%A7%E5%92%8C%E6%96%B9%E6%B3%95.md)

### 使用键的集合对象

|对象名|说明
|-|-
|Map|Map 对象保存键值对。任何值(对象或者原始值) 都可以作为一个键或一个值。[detali](https://github.com/wanni-yang/frontend-learning/blob/master/javascript/Map.md)
|Set|允许存储任何类型的唯一值，无论是原始值或者是对象引用
|WeekMap|WeakMap 的 key 只能是 Object 类型。 原始数据类型 是不能作为 key 的
|WeekSet|WeakSet 对象是一些对象值的集合, 并且其中的每个对象值都只能出现一次.

### 结构化数据

> 这些对象用来表示和操作结构化的缓冲区数据，或使用 JSON （JavaScript Object Notation）编码的数据。

|对象名|说明
|-|-
|JSON|

### 控制抽象对象

|对象名|说明
|-|-
|Promise|用于表示一个异步操作的最终状态（完成或失败），以及其返回的值。
|Generator|生成器对象是由一个 generator function 返回的,并且它符合可迭代协议和迭代器协议。
|GeneratorFunction|GeneratorFunction构造器生成新的生成器函数 对象。在JavaScript中，生成器函数实际上都是GeneratorFunction的实例对象。

### 反射

|对象名|说明
|-|-
|Reflex|Reflect 是一个内置的对象，它提供拦截 JavaScript 操作的方法。这些方法与处理器对象的方法相同。Reflect不是一个函数对象，因此它是不可构造的。能将其与一个new运算符一起使用
|Proxy|Proxy 对象用于定义基本操作的自定义行为（如属性查找，赋值，枚举，函数调用等）。

### 其他

|对象名|说明
|-|-
|arguments|[detail](https://github.com/wanni-yang/frontend-learning/blob/master/javascript/%E5%87%BD%E6%95%B0/arguments%E5%AF%B9%E8%B1%A1.md)


