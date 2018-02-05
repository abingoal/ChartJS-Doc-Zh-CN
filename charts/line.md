# 折线图(Line)

折线图是在一条线上绘制数据点的展现方式。通常用于显示趋势数据或两个数据集的比较。

{% chartjs %}
{
"type": "line",
"data": {
"labels": [
"January",
"February",
"March",
"April",
"May",
"June",
"July"
],
"datasets": [{
"label": "My First Dataset",
"data": [65, 59, 80, 81, 56, 55, 40],
"fill": false,
"borderColor": "rgb(75, 192, 192)",
"lineTension": 0.1
}]
},
"options": {

    }

}
{% endchartjs %}

## 示例用法

```javascript
var myLineChart = new Chart(ctx, {
	type: "line",
	data: data,
	options: options
});
```

## 数据集属性

折线图允许为每个数据集指定多个属性以显示特定数据集。所有 point \*属性都可以被指定为一个数组。如果这些设置为数组值，则第一个值应用于第一个点，第二个值应用于第二个点，依此类推。

| 名称                        | 类型                            | 描述                                                                                                                   |
| --------------------------- | ------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `label`                     | `String`                        | 在图例和工具提示中显示的数据集的标签。                                                                                 |
| `xAxisID`                   | `String`                        | 绘制此数据集的 x 轴的 ID。如果未指定，则默认为第一个找到的 x 轴的 ID。                                                 |
| `yAxisID`                   | `String`                        | 绘制该数据集的 y 轴的 ID。如果未指定，则默认为第一个找到的 y 轴的 ID。                                                 |
| `backgroundColor`           | `Color/Color[]`                 | 线条背景色 参考 [颜色(Colors)](../general/colors.md#colors)                                                            |
| `borderColor`               | `Color/Color[]`                 | 线条颜色 参考 [颜色(Colors)](../general/colors.md#colors)                                                              |
| `borderWidth`               | `Number/Number[]`               | 线的宽度(以像素为单位)                                                                                                 |
| `borderDash`                | `Number[]`                      | 破折号的长度和间距。 参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/setLineDash) |
| `borderDashOffset`          | `Number`                        | 偏移量 参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineDashOffset)            |
| `borderCapStyle`            | `String`                        | 线帽样式 参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineCap)                 |
| `borderJoinStyle`           | `String`                        | 线连接风格 参考 [MDN](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineJoin)              |
| `cubicInterpolationMode`    | `String`                        | 离散的点之间的连接方式 [更多...](#cubicInterpolationMode)                                                              |
| `fill`                      | `Boolean/String`                | 折线区域的填充方式 [更多...](#fill)                                                                                    |
| `lineTension`               | `Number`                        | 贝塞尔曲线张力。设置为 0 绘制直线。如果使用单调立方插值，则忽略此选项。                                                |
| `pointBackgroundColor`      | `Color/Color[]`                 | 点的填充色                                                                                                             |
| `pointBorderColor`          | `Color/Color[]`                 | 点的边框色                                                                                                             |
| `pointBorderWidth`          | `Number/Number[]`               | 点边框宽度(以像素为单位)                                                                                               |
| `pointRadius`               | `Number/Number[]`               | 点的半径。如果设置为 0，则不显示。                                                                                     |
| `pointStyle`                | `String/String[]/Image/Image[]` | 数据点的样式 [更多...](#pointStyle)                                                                                    |
| `pointHitRadius`            | `Number/Number[]`               | 对鼠标事件作出响应的非显示点的像素大小。                                                                               |
| `pointHoverBackgroundColor` | `Color/Color[]`                 | 鼠标悬浮时点背景颜色。                                                                                                 |
| `pointHoverBorderColor`     | `Color/Color[]`                 | 鼠标悬浮时点的边框色                                                                                                   |
| `pointHoverBorderWidth`     | `Number/Number[]`               | 鼠标悬浮时点的边框宽度                                                                                                 |
| `pointHoverRadius`          | `Number/Number[]`               | 鼠标悬浮时点的半径大小                                                                                                 |
| `showLine`                  | `Boolean`                       | 如果设置 false，则不会为此数据集绘制线条。                                                                             |
| `spanGaps`                  | `Boolean`                       | 如果为 true，则会在没有或为空数据的点之间绘制线条。如果为 false，则带有 NaN 数据的点会产生一个中断                     |
| `steppedLine`               | `Boolean/String`                | 是否显示为阶梯线 [更多...](#stepped-line)                                                                              |

### cubicInterpolationMode

支持以下插值模式：

* 'default'
* 'monotone'.

“default”使用自定义加权立方插值，为所有类型的数据集生成曲线。

“monotone”更适合于`y = f（x）`数据集：它保留被插值数据集的单调性（或分段单调性），并确保局部极值（如果有的话）停留在输入数据点。

如果保持不变（`undefined`），则使用全局`·options.elements.line.cubicInterpolationMode`属性。

### fill

如果为`true`，则填写该行下面的区域。该行被填充到基线。如果 y 轴有一个 0 值，那么该行就被填充到该点。如果该轴只有负值，则该线将填充到最高值。如果轴只有正值，则将其填充到最低值。

要填充到特定位置的字符串值：

* `'zero'`
* `'top'`
* `'bottom'`

### pointStyle

数据点的样式选项如下：

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

如果选项是图片，则使用[drawImage](https://developer.mozilla.org/en/docs/Web/API/CanvasRenderingContext2D/drawImage)在 canvas 上绘制该图像。

### Stepped Line

`stepsLine`支持以下值:

* `false`: 不设置 (默认)
* `true`: 数值之前绘制线条 (等于. 'before')
* `'before'`: 之前
* `'after'`: 之后

[参考实例](http://www.chartjs.org/samples/latest/charts/line/stepped.html)
如果设置`stepsLine`值为 false 以外的任何值，`lineTension`将被忽略。

## 配置选项

折线图定义了以下配置选项。这些选项与全局图表配置选项`Chart.defaults.global`合并，形成最终传递给图表的选项。

| 名称        | 类型      | 默认值  | 描述                                           |
| ----------- | --------- | ------- | ---------------------------------------------- |
| `showLines` | `Boolean` | `true`  | 如果为 false，则在数据点之间不显示线条         |
| `spanGaps`  | `Boolean` | `false` | 如果为 false, NaN 数据会在折线中间显示一个间断 |

## 默认选项

通常要将配置设置应用于所有创建的折线图。全局折线图设置存储在`Chart.defaults.line`中。更改全局选项只会影响更改后创建的图表。现有图表不会更改。

例如，要使用`spanGaps = true`配置所有折线图，应该这样：

```javascript
Chart.defaults.line.spanGaps = true;
```

## 数据结构

线形图数据集的数据属性可以使用两种方式。

### Number[]

```javascript
data: [20, 10];
```

当数据是数字数组时，x 轴通常是一个[category](../axes/cartesian/category.md#Category Axis)。数据点则按照在数组中的索引，依次显示在图表上。使用 category 轴创建折线图时，必须指定数据对象的`labels`属性。

### Point[]

```javascript
data: [
	{
		x: 10,
		y: 20
	},
	{
		x: 15,
		y: 10
	}
];
```

此项用于稀疏数据集，例如[散点图(scatter charts)](./scatter.md#scatter-chart)中的数据集。每个数据点都使用包含`x`和 `y` 属性的对象来指定。

# 堆积面积图

通过更改 `y` 轴上的设置以启用堆叠，折线图可以配置为堆积面积图。堆积面积图可以用来显示一个数据趋势是如何由多个小块组成的。

```javascript
var stackedLine = new Chart(ctx, {
	type: "line",
	data: data,
	options: {
		scales: {
			yAxes: [
				{
					stacked: true
				}
			]
		}
	}
});
```

# 高性能折线图

绘制大量数据时，图表渲染时间可能会开始变得相当长。在这种情况下，可以使用以下策略来提高性能。

## 数据抽取

抽取有意义的数据来实现最佳效果。当图表上显示大量数据时，在仅有几百像素宽的图表上显示数以万计的数据点是没有意义的。

数据抽取有许多方法，算法的选择取决于你的数据和你想要达到的结果。例如，[最小/最大](http://digital.ni.com/public.nsf/allkb/F694FFEEA0ACF282862576020075F784)抽取将保留数据中的峰值，但每个像素最多可能需要 4 个点。这种类型的抽取对于在非常嘈杂的数据中查看峰值数据很有效。

## 禁用贝塞尔曲线

在图表上绘制直线比贝塞尔曲线更高效，因此禁用贝塞尔曲线将提高渲染时间。

要为整个图表禁用贝塞尔曲线，执行以下操作：

```javascript
new Chart(ctx, {
	type: "line",
	data: data,
	options: {
		elements: {
			line: {
				tension: 0 // 禁用贝塞尔曲线
			}
		}
	}
});
```

## 不渲染线条

如果有很多数据点，那么可以禁用线条的的渲染并仅绘制点。这样做意味着在画布上绘画将会减少更多渲染，从而提高性能。

要禁用线条渲染，可执行以下操作:

```javascript
new Chart(ctx, {
	type: "line",
	data: {
		datasets: [
			{
				showLine: false // 为单个数据集禁用
			}
		]
	},
	options: {
		showLines: false // 为所有的数据集禁用
	}
});
```

## 禁用动画

如果你的图表渲染需要很长时间，那么禁用动画是一个好办法。这样做意味着图表只需要在更新期间渲染而不是多次渲染。这将减少 CPU 使用率并改善一般页面的性能。

To disable animations

```javascript
new Chart(ctx, {
	type: "line",
	data: data,
	options: {
		animation: {
			duration: 0 // 一般动画时间
		},
		hover: {
			animationDuration: 0 // 悬停项目时动画的持续时间
		},
		responsiveAnimationDuration: 0 // 调整大小后的动画持续时间
	}
});
```
