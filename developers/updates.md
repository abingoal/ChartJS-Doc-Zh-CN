# 更新 Charts

在创建图表后更新图表是非常常见的。图表数据更改后，Chart.js 将动画显示新的数据值。

## 添加或移除数据

通过更改数据数组来支持添加和删除数据。要添加数据，只需将数据添加到数据数组中，如本例所示。

```javascript
function addData(chart, label, data) {
	chart.data.labels.push(label);
	chart.data.datasets.forEach(dataset => {
		dataset.data.push(data);
	});
	chart.update();
}
```

```javascript
function removeData(chart) {
	chart.data.labels.pop();
	chart.data.datasets.forEach(dataset => {
		dataset.data.pop();
	});
	chart.update();
}
```

## 禁止动画

有时当图表更新时，您可能不需要动画。为此，你可以设置`update` 的持续时间为 `0`.这将会同步渲染图表，而不需要动画。
