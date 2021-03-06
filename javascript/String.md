### String
- String 构造函数
 
 |属性名|说明|
 |-|-|
 |prototype|可以为 String 对象增加新的属性。|
 
 |方法|说明|
 |-|-|
 |fromCharCode| 通过一串 Unicode 创建字符串。|
 
- String原型 String.prototype,所有实例都会继承原型的属性和方法
 
 |属性名|说明|
 |-|-|
 |constructor|用于创造对象的原型对象的特定的函数|
 |length|返回字符串长度|
 
 |方法|参数|返回值|说明
 |-|-|-|-
 |charAt|index|字符|返回特定位置的字符
 |charCodeAt|index|UTF-16 代码单元值0到65535之间的整数 or NaN|返回给定索引的字符的unicode的值
 |concat|string2...stringN|新字符串|连接两个字符串文本，不影响原字符串
 |includes|searchString,position|true or false|判断是否包含其他字符串,区分大小写
 |startsWith|searchString, postion|true or false|判断字符串开头是否包含其他字符串的字符
 |endsWith|searchString, postion|true or false|判断字符串结尾是否包含其他字符串的字符
 |indexOf|searchValue ,fromIndex|第一次出现的索引值 or -1|查找首个被发现的给定值
 |lastIndexOf|searchValue ,fromIndex|最后一次出现的索引值 or -1|查找最后一个被发现的给定值
 |match|regexp||使用正则表达式与字符串比较
 |replace|regexp or substr,newSubStr or funtion [详细](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace) |新字符串|在正则表达式和字符串直接比较，然后用新的子串来替换被匹配的子串
 |search|regexp|第一个出现的匹配性的下标 or -1|对正则表达式和指定字符串进行匹配搜索
 |repeat|count|包含指定字符串的指定数量副本的新字符串|返回指定重复次数的由元素组成的字符串对象
 |slice|beginSlice,endSlice|新字符串|截取字符串区域,不会改变原字符串
 |split|separator，limit|数组|分割字符串为数组
 |*substr*|indexStart,length|从指定位置开始到指定字符数的字符 or 空字符|指定位置开始的字符
 |substring|[indexStart, indexEnd)|新字符串|指定两个下标之间的字符
 |toLocalLowerCase|-|小写字符串|转换小写
 |toLowerCase|-|小写字符串|转换小写
 |toLocalUpperCase|-|大写字符串|转换大写
 |toUpperCase|-|大写字符串|转换大写
 |toString|-|指定对象的字符串形式|String 对象覆盖了Object 对象的 toString 方法；并没有继承 Object.toString()。对于 String 对象，toString 方法返回该对象的字符串形式
 |trim|-|新字符串|去除首尾空格
 |valueOf|-|一个String对象的原始值等同于String.prototype.toString()|该方法通常在 JavaScript 内部被调用，而不是在代码里显示调用

### 原型方法之间

- substring([indexStart,indexEnd))

  substring 要截取的是从 indexA 到 indexB（不包含）之间的字符，符合以下规律：
  若 indexA == indexB，则返回一个空字符串；
  若 省略 indexB，则提取字符一直到字符串末尾；
  若 任一参数小于 0 或 NaN，则被当作 0；
  若 任一参数大于 length，则被当作 length。
  而 如果 indexA > indexB，则 substring 的执行效果就像是两个参数调换一般。
  
  > substr 和 substring，都是两个参数，作用基本相同，两者第一个参数含义相同，但用法不同，前者可为负数，后者值为负数或者非整数时将隐式转换为0。前者第二个参数表示截取字符串的长度，后者第二个参数表示截取字符串的下标；同时substring第一个参数大于第二个参数时，执行结果同位置调换后的结果
  
  

  

