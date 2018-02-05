# 响应式图表
当根据窗口大小更改图表大小时，主要的限制是画布渲染大小（`canvas.width`和`.height`）不能用相对值表示，与显示大小相反（`canvas.style.width`和`.height`）。此外，这些尺寸彼此独立，因此画布渲染尺寸不会根据显示尺寸自动调整，从而使渲染不准确。

以下示例不起作用：

- `<canvas height="40vh" width="80vw">`: 无效值，画布不调整大小 ([示例](https://codepen.io/chartjs/pen/oWLZaR))
- `<canvas style="height:40vh; width:80vw">`: 无效的行为，画布调整大小但变得模糊([example](https://codepen.io/chartjs/pen/WjxpmO))

Chart.js提供了几个[选项](#configuration-option)，通过检测画布显示大小何时更改并相应地更新渲染大小来启用响应并控制图表的大小调整行为。

## 配置选项

| 名称 | 类型 | 默认值 | 描述
| ---- | ---- | ------- | -----------
| `responsive` | `Boolean` | `true` | 调整图表画布的容器大小 ([重要提示](#important-note)).
| `responsiveAnimationDuration` | `Number` | `0` | 调整大小后执行动画时间（以毫秒为单位））
| `maintainAspectRatio` | `Boolean` | `true` | 保持原有的宽高比
| `onResize` | `Function` | `null` | 调整大小时调用,获取传递两个参数：图表实例和新大小

## 重要提示

不能直接从`CANVAS`元素检测画布尺寸何时改变。Chart.js使用其父容器来更新canvas渲染和显示大小。然而，该方法要求容器相对定位。强烈建议将此容器专用于图表canvas,然后可以通过设置容器大小的相对值来实现响应：

[例如](https://codepen.io/chartjs/pen/YVWZbz)
```html
<div class="chart-container" style="position: relative; height:40vh; width:80vw">
    <canvas id="chart"></canvas>
</div>
```
也可以通过修改容器大小来改变图表大小：

```javascript
chart.canvas.parentNode.style.height = '128px';
```
