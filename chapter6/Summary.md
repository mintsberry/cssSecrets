## Chapter6 用户体验
### 扩大可点击区域
通过伪类元素设置负的margin值扩大点击区域
```
  content: '';
    position: absolute;
    top: -10px;
    bottom: -10px;
    left: -10px;
    right: -10px;
```
### 自定义复选框
通过clip选择原生复选框解决display:none无法Tab无法切换焦点  
+兄弟选择器 根据元素状态变更后通过兄弟选择器来更改后续元素样式
```
    input[type="checkbox"] + label::before {
      content: '\a0';
      display: inline-block;
      vertical-align: .1em;
      width: .8em;
      height: .8em;
      margin-right: .2em;
      border-radius: .2em;
      background: silver;
      text-indent: .15em;
      line-height: .65;
    }
    input[type="checkbox"]:checked + label::before  {
      content: '\2713';
      background: yellowgreen;
    }
    input[type="checkbox"]:disabled + label::before  {
      background: gray;
      box-shadow: none;
      color: #555;
    }
    input[type="checkbox"]:focus + label::before  {
      box-shadow: 0 0 .1em .1em #58a;
    }
    input[type="checkbox"] {
      position: absolute;
      clip: rect(0,0,0,0);
    }
```
思路: 通过checkbox的状态选择选择后续元素样式，checkbox有两种状态因此可以使其他元素也有两种状态样式,如开关按钮
### 阴影弱化背景
(1) 额外元素背景
```
  .overlay {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: rgba(0, 0, 0, .8)
  }
```
缺点： 增加一个额外的HTML元素  

(2) 伪元素
```
  div::before {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index
    background: rgba(0, 0, 0, .8)
  }
```
缺点:无法绑定独立的事件  

(3) box-shadow
```
  box-shadow: 0 0 0 999px rgba(0,0,0,.8)
```
  缺点：无法阻挡遮罩元素事件， 遮罩面积有限
  
(4) backdrop   
  浏览器支持有限不推荐
### 滚动提示
使用background-image生成两条背景，一条遮罩，一条为阴影，设立不同background-attachment值，阴影为scroll，遮罩为local固定，滚动条在顶部时阴影被遮挡，下拉时阴影显示
```
  background: 
  linear-gradient(white, hsla(0, 0%, 100%, 0))
  ,radial-gradient(at top, rgba(0,0,0,.2), transparent 70%) ;
  background-repeat: no-repeat;
  background-size: 100% 50px,100% 15px;
  background-attachment: local, scroll;
```