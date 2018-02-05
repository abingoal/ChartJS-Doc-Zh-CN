# 雷达图(Radar)

雷达图是显示多个数据点和它们之间的差异的一种方式。

通常用于比较两个或更多不同数据集的点。

{% chartjs %}
{
"type": "radar",
"data": {
"labels": [
"Eating",
"Drinking",
"Sleeping",
"Designing",
"Coding",
"Cycling",
"Running"
],
"datasets": [{
"label": "My First Dataset",
"data": [65, 59, 90, 81, 56, 55, 40],
"fill": true,
"backgroundColor": "rgba(255, 99, 132, 0.2)",
"borderColor": "rgb(255, 99, 132)",
"pointBackgroundColor": "rgb(255, 99, 132)",
"pointBorderColor": "#fff",
"pointHoverBackgroundColor": "#fff",
"pointHoverBorderColor": "rgb(255, 99, 132)",
"fill": true
}, {
"label": "My Second Dataset",
"data": [28, 48, 40, 19, 96, 27, 100],
"fill": true,
"backgroundColor": "rgba(54, 162, 235, 0.2)",
"borderColor": "rgb(54, 162, 235)",
"pointBackgroundColor": "rgb(54, 162, 235)",
"pointBorderColor": "#fff",
"pointHoverBackgroundColor": "#fff",
"pointHoverBorderColor": "rgb(54, 162, 235)",
"fill": true
}]
},
"options": {
"elements": {
"line": {
"tension": 0,
"borderWidth": 3
}
}
}
}
{% endchartjs %}

## 示例用法

```javascript
var myRadarChart = new Chart(ctx, {
	type: "radar",
	data: data,
	options: options
});
```

## 数据集属性

雷达图允许为每个数据集指定一些属性显示特定数据集。

所有 point \*属性都可以被指定为一个数组。如果这些设置为数组值，则第一个值应用于第一个点，第二个值应用于第二个点，依此类推。

| 名称                        | 类型                            | 描述                                                                                                                 |
| --------------------------- | ------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| `label`                     | `String`                        | 图例和工具提示中的数据集的标签名                                                                                     |
| `backgroundColor`           | `Color/Color[]`                 | 填充色 参考 [颜色(Colors)](../general/colors.md#colors)                                                              |
| `borderColor`               | `Color/Color[]`                 | 线的颜色 参考[颜色(Colors)](../general/colors.md#colors)                                                             |
| `borderWidth`               | `Number/Number[]`               | 线宽度(以像素为单位)                                                                                                 |
| `borderDash`                | `Number[]`                      | 破折号的长度和间距 参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/setLineDash) |
| `borderDashOffset`          | `Number`                        | 偏移量 参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineDashOffset)          |
| `borderCapStyle`            | `String`                        | 线冒样式 参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineCap)               |
| `borderJoinStyle`           | `String`                        | Line joint 样式 参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineJoin)       |
| `fill`                      | `Boolean/String`                | 区域填充色 [更多...](#fill)                                                                                          |
| `lineTension`               | `Number`                        | 贝塞尔曲线张力。0 为直线。                                                                                           |
| `pointBackgroundColor`      | `Color/Color[]`                 | 数据点填充色                                                                                                         |
| `pointBorderColor`          | `Color/Color[]`                 | 数据点边框色                                                                                                         |
| `pointBorderWidth`          | `Number/Number[]`               | 数据点边框宽度(以像素为单位)                                                                                         |
| `pointRadius`               | `Number/Number[]`               | 数据点半径。0 为不显示点                                                                                             |
| `pointStyle`                | `String/String[]/Image/Image[]` | 数据点样式 [更多...](#pointStyle)                                                                                    |
| `pointHitRadius`            | `Number/Number[]`               | 对鼠标事件作出响应的非显示点的像素大小。                                                                             |
| `pointHoverBackgroundColor` | `Color/Color[]`                 | 鼠标悬浮时，数据点背景颜色                                                                                           |
| `pointHoverBorderColor`     | `Color/Color[]`                 | 鼠标悬浮时，数据点边框色                                                                                             |
| `pointHoverBorderWidth`     | `Number/Number[]`               | 鼠标悬浮时数据点的边框宽度                                                                                           |
| `pointHoverRadius`          | `Number/Number[]`               | 鼠标悬停时，数据点的半径大小                                                                                         |

### pointStyle

数据点风格选项：

* 'circle'
* 'cross'
* 'crossRot'
* 'dash'.
* 'line'
* 'rect'
* 'rectRounded'
* 'rectRot'
* 'star'
* 'triangle'

如果是使用图片，则使用[drawImage](https://developer.mozilla.org/en/docs/Web/API/CanvasRenderingContext2D/drawImage)在 canvas 上绘制该图像。

## 配置选项

与其他图表不同，雷达图表没有图表特定选项。

## 比例选项

雷达图只支持一个比例尺。该比例的选项在`scale`属性中定义。

```javascript
options = {
	scale: {
		// Hides the scale
		display: false
	}
};
```

## 默认选项

通常要将配置设置应用于所有创建的雷达图表。全局雷达图表设置在`Chart.defaults.radar`中。更改全局选项只会影响更改后创建的图表。现有图表不会更改。

## 数据结构

雷达图表数据集的`data`属性被指定为一个数字数组。数据数组中的每个点对应于 x 轴上相同索引处的标签。

```javascript
data: [20, 10];
```

对于雷达图表，为了表达每个点的含义，我们在图表中的每个点周围都包含一个字符串数组。

```javascript
data: {
    labels: ['Running', 'Swimming', 'Eating', 'Cycling'],
    datasets: [{
        data: [20, 10, 4, 2]
    }]
}
```
