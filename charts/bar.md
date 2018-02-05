# 柱状/条形图(Bar)

柱状/条形图提供了一种以竖线表示数据值的显示方式。用来显示数据趋势，并排比较多个数据集。

{% chartjs %}
{
"type": "bar",
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
"backgroundColor": [
"rgba(255, 99, 132, 0.2)",
"rgba(255, 159, 64, 0.2)",
"rgba(255, 205, 86, 0.2)",
"rgba(75, 192, 192, 0.2)",
"rgba(54, 162, 235, 0.2)",
"rgba(153, 102, 255, 0.2)",
"rgba(201, 203, 207, 0.2)"
],
"borderColor": [
"rgb(255, 99, 132)",
"rgb(255, 159, 64)",
"rgb(255, 205, 86)",
"rgb(75, 192, 192)",
"rgb(54, 162, 235)",
"rgb(153, 102, 255)",
"rgb(201, 203, 207)"
],
"borderWidth": 1
}]
},
"options": {
"scales": {
"yAxes": [{
"ticks": {
"beginAtZero": true
}
}]
}
}
}
{% endchartjs %}

## 示例用法

```javascript
var myBarChart = new Chart(ctx, {
	type: "bar",
	data: data,
	options: options
});
```

## 数据集属性

柱状/条形图允许为每个数据集指定一些属性用于显示特定数据集。一些属性可以被指定为一个数组。如果这些设置为数组值，则第一个值应用于第一个节点，第二个值应用于第二个节点，依此类推。

| 名称                   | 类型              | 描述                                                                    |
| ---------------------- | ----------------- | ----------------------------------------------------------------------- |
| `label`                | `String`          | 在图例和工具提示中显示的数据集标签                                      |
| `xAxisID`              | `String`          | 绘制此数据集的 x 轴的 ID。如果未指定，则默认为第一个找到的 x 轴的 ID 。 |
| `yAxisID`              | `String`          | 绘制该数据集的 y 轴的 ID。如果未指定，则默认为第一个找到的 y 轴的 ID。  |
| `backgroundColor`      | `Color/Color[]`   | 柱状/条形图填充色. 参考 [颜色(Colors)](../general/colors.md#colors)     |
| `borderColor`          | `Color/Color[]`   | 边框色 参考 [颜色(Colors)](../general/colors.md#colors)                 |
| `borderWidth`          | `Number/Number[]` | 边框宽度(以像素为单位)                                                  |
| `borderSkipped`        | `String`          | 不绘制边框 [更多...](#borderSkipped)                                    |
| `hoverBackgroundColor` | `Color/Color[]`   | 悬浮时的填充色                                                          |
| `hoverBorderColor`     | `Color/Color[]`   | 悬浮时的边框色                                                          |
| `hoverBorderWidth`     | `Number/Number[]` | 悬浮时边框宽度                                                          |

### borderSkipped

此设置用于避免基线被填充。一般来说，除非创建从柱状/条形图派生的图表类型，否则不需要更改。

选项:

* 'bottom'
* 'left'
* 'top'
* 'right'

## 配置选项

柱状/条形图定义了以下配置选项。这些选项与全局图表配置选项`Chart.defaults.global`合并，形成最终传递给图表的选项。

| 名称                        | 类型      | 默认值 | 描述                                                                                                                                               |
| --------------------------- | --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `barPercentage`             | `Number`  | `0.9`  | 在 category 百分比内，每条 bar 的百分比(0-1)。如果设置为 1，则将使用 category 的整个宽度 [更多...](#bar-chart-barpercentage-vs-categorypercentage) |
| `categoryPercentage`        | `Number`  | `0.8`  | 每个数据点可用宽度的百分比[更多...](#bar-chart-barpercentage-vs-categorypercentage)                                                                |
| `barThickness`              | `Number`  |        | 手动设置每个 bar 的宽度像素。如果未设置，则使用 `barPercentage` 和 `categoryPercentage` 自动调整大小;                                              |
| `maxBarThickness`           | `Number`  |        | 设置该选项确保自动调整尺寸的 bar 的大小。仅当`barThickness`未设置时才能使用（自动调整大小已启用）。                                                |
| `gridLines.offsetGridLines` | `Boolean` | `true` | 如果为 true，则特定数据点的条形落在网格线之间。如果为 false，网格线将直接位于网格中间。[更多...](#offsetGridLines)                                 |

### offsetGridLines

如果为 true，则特定数据点的条形落在网格线之间。如果为 false，网格线将直接位于网格中间。在实际项目中这是不太可能需要改变的。一般通过不同的配置来重复使用。

此设置适用于条形图的轴配置。需要为每个新添加到图表中的轴设置此设置。

```javascript
options = {
	scales: {
		xAxes: [
			{
				gridLines: {
					offsetGridLines: true
				}
			}
		]
	}
};
```

## 默认选项

通常要将配置设置应用于所有创建的条形图。全局条形图设置存储在`Chart.defaults.bar`中。更改全局选项只会影响更改后创建的图表。现有图表不会更改。

## barPercentage vs categoryPercentage

以下显示了百分比选项与类别百分比选项之间的关系。

```text
// categoryPercentage: 1.0
// barPercentage: 1.0
Bar:        | 1.0 | 1.0 |
Category:   |    1.0    |
Sample:     |===========|

// categoryPercentage: 1.0
// barPercentage: 0.5
Bar:          |.5|  |.5|
Category:  |      1.0     |
Sample:    |==============|

// categoryPercentage: 0.5
// barPercentage: 1.0
Bar:            |1.||1.|
Category:       |  .5  |
Sample:     |==============|
```

## 数据结构

条形图数据集的`data`属性被指定为一个数字数组。数据数组中的每个点对应于 x 轴上相同索引处的标签。

```javascript
data: [20, 10];
```

# 堆积条形图

条形图可以通过改变 X 轴和 Y 轴上的设置来启用堆叠，将其配置为堆叠条形图。堆积的条形图可以用来显示一个数据系列是如何由许多小块构成的。

```javascript
var stackedBar = new Chart(ctx, {
	type: "bar",
	data: data,
	options: {
		scales: {
			xAxes: [
				{
					stacked: true
				}
			],
			yAxes: [
				{
					stacked: true
				}
			]
		}
	}
});
```

## 数据集属性

以下数据集属性特定于堆叠条形图。

| 名称    | 类型     | 描述                                                        |
| ------- | -------- | ----------------------------------------------------------- |
| `stack` | `String` | 该数据集所属的组的 ID（堆叠时，每个组将是一个单独的 stack） |

# 水平条形图

水平条形图是垂直条形图上的变体。它有时用来显示趋势数据，并排比较多个数据集。

{% chartjs %}
{
"type": "horizontalBar",
"data": {
"labels": ["January", "February", "March", "April", "May", "June", "July"],
"datasets": [{
"label": "My First Dataset",
"data": [65, 59, 80, 81, 56, 55, 40],
"fill": false,
"backgroundColor": [
"rgba(255, 99, 132, 0.2)",
"rgba(255, 159, 64, 0.2)",
"rgba(255, 205, 86, 0.2)",
"rgba(75, 192, 192, 0.2)",
"rgba(54, 162, 235, 0.2)",
"rgba(153, 102, 255, 0.2)",
"rgba(201, 203, 207, 0.2)"
],
"borderColor": [
"rgb(255, 99, 132)",
"rgb(255, 159, 64)",
"rgb(255, 205, 86)",
"rgb(75, 192, 192)",
"rgb(54, 162, 235)",
"rgb(153, 102, 255)",
"rgb(201, 203, 207)"
],
"borderWidth": 1
}]
},
"options": {
"scales": {
"xAxes": [{
"ticks": {
"beginAtZero": true
}
}]
}
}
}
{% endchartjs %}

## 示例

```javascript
var myBarChart = new Chart(ctx, {
	type: "horizontalBar",
	data: data,
	options: options
});
```

## 配置选项

水平条形图的配置选项与[条形图(bar)](../bar/config-options.md#config-options)相同。但是，任何在条形图中 x 轴上指定的选项都将应用于水平条形图中的 y 轴。

默认的水平栏配置选项在`Chart.defaults.horizo​​ntalBar`中设置。
