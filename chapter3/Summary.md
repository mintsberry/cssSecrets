## Chapter3 背景与边框
### 半椭圆
```
  border-radius:  50% /100% 100% 0 0;
                  background-color: aqua;
                  width: 80px;
                  height: 80px;
```
### 平行四边形
1.嵌套元素    
  通过元素添加css动画skew(),再对内容元素添加反向skew()变形抵消容器变形影响
  ```
  .wrapper {
    transform: skewX(-45deg);
  }
  .wrapper > div {
    transfrom: skewX(45deg);
  }
  ```
  思路:transform会影响子元素，任何子元素都可以设置反向的变形效果抵消继承的影响  
2.伪元素变形
  ```
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background-color: #58a;
  transform: skew(-45deg);
  z-index: -1;
  ```
  思路:当需要对一个元素产生形变图形或其他效果时候，但不想改变元素本身可以通过伪类实现

### 菱形图片
对图片包裹元素进行旋转，同时子元素反向旋转抵消旋转效果放大图片实现
```
  .pic{
    width: 400px;
    height: 400px;
    transform: rotate(45deg);
    overflow: hidden;
    margin: 50px auto;
  }
  .pic > img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transform: rotate(-45deg) scale(1.42);
  }
```
也可以通过裁剪路径实现该效果
### 切角效果
```
  background: #58a;
  background: linear-gradient(-45deg, #abc 50%, #999 0);
  color: white;
```
### 梯形标签页
  ```
  div {
    position: relative;
    display: inline-block;
    padding: .5em 1em .35em;
    color: white;
  }
  div::before {
    content: "";
    z-index: -1;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    background: #abc;
    transform: perspective(.5em) rotateX(5deg) scaleY(1.3);
    transform-origin: right;
  }
  ```
### 饼图
  通过渐变实现平分饼图`background-image: linear-gradient(to right, transparent 50%, #655 0);` 
  通过伪元素和半圆对饼图进行遮罩成为完整饼图
  ```
  content: '';
  display: block;
  margin-left: 50%;
  height: 100%;
  background-color: inherit;
  border-radius: 0 100% 100% 0 / 50%; 半圆
  ```
  通过延迟动画完成超过50%后样式错误
  ```
  animation: spin 3s linear infinite,
             bg 6s step-end infinite;
  ```
  通过指定负数延时来完成静态不同比率饼图
  ```
  .pie {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    background: yellowgreen;
    background-image: linear-gradient(to right, transparent 50%, #655 0);
  }
  .pie::before {
    content: '';
    display: block;
    margin-left: 50%;
    height: 100%;
    background-color: inherit;
    border-radius: 0 100% 100% 0 / 50%;
    transform-origin: left ;
    animation: spin 50s linear infinite,
                bg 100s step-end infinite;
    animation-delay: inherit;
    animation-play-state: paused;
  }
  @keyframes spin {
    to {transform: rotate(.5turn);}
  }
  @keyframes bg {
    50% {background: #655;}
  }
  ```