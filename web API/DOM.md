 ### Element
  - 特征属性
  <pre>
      Element.attributes  //返回当前元素节点的所有属性节点
      Element.id  //返回指定元素的id属性，可读写
      Element.tagName  //返回指定元素的大写标签名
      Element.innerHTML   //返回该元素包含的HTML代码，可读写
      Element.outerHTML  //返回指定元素节点的所有HTML代码，包括它自身和包含的的所有子元素，可读写
      Element.className  //返回当前元素的class属性，可读写
      Element.classList  //返回当前元素节点的所有class集合
      Element.dataset   //返回元素节点中所有的data-*属性。
  </pre>
  - 尺寸属性
  <pre>
    Element.clientHeight   //返回元素节点可见部分的高度
    Element.clientWidth   //返回元素节点可见部分的宽度
    Element.clientLeft   //返回元素节点左边框的宽度
    Element.clientTop   //返回元素节点顶部边框的宽度
    Element.scrollHeight  //返回元素节点的总高度
    Element.scrollWidth  //返回元素节点的总宽度
    Element.scrollLeft   //返回元素节点的水平滚动条向右滚动的像素数值,通过设置这个属性可以改变元素的滚动位置
    Element.scrollTop   //返回元素节点的垂直滚动向下滚动的像素数值
    Element.offsetHeight   //返回元素的垂直高度(包含border,padding)
    Element.offsetWidth    //返回元素的水平宽度(包含border,padding)
    Element.offsetLeft    //返回当前元素左上角相对于Element.offsetParent节点的垂直偏移
    Element.offsetTop   //返回水平位移
    Element.style  //返回元素节点的行内样式
  </pre>
  - 其他
  <pre>
    Element.children   //包括当前元素节点的所有子元素
    Element.childElementCount   //返回当前元素节点包含的子HTML元素节点的个数
    Element.firstElementChild  //返回当前节点的第一个Element子节点  
    Element.lastElementChild   //返回当前节点的最后一个Element子节点  
    Element.nextElementSibling  //返回当前元素节点的下一个兄弟HTML元素节点
    Element.previousElementSibling  //返回当前元素节点的前一个兄弟HTML节点
    Element.offsetParent   //返回当前元素节点的最靠近的、并且CSS的position属性不等于static的父元素。
  </pre>
  #### Element 方法
   - 位置
   <pre>
    getBoundingClientRect()  
    // getBoundingClientRect返回一个对象，包含top,left,right,bottom,width,height // width、height 元素自身宽高
    // top 元素上外边界距窗口最上面的距离
    // right 元素右外边界距窗口最上面的距离
    // bottom 元素下外边界距窗口最上面的距离
    // left 元素左外边界距窗口最上面的距离
    // width 元素自身宽(包含border,padding) 
    // height 元素自身高(包含border,padding) 

    getClientRects()   //返回当前元素在页面上形参的所有矩形。

    // 元素在页面上的偏移量  
    var rect = el.getBoundingClientRect()  
    return {   
      top: rect.top + document.body.scrollTop,   
      left: rect.left + document.body.scrollLeft  
    }
   </pre>
   - 属性相关
   <pre>
    Element.getAttribute()：读取指定属性  
    Element.setAttribute()：设置指定属性  
    Element.hasAttribute()：返回一个布尔值，表示当前元素节点是否有指定的属性  
    Element.removeAttribute()：移除指定属性
   </pre>
   - 查找
   <pre>
    Element.querySelector()  
    Element.querySelectorAll()  
    Element.getElementsByTagName()  
    Element.getElementsByClassName()
   </pre>
   - 事件
   <pre>
    Element.addEventListener()：添加事件的回调函数  
    Element.removeEventListener()：移除事件监听函数  
    Element.dispatchEvent()：触发事件

    //ie8
    Element.attachEvent(oneventName,listener)
    Element.detachEvent(oneventName,listener)

    // event对象  
    var event = window.event||event;    

    // 事件的目标节点  
    var target = event.target || event.srcElement;

    // 事件代理  
    ul.addEventListener('click', function(event) {   
      if (event.target.tagName.toLowerCase() === 'li') {   
        console.log(event.target.innerHTML)   
      }  
    });
   </pre>