## 前端动画实现

前端动画是用户交互的关键部分，使用动画增强交互性，可以提升视觉体验。

### 实现动画的方法

1. 视频 or gif
2. ~~Flash~~
3. 通过 JavaScript 动态改变DOM结点的CSS
4. WebGL
5. Canvas

### 动画渲染技术的趋势

Canvas + WebGL

### 前端动画分类

1.  JavaScript 控制的动画
2.  CSS 控制的动画

#### JS 动画

JS 动画的原理是通过`setTimeout` `setInterval` 或`requestAnimationFrame` 方法绘制动画帧（render），从而动态地改变网页中图形的显示属性 (如 DOM 样式，canvas 位图数据，SVG 对象属性等)，进而达到动画的目的。

多数情况下，应 **首先选用** `requestAnimationFrame`方法（RAF），因为 RAF 的原理是会在浏览器下一次重绘之前更新动画，即它的刷新频率和浏览器自身的刷新频率保持一致 (一般为 60Hz)，从而确保了性能。另外 RAF 在浏览器切入后台时会暂停执行，也可以提升性能。

#### CSS 动画

CSS 动画有以下特点：

优点

*   实现比较简单
*   执行与 JS 主线程无关，例如在 Chromium 里，CSS 动画运行在 `compositor thread` 线程中，即使 JS 线程卡住，CSS 动画照常执行
*   强制使用硬件加速，能有效利用 GPU

缺点

*   只能操作 DOM 或 XML 对象的部分属性
*   动画控制能力薄弱，不能逐帧定义动画状态
*   支持的缓动函数有限 (CSS3 动画的贝塞尔曲线是一个标准 3 次方曲线)
*   滥用硬件加速也会导致性能问题

