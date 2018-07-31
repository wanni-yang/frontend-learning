> 块格式上下文是页面CSS视觉渲染的一部分，用于决定块盒子的布局及浮动相互影响范围的一个区域。一个BFC包含创建该上下文元素的所有子元素，但不包括创建了新BFC的子元素的内部元素，即一个元素不能同时存在两个BFC中。

> 视觉格式化模型(visual formatting model)是用来处理文档并将它显示在视觉媒体上的机制，它也是CSS中的一个概念。视觉格式化模型定义了盒（Box）的生成，盒主要包括了块盒、行内盒、匿名盒（没有名字不能被选择器选中的盒）以及一些实验性的盒（未来可能添加到规范中）。盒的类型由display属性决定。
 - block box
  `display:block`,参与BFC,垂直排列,block-level,
 - inline box
   - `display :inline-block;inline-block;inline-table`，水平排列
   - inline-level-boxes参与行内格式化上下文(inline formatting context)。同时参与生成行内格式化上下文的行内级盒称为行内盒(inline boxes)。所有display:inline的非替换元素生成的盒是行内盒
   - 不参与生成行内格式化上下文的行内级盒称为原子行内级盒(atomic inline-level boxes)。这些盒由可替换行内元素，或 display 值为 inline-block 或 inline-table 的元素生成，不能拆分成多个盒
 - anonymous box
  匿名盒也有份匿名块盒与匿名行内盒，因为匿名盒没有名字，不能利用选择器来选择它们，所以它们的所有属性都为inherit或初始默认值
 #### 定位
 
   <b>box是定位的基本单位</b>
   - 常规流
   - 静态定位，常规流的box位置
   - 相对定位，box位置偏离原来的位置但是原位置仍保留
 - 浮动
   - 位于当前行的开头或者末尾
   - 影响常规流布局，导致常规流环绕在它的周围，除非clear
 - 绝对定位
   - box从常规流中移除，不影响常规流布局
   - `position:absolute;fixed`
   - `absolute`相对于最近的一个属性`absolute/relative/fixed`的父元素，不存在的话就是body
 #### 创建BFC
   - 根元素或者包含它的元素
   - `float 不为 none`的元素
   - `position:absolute/fixed`
   - 非块级box容器`display:table-cell，table-caption，inline-block, flex, inline-flex`
   - 表格单元格
   - `overflow不是visible`
   - flex boxes `display:flex;inline-flex`
 ###### BFC特性
 - 同一个BFC中的元素相互影响可能发生margin collapse
  <pre>可以通过创建新的BFC来解决margin叠加</pre>
  [margin collapse](http://jsrun.net/YqgKp/edit)
 - 同一个BFC中每个盒子的margin-left的左边与容器块border-left的左边相接触（从左到右）浮动存在也如此
 - BFC区域不会和float box叠加
  <pre>和float box同级创建一个BFC就可以进行两栏布局
  </pre>
  [布局](http://jsrun.net/kqgKp/edit)
 - BFC在页面上是独立的容器，处于BFC内部的元素与外部的元素相互隔离，
 使内外元素的定位不会相互影响
 - 计算BFC高度时，考虑其包含的全部元素包括浮动元素
 <pre>float box的父容器创建BFC避免塌陷</pre>
 [float box 父容器高度](http://jsrun.net/pqgKp/edit)
