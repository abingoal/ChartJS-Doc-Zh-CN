# 配置

该配置用于更改图表的行为。用属性来控制样式，字体，图例等。

## 全局配置


此概念在Chart.js 1.0中引入，以保持配置[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)，并允许跨图表类型全局更改选项，避免为每个实例指定选项或特定图表类型的默认值。

Chart.js将传递给图表的选项对象与使用图表类型默认值的全局配置合并，并适当缩放默认值。这样您可以按照您在单个图表配置中的特定要求，同时在适用的情况下仍然更改所有图表类型的默认值。 全局常规选项在`Chart.defaults.global`中定义。每个图表类型的默认值在该图表类型的文档中讨论。

以下示例将将所有图表的hover模式设置为“nearest”，其中图表类型默认值不会被覆盖，或者在创建时传递给构造函数。

```javascript
Chart.defaults.global.hover.mode = 'nearest';
//hover模式设置为nearest，因为它不被覆盖
var chartHoverModeNearest  = new Chart(ctx, {
    type: 'line',
    data: data,
});

// 该图标的hover模式自定义传入
var chartDifferentHoverMode = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        hover: {
            // 覆盖全局设置
            mode: 'index'
        }
    }
})
```

