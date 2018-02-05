# 图表原型方法

对于每个图表，共享`ChartType`上有一组全局原型方法，你可能会发现它们很有用。这些在 Chart.js 创建的所有图表上都可用，但是对于这些示例，我们使用我们制作的折线图。

```javascript
// For example:
var myLineChart = new Chart(ctx, config);
```

## .destroy()

使用此方法来销毁我们创建的任何图表实例。这将会清除 Chart.js 中对 chart 对象的所有引用，以及由 Chart.js 附加的任何关联的事件监听。该方法必须在 canvas 重新用于新图表之前调用。

```javascript
// Destroys a specific chart instance
myLineChart.destroy();
```

## .update(duration, lazy)

触发图表的更新。这可以在更新数据对象之后安全地调用。这将更新所有的比例，图例，然后重新渲染图表。

```javascript
// duration is the time for the animation of the redraw in milliseconds
// lazy is a boolean. if true, the animation can be interrupted by other animations
myLineChart.data.datasets[0].data[2] = 50; // Would update the first dataset's value of 'March' to be 50
myLineChart.update(); // Calling update now animates the position of March from 90 to 50.
```

> **注意:** 只在替换数据引用时起作用 (例如 `myLineChart.data = {datasets: [...]}`

> **version 2.6**. 在此之前，使用以下解决方法可以替换整个数据对象： `myLineChart.config.data = {datasets: [...]}`.

参考 [更新图表(Updating Charts)](updates.md) 查看更多细节

## .reset()

将图表重置为初始动画之前的状态。然后可以使用`update`来触发新的动画。

```javascript
myLineChart.reset();
```

## .render(duration, lazy)

触发所有图表元素的重绘。 请注意，这不会更新新数据的元素。 在这种情况下使用`.update（）`。

```javascript
// duration is the time for the animation of the redraw in milliseconds
// lazy is a boolean. if true, the animation can be interrupted by other animations
myLineChart.render(duration, lazy);
```

## .stop()

使用它来停止任何当前的动画循环。 这将在当前的动画帧中暂停图表。 调用`.render（）`重新启用动画。

```javascript
// Stops the charts animation loop at its current frame
myLineChart.stop();
// => returns 'this' for chainability
```

## .resize()

使用该方法来手动调整画布元素的大小。 每次调整 canvas 容器的大小时都会执行此操作，但如果要更改 canvas 节点容器元素的大小，则可以手动调用此方法。

```javascript
// Resizes & redraws to fill its container element
myLineChart.resize();
// => returns 'this' for chainability
```

## .clear()

将清除图表 canvas。 在动画帧之间广泛使用。

```javascript
// Will clear the canvas that myLineChart is drawn on
myLineChart.clear();
// => returns 'this' for chainability
```

## .toBase64Image()

返回当前状态的图表的基本 64 位编码字符串

```javascript
myLineChart.toBase64Image();
// => returns png data url of the image on the canvas
```

## .generateLegend()

返回该图表的从`legendCallback`选项中生成的图例 HTML 字符串。

```javascript
myLineChart.generateLegend();
// => returns HTML string of a legend for this chart
```

## .getElementAtEvent(e)

在 Chart 实例上调用`getElementAtEvent（event）`传递一个事件或 jQuery 事件的参数将返回事件位置的单个元素。 如果范围内有多个项目，则只返回第一个项目。 从这个方法返回的值是一个带有单个参数的数组，用于保持`get * AtEvent`方法之间的一致的 API。

```javascript
myLineChart.getElementAtEvent(e);
// => returns the first element at the event point.
```

## .getElementsAtEvent(e)

查找事件点下的元素，然后返回相同数据索引处的所有元素。 在内部用于“标签”模式突出显示。在 Chart 实例上调用`getElementsAtEvent（event )`传递一个事件的参数或 jQuery 事件，将返回那个事件的相同位置上的点元素。

```javascript
canvas.onclick = function(evt) {
	var activePoints = myLineChart.getElementsAtEvent(evt);
	// => activePoints is an array of points on the canvas that are at the same position as the click event.
};
```

这个功能对于实现基于 DOM 的工具提示，或者在应用程序中触发自定义行为是有用的。

## .getDatasetAtEvent(e)

查找事件点下的元素，然后返回该数据集中的所有元素。 在内部用于'dataset'模式突出显示。

```javascript
myLineChart.getDatasetAtEvent(e);
// => returns an array of elements
```

## .getDatasetMeta(index)

查找与当前索引相匹配的数据集并返回该元数据。 此返回的数据具有用于构建图表的所有元数据。

元数据的`data`属性将包含关于每个点，矩形等的信息，具体取决于图表类型。
[Chart.js tests](https://github.com/chartjs/Chart.js/tree/master/test)中提供了大量的用法示例。

```javascript
var meta = myChart.getDatasetMeta(0);
var x = meta.data[0]._model.x;
```
