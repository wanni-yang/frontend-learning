### css3新增伪类
### 函数
函数名|参数|说明
-|-|-
attr|attribute-name|返回选择元素的属性值
calc|数学表达式|允许计算css的属性值
linear-gradient|direction(渐变角度，left--270deg right--90deg top--0deg bottom--180deg) color-stop1,color-stop2...(渐变起止颜色，停止位置可用百分比)|创建一个线性渐变的图像
radial-gradient|shape(ellipse,circle),size(渐变的大小) position(center top bottom),start-color,...,last-color |径向渐变创建图像
repeating-linear-gradient|direction(渐变角度，left right top bottom 180deg) color-stop1(eg transparent 15px 从15px的位置开始渐变),color-stop2...(渐变起止颜色，停止位置可用百分比)|重复线性渐变创建图像
repeat-radial-gradient||重复径向渐变创建图像
translate|x,y|从当前位置移动元素
polygon|多边形各个点的坐标（x1 y1,x2,y2...）|绘制多边形
cubic-bezier|x1,x2,y1,y2|滑动曲线
step|步数，整数|阶跃函数
### 单位
长度单位|类型|说明
-|-|-
em|相对长度|相对于当前元素的字体大小
ex|相对长度|相对于小写字母x的高度
ch|相对长度|相对于数字0的宽度
rem|相对长度|相对于根元素的字体大小
vw|相对长度|相对于视窗宽度 1vw=视窗宽度的1%
vh|相对长度|相对于视窗高度
vmin|相对长度|vh vw中小的那个
vmax|相对长度|vh vw中大的那个
%|相对长度|

绝对长度：cm mm in pc pt px

### 背景
属性名|值|说明
-|-|-|
background-clip|content-box or padding-box or border-box|规定背景的绘制区域
background-origin|content-box or padding-box or border-box|用来规定background-position相对哪个位置来定位，如果背景图像的 background-attachment 属性为fixed，则该属性没有效果
background-size|length(第一个是width，只有一个值，第二个值为auto) or percentage(相对父元素) or cover or contain|cover把背景图像扩展至足够大，以使背景图像完全覆盖背景区域。背景图像的某些部分也许无法显示在背景定位区域中。contain	把图像图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域。
