### 过渡与动画

 <b>animation&@keyframes&transform&transition css rule</b>  
 
  属性名|语法
  -|-
  animation|name duration timing-function delay iteration-count direction fill-mode play-state;
  @keyframes|animationname {keyframes-selector {css-styles;}}
  transform|transfrom-functions
  transition|property(css属性 eg width) duration(持续时间) timing-function(转速曲线) delay(效果开始的时间)
  
  keyframes-selector 必需的。动画持续时间的百分比。合法值：0-100% from(和0%相同) to (和100%相同)
  
  animation-property|值|说明
  -|-|-
  animation-name|keyframename or none|关键帧名称@keyframes定义
  animation-duration|time|多长时间完成秒或者毫秒为单位
  animation-timing-function|三次贝塞尔曲线cubic-bezier(x1,y1,x2,y2)|如何完成一个周期
  animation-delay|time|启动之前的延迟
  animation-iteration-count|n or infinite无限次|播放次数
  animation-direction|normal 正常播放<br>reverse反向播放<br>alternate奇数次正向偶数次反向<br>alternate-reverse奇数次反向偶数次正向<br>initial<br>inherit|是否轮流反向播放
  animation-fill-mode|none 动画播放之前之后都不会应用任何样式到目标元素</br>forwards 动画结束后应用该属性值</br>backwards启动动画的第一次迭代的关键帧中定义的属性值</br>both|不播放时，启动之前或者完成之后的样式
  animation-play-state|pause or running|控制动画状态运行或者暂停
  initial||默认值
  inherit||继承父元素
  
  cubic-bezier((x1,y1,x2,y2)分别代表两个控制锚点的坐标值,我们通过这两个控制锚点来指定想要的贝塞尔曲线. 语法形式是这样的:cubic-bezier(x1, y1, x2, y2),其中 (x1, y1) 表示第一个控制锚点的坐标,而 (x2, y2) 是第二个。曲线片断的两个端点分别固定在(0,0) 和 (1,1),前者是整个过渡的起点（时间进度为零,动画进度为零）,后者是终点（时间进度为 100%,动画进度为 100%）。
  backwards:当 animation-direction 为 "normal" 或 "alternate" 时是 from 关键帧中的值,当 animation-direction 为 "reverse" 或 "alternate-reverse" 时是to关键帧中的值
  
  transform-function|说明
  -|-
  none|	定义不进行转换。
  matrix(n,n,n,n,n,n) |	定义 2D 转换，使用六个值的矩阵。
  matrix3d(n,n,n,n,n,n,n,n,n,n,n,n,n,n,n,n)|定义 3D 转换，使用 16 个值的 4x4 矩阵。
  translate(x,y)|定义 2D 转换。
  translate3d(x,y,z)|	定义 3D 转换。
  translateX(x)|	定义转换，只是用 X 轴的值。
  translateY(y)|	定义转换，只是用 Y 轴的值。
  translateZ(z)	|定义 3D 转换，只是用 Z 轴的值。
  scale(x[,y]?)	|定义 2D 缩放转换。
  scale3d(x,y,z)|	定义 3D 缩放转换。
  scaleX(x)|	通过设置 X 轴的值来定义缩放转换。
  scaleY(y)|	通过设置 Y 轴的值来定义缩放转换。
  scaleZ(z)|	通过设置 Z 轴的值来定义 3D 缩放转换。
  rotate(angle)|	定义 2D 旋转，在参数中规定角度。
  rotate3d(x,y,z,angle)|	定义 3D 旋转。
  rotateX(angle)|	定义沿着 X 轴的 3D 旋转。
  rotateY(angle)|	定义沿着 Y 轴的 3D 旋转。
  rotateZ(angle)|	定义沿着 Z 轴的 3D 旋转。
  skew(x-angle,y-angle)	|定义沿着 X 和 Y 轴的 2D 倾斜转换。
  skewX(angle)|	定义沿着 X 轴的 2D 倾斜转换。
  skewY(angle)|	定义沿着 Y 轴的 2D 倾斜转换。
  perspective(n)|	为 3D 转换元素定义透视视图。
  
  transition-property|说明
  -|-
  transition-property|none or all（全部属性） or property
  transition-duration|time以秒或者毫秒为单位
  transition-timing-function|linear（相同速度cubic-bezier(0,0,1,1)） </br>ease（开始慢-变快-结束慢cubic-bezier(0.25,0.1,0.25,1)）</br> ease-in（慢开始cubic-bezier(0.42,0,1,1)）</br> ease-out（慢结束cubic-bezier(0,0,0.58,1)） </br>ease-in-out（开始慢-结束慢cubic-bezier(0.42,0,0.58,1)）</br> cubic-bezier(n,n,n,n)n取[0,1]
  transition-delay|time
  
#### 1. 缓动效果
  - 位移变化 模拟小球下落回弹的过程
  - 尺寸变化 鼠标悬停变大、弹框缓慢弹出、图形元素动态变化
  - 角度变化 饼图扇区从0度开始展开到实际大小
#### 2. 逐帧动画
#### 3. 闪烁效果
#### 4. 打字动画
#### 5. 状态平滑的动画
#### 6. 沿环形路径平移的动画
