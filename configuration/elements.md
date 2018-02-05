# 通用元素配置

虽然图表类型提供了设置来配置每个数据集的样式，但我们有时希望以相同的方式对所有数据集进行样式设置。常用的做法是用相同的颜色对 条形图中的所有线条进行描边来改变每个数据集的填充。

我们可以为四种不同类型的元素配置选项：**[arc](#arc-configuration)**, **[lines](#line-configuration)**, **[points](#point-configuration)**, 和 **[rectangles](#rectangle-configuration)**。当设置后，这些选项将应用于该类型的所有对象，除非被附加到数据集的配置被覆盖掉。

## 全局配置

元素选项可以在每个图表或全局中指定。元素的全局选项在`Chart.defaults.global.elements`中定义。例如，要设置全局条形图的边框宽度，可以执行以下操作：

```javascript
Chart.defaults.global.elements.rectangle.borderWidth = 2;
```

## 点指示器配置

点元素用于表示折线图或气泡图中的点。

全局点指示器配置选项: `Chart.defaults.global.elements.point`

| 名称               | 类型     | 默认值              | 描述                   |
| ------------------ | -------- | ------------------- | ---------------------- |
| `radius`           | `Number` | `3`                 | 半径                   |
| `tyle`             | `String` | `circle`            | 样式                   |
| `backgroundColor`  | `Color`  | `'rgba(0,0,0,0.1)'` | 填充色                 |
| `borderWidth`      | `Number` | `1`                 | 边框宽度               |
| `borderColor`      | `Color`  | `'rgba(0,0,0,0.1)'` | 边框颜色               |
| `hitRadius`        | `Number` | `1`                 | 点击时额外增加的点半径 |
| `hoverRadius`      | `Number` | `4`                 | 悬浮时的点半径         |
| `hoverBorderWidth` | `Number` | `1`                 | 悬浮时的边框宽度       |

## 折线配置

线元素用于表示折线图中的线。

全局折线配置: `Chart.defaults.global.elements.line`

| 名称               | 类型             | 默认值              | 描述                                                                                                           |
| ------------------ | ---------------- | ------------------- | -------------------------------------------------------------------------------------------------------------- |
| `tension`          | `Number`         | `0.4`               | 贝塞尔曲线张力 (`0` 表示没有)                                                                                  |
| `backgroundColor`  | `Color`          | `'rgba(0,0,0,0.1)'` | 填充色                                                                                                         |
| `borderWidth`      | `Number`         | `3`                 | 画笔宽度                                                                                                       |
| `borderColor`      | `Color`          | `'rgba(0,0,0,0.1)'` | 画笔颜色                                                                                                       |
| `borderCapStyle`   | `String`         | `'butt'`            | 线帽样式 (详看 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineCap)).      |
| `borderDash`       | `Array`          | `[]`                | 线段 (详看 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/setLineDash)).      |
| `borderDashOffset` | `Number`         | `0`                 | 偏移量 (详看 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineDashOffset)). |
| `borderJoinStyle`  | `String`         | `'miter'`           | 连接样式 (详看 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineJoin)).     |
| `capBezierPoints`  | `Boolean`        | `true`              | `true` 表示在图表内受贝塞尔曲线控制，`false`为没限制                                                           |
| `fill`             | `Boolean/String` | `true`              | 填充位置: `'zero'`, `'top'`, `'bottom'`, `true` (等于`'zero'`) 或者 `false` (不填充).                          |
| `stepped`          | `Boolean`        | `false`             | `true` 将线显示为阶梯线(`tension`设置将会被忽略).                                                              |

## 条形配置

矩形元素用于表示条形图中的条形。

全局矩形设置: `Chart.defaults.global.elements.rectangle`

| 名称              | 类型     | 默认值              | 描述                                                            |
| ----------------- | -------- | ------------------- | --------------------------------------------------------------- |
| `backgroundColor` | `Color`  | `'rgba(0,0,0,0.1)'` | 填充色                                                          |
| `borderWidth`     | `Number` | `0`                 | 边框宽度                                                        |
| `borderColor`     | `Color`  | `'rgba(0,0,0,0.1)'` | 边框色.                                                         |
| `borderSkipped`   | `String` | `'bottom'`          | 跳过 (排除) 的边框: `'bottom'`, `'left'`, `'top'` or `'right'`. |

## 弧配置

圆弧用于极地图，甜甜圈图和饼图。

全局圆弧配置: `Chart.defaults.global.elements.arc`.

| 名称              | 类型     | 默认值              | 描述     |
| ----------------- | -------- | ------------------- | -------- |
| `backgroundColor` | `Color`  | `'rgba(0,0,0,0.1)'` | 填充色   |
| `borderColor`     | `Color`  | `'#fff'`            | 描边框色 |
| `borderWidth`     | `Number` | `2`                 | 描边宽度 |
