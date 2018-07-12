### 是什么
> HTML 拖放接口使应用程序能够在Firefox和其他浏览器中使用拖放功能。例如，通过这些功能，用户可以使用鼠标选择可拖动元素，将元素拖动到可放置元素，
并通过释放鼠标按钮来放置这些元素。可拖动元素的一个半透明表示在拖动操作期间跟随鼠标指针。

### 发生过程
> 一个典型的drag操作是这样开始的：用户用鼠标选中一个可拖动的（draggable）元素，移动鼠标到一个可放置的（droppable）元素，然后释放鼠标。 在操作期间，
会触发一些事件类型，有一些事件类型可能会被多次触发（比如drag 和 dragover 事件类型）

##### 涉及到的事件和事件 handler

|Event|	On Event Handler|	Description
|-|-|-
|drag|	ondrag	|当拖动元素或选中的文本时触发。
|dragend	|ondragend	|当拖拽操作结束时触发 (比如松开鼠标按键或敲“Esc”键). 
|dragenter|	ondragenter|	当拖动元素或选中的文本到一个可释放目标时触发。
|dragexit	|ondragexit|	当元素变得不再是拖动操作的选中目标时触发。
|dragleave|	ondragleave	|当拖动元素或选中的文本离开一个可释放目标时触发。
|dragover	|ondragover	|当元素或选中的文本被拖到一个可释放目标上时触发（每100毫秒触发一次）。
|dragstart|	ondragstart|	当用户开始拖动一个元素或选中的文本时触发。
|drop	|ondrop	|当元素或选中的文本在可释放目标上被释放时触发。

### 接口

|接口名称|属性|说明
|-|-|-
|DragEvent|DragEvent构造函数，dataTransfer|dataTransfer属性是一个DataTransfer对象。 DataTransfer 对象包含了拖拽事件的状态
|DataTransfer||
|DataTransferItem||
|DataTransferItemList||
