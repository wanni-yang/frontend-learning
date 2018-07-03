 ### 是什么
 
 >JSON 是一种语法，用来序列化对象、数组、数值、字符串、布尔值和 null 。它基于 JavaScript 语法，但与之不同：JavaScript不是JSON，JSON也不是JavaScript。
 
 >属性名称必须是双引号括起来的字符串；最后一个属性后不能有逗号
 
 - json.parse()
    - 不允许逗号结尾
    - JSON.parse(text[, reviver])
    - reviver函数的遍历顺序依照：从最内层开始，按照层级顺序，依次向外遍历
    - 返回object
 - json.stringfy()
   - JSON.stringify(value[, replacer [, space]])
