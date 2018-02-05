# 图例配置

显示图表上出现的区域数据集的图例。

## 配置选项

图例配置在 `options.legend` 中.全局配置在 `Chart.defaults.global.legend`。

| 名称        | 类型       | 默认值  | 描述                                                      |
| ----------- | ---------- | ------- | --------------------------------------------------------- |
| `display`   | `Boolean`  | `true`  | 是否显示                                                  |
| `position`  | `String`   | `'top'` | 位置 [更多...](#position)                                 |
| `fullWidth` | `Boolean`  | `true`  | 是否铺满画布，此配置不常改变                              |
| `onClick`   | `Function` |         | 标签项的回调事件                                          |
| `onHover`   | `Function` |         | 'mousemove' 事件注册在标签项上时的回调                    |
| `reverse`   | `Boolean`  | `false` | 以相反的顺序显示数据集                                    |
| `labels`    | `Object`   |         | 参阅下面的[图例标签配置](#legend-label-configuration)部分 |

## 位置

图例的位置选项：

* `'top'`
* `'left'`
* `'bottom'`
* `'right'`

## 图例标签配置

图例标签配置使用`label`关键字。

| 名称             | 类型       | 默认值                                                 | 描述                                                                                                                                        |
| ---------------- | ---------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `boxWidth`       | `Number`   | `40`                                                   | 宽度                                                                                                                                        |
| `fontSize`       | `Number`   | `12`                                                   | 字体大小                                                                                                                                    |
| `fontStyle`      | `String`   | `'normal'`                                             | 字体样式                                                                                                                                    |
| `fontColor`      | Color      | `'#666'`                                               | 字体颜色                                                                                                                                    |
| `fontFamily`     | `String`   | `"'Helvetica Neue', 'Helvetica', 'Arial', sans-serif"` | 字体集                                                                                                                                      |
| `padding`        | `Number`   | `10`                                                   | 每个图例之间的间距                                                                                                                          |
| `generateLabels` | `Function` |                                                        | 为图例中的每个事物生成图例项目。默认实现返回颜色框的文本+样式。有关详细信息，请参阅[图例项目](#chart-configuration-legend-item-interface)。 |
| `filter`         | `Function` | `null`                                                 | 从图例中过滤图例。接收 2 个参数，[图例项目](<(#chart-configuration-legend-item-interface)>)和图表数据。                                     |
| `usePointStyle`  | `Boolean`  | `false`                                                | 标签样式将匹配相应的点样式（大小基于 fontSize，boxWidth 不在这种情况下使用）。                                                              |

## 图例项目接口

传递给图例`onClick`函数的项目是从`labels.generateLabels`返回的项目。这些项目必须实现以下接口。

```javascript
{
    // 要显示的标签
    text: String,

    // 填充图例框的样式
    fillStyle: Color,

    // 如果为true，则表示隐藏的数据集。标签将以透视效果呈现。
    hidden: Boolean,

    // 边框 参考 https://developer.mozilla.org/en/docs/Web/API/CanvasRenderingContext2D/lineCap
    lineCap: String,

    // 边框 参考 https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/setLineDash
    lineDash: Array[Number],

    // 边框 参考  https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineDashOffset
    lineDashOffset: Number,

    // 边框 参考 https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/lineJoin
    lineJoin: String,

    // 边框宽度
    lineWidth: Number,

    // 图例框的描边样式
    strokeStyle: Color

    // 图例框的点样式（仅当usePointStyle为true时才使用）
    pointStyle: String
}
```

## Example

The following example will create a chart with the legend enabled and turn all of the text red in color.

```javascript
var chart = new Chart(ctx, {
	type: "bar",
	data: data,
	options: {
		legend: {
			display: true,
			labels: {
				fontColor: "rgb(255, 99, 132)"
			}
		}
	}
});
```

## Custom On Click Actions

It can be common to want to trigger different behaviour when clicking an item in the legend. This can be easily achieved using a callback in the config object.

The default legend click handler is:

```javascript
function(e, legendItem) {
    var index = legendItem.datasetIndex;
    var ci = this.chart;
    var meta = ci.getDatasetMeta(index);

    // See controller.isDatasetVisible comment
    meta.hidden = meta.hidden === null? !ci.data.datasets[index].hidden : null;

    // We hid a dataset ... rerender the chart
    ci.update();
}
```

Lets say we wanted instead to link the display of the first two datasets. We could change the click handler accordingly.

```javascript
var defaultLegendClickHandler = Chart.defaults.global.legend.onClick;
var newLegendClickHandler = function(e, legendItem) {
	var index = legendItem.datasetIndex;

	if (index > 1) {
		// Do the original logic
		defaultLegendClickHandler(e, legendItem);
	} else {
		let ci = this.chart;
		[ci.getDatasetMeta(0), ci.getDatasetMeta(1)].forEach(function(meta) {
			meta.hidden =
				meta.hidden === null ? !ci.data.datasets[index].hidden : null;
		});
		ci.update();
	}
};

var chart = new Chart(ctx, {
	type: "line",
	data: data,
	options: {
		legend: {}
	}
});
```

Now when you click the legend in this chart, the visibility of the first two datasets will be linked together.

## HTML Legends

Sometimes you need a very complex legend. In these cases, it makes sense to generate an HTML legend. Charts provide a `generateLegend()` method on their prototype that returns an HTML string for the legend.

To configure how this legend is generated, you can change the `legendCallback` config property.

```javascript
var chart = new Chart(ctx, {
	type: "line",
	data: data,
	options: {
		legendCallback: function(chart) {
			// Return the HTML string here.
		}
	}
});
```
