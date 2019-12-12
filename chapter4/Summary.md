## Chapter4 视觉效果
### 单侧投影
box-shadow指定模糊半径，通过扩张半径去缩小投影尺寸，再用偏移量指定投影效果偏移实现单侧投影
```
box-shadow: 0 5px 4px -4px #333; 
```
### 临边投影
```
 box-shadow: 6px 6px 4px -2px #333;
```
### 双侧投影
指定多个投影值实现多重投影
```
box-shadow: 5px 0 4px -2px #333,
            -5px 0 4px -2px #333;
```
### 不规则投影
filter:drop-shadow() 能够给任何不透明元素添加投影效果
### 毛玻璃
```
  main::before {
      content: '';
      z-index: -1;
      margin: -20px;
      position: absolute;
      top: 0;
      right: 0;
      left: 0;
      bottom: 0;
      filter: blur(20px);
      background: hsla(0, 0%, 100%, .3);
      /* background: rgba(255, 0, 0, .5); */
  }
```