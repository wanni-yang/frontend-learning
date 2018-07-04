### 是什么
  
>一个Map对象以插入顺序迭代其元素 — 一个  for...of 循环为每次迭代返回一个[key，value]数组。Map 对象保存键值对。任何值(对象或者原始值) 都可以作为一个键或一个值

> 键的相等，=== 除了NaN，虽然NaN！= NaN 但是在map中是相同de

### Object && Map

|Object|Map
|-|-
|key--只能是字符串或者symbols|key可以是任意值，函数 对象 基本类型
|键值对个数--手动计算|通过size属性直接获取
|迭代--先获取key数组再迭代|可迭代
|频繁增删键值对--性能弱|性能优势

### 属性
|属性名|说明
|-|-
|length|值为0
|prototype|表示 Map 构造器的原型。 允许添加属性从而应用于所有的 Map 对象。

###原型属性

|属性名|说明
|Map.prototype.constructor|返回一个函数，它创建了实例的原型。默认是Map函数
|Map.prototype.size|返回Map对象的键/值对的数量。

### 原型方法

|方法名|参数|返回值|说明
|-|-|-|-
|clear()|||移除所有键值对
|delete()|key|移除关联key的值|移除和key关联的的值
|entries()||返回一个新的 Iterator 对象|它按插入顺序包含了Map对象中每个元素的 [key, value] 数组。
|forEach()|callbackfn,thisArg||按插入顺序为Map对象的键值对调用回调函数，thisArg作为回调里的this值
|get()|key|返回key关联的值 or undefined|
|has()|key|true or false|判断是否包含key对应的值
|keys()||返回一个新的 Iterator对象|按插入顺序包含了Map对象中每个元素的键
|set()|key,value|Map对象|设置Map对象中键的值
|values()||返回一个新的Iterator对象|按插入顺序包含了Map对象中每个元素的值
