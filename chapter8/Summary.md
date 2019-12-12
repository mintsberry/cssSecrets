## Chapter7 过渡与动画
### 状态平滑动画
 通过改变animation-play-state的值实现动画暂停
 ```
.box {
  display: inline-block;
  width: 150px;
  height: 150px;
  background: url('');
  background-size: auto 100%;
  animation: panormaic 10s linear infinite alternate paused;
}
.box:hover {
  animation-play-state: running;
}
```
### transfrom-origin
通过transform可以模拟出transform-origin效果
```
  transform: rotate(30deg);
  transform-origin: 200px 300px;
  /* 相同效果 */
  transform: translate(200px, 300px)
            rotate(30deg)
            translate-(200px, -300px)
```