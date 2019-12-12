## Chapter7 结构和布局
### 自适应内部元素
min-content 图片同级文字显示根据图片的大小一样
```
  padding: 10px;
  width: min-content;
  border: 1px dotted gray;
  margin: auto;
```
### 根据兄弟元素数量设置样式
`li:first-child:nth-last-child(x)`从最后一个元素开始，x为元素个数，当倒数x个等于第一个元素既可判断元素个数是否符合
### 根据元素范围
`nth-last-child(n+x) ~ li`选中倒数x个元素之前的所有元素，同时选择元素有第一个元素时说明元素数量范围符合，再通过`li:first-child:nth-last-child(n+x)`完成补集元素选中
```
  li:first-child:nth-last-child(n+x),
  li:first-child:nth-last-child(n+x) ~ li {
    background-color: lightcoral;
  }
```
### 定宽居中
常规
```
.wrapper {
  max-width: 900px;
  margin: 1em auto
}
```
通过padding 减少包裹元素的使用
```
  .father {
    max-width: 900px
    padding: 1em calc(50% - 450px);
  }
  .wrapper {

  }
```
### 垂直居中
(1) 绝对定位
可以通过cacl()函数计算
(2) transform
```
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%)
```
(3) 基于视口
```
  main {
    width: 18em;
    padding: 1em 1.5em;
    margin: 50vh auto 0;
    transform: translateY(-50%)
  }
```
  只适用于在视口居中的场景 
(4) 基于Flexbox的解决方案
```
  .wrapper {
    display: flex;
    min-height: 100vn;
    margin: 0
  }
  .content {
    margin: auto
  }
```
### 紧贴底部的页脚
(1) 固定高度  
  通过设置min-height 缺点需要计算  

(2) Flex 
  ```
  body {
    display: flex;
    flex-flow: colum;
    min-height: 100vh;
  }
  main {
    flex: 1;
  }
  ```

