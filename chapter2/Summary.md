## Chapter2 背景与边框
### 半透明边框
边框设置透明度 `border: 10px solid hsla(0,0%,100%,.5)`  
background-clip规定背景的绘制区域` background-clip: padding-box`
### 多重边框
1.设置多个box-shadow模拟多个边框  
```JavaScript
box-shadow: 0 0 0 10px #666,  
            0 0 0 15px deepink,  
            0 2px 5px 15px rgba(0,0,0.6)；
````
缺点无法响应鼠标事件，不会影响布局  
2.outline 两层边框
```
border 10px solid #666;
outline: 5px solid deeppink;
```
### 背景定位
1.background-origin 定位背景图像 `background-position: right 10px bottom 10px`  
2.background-position 通过calc定位 `background-position: calc(100% - 20px) calc(100% - 10px)`
### 边框内圆角
  outline不受border-radius影响，outline与border的间隙用box-shadow填充，阴影宽度为三角函数
  ```
    background-color: tan;
    border-radius: .8em;
    padding: 1em;
    box-shadow: 0 0 0 .6em #644;
    outline: .6em solid #644;
  ```
### 条纹背景
  linear-gradient函数当元素色标相同时过度不平滑，再通过设置background-size重复背景
  ```
  background-image: linear-gradient(#fb3 50%, #58a 0);
  background-size: 100% 30px;
  ```
### 连续的图像边框
  ```
  .ant {
    padding: 1em;
    border: 1px solid transparent;
    background: linear-gradient(white, white) padding-box,
                repeating-linear-gradient(-45deg, black 0, black 25%, white 0, white 50%) 0 / .6em .6em;
    animation: ants 100s linear infinite;
  }
  @keyframes ants {
    to {
      background-position:  100%;
    }
  }
  ```