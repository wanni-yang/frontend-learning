### 过渡与动画
1. 缓动效果
  - 位移变化 模拟小球下落回弹的过程
  - 尺寸变化 鼠标悬停变大、弹框缓慢弹出、图形元素动态变化
  - 角度变化 饼图扇区从0度开始展开到实际大小
  
  <b>animation&@keyframes css rule</b>  
  
  属性名|语法
  -|-
  animation|name duration timing-function delay iteration-count direction fill-mode play-state;
  @keyframes|animationname {keyframes-selector {css-styles;}}
  transform|transfrom-functions
  
  keyframes-selector 必需的。动画持续时间的百分比。合法值：0-100% from(和0%相同) to (和100%相同)
  
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
  
2. 逐帧动画
3. 闪烁效果
4. 打字动画
5. 状态平滑的动画
6. 沿环形路径平移的动画
