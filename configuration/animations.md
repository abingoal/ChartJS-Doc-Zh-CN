# 动画

Chart.js开箱即用动画图表。提供了许多选项来配置动画的外观以及动画时间。

## 动画配置

以下为全局选项，在`Chart.defaults.global.animation`中定义。

| 名称 | 类型 | 默认值 | 描述
| -----| ---- | --------| -----------
| `duration` | `Number` | `1000` | 动画所需的毫秒数
| `easing` | `String` | `'easeOutQuart'` | Easing [更多...](#easing)
| `onProgress` | `Function` | `null` | 每一步动画的回调 [更多...](#animation-callbacks)
| `onComplete` | `Function` | `null` | 动画结束后回调 [更多...](#animation-callbacks)

## Easing
 可用选项:
* `'linear'`
* `'easeInQuad'`
* `'easeOutQuad'`
* `'easeInOutQuad'`
* `'easeInCubic'`
* `'easeOutCubic'`
* `'easeInOutCubic'`
* `'easeInQuart'`
* `'easeOutQuart'`
* `'easeInOutQuart'`
* `'easeInQuint'`
* `'easeOutQuint'`
* `'easeInOutQuint'`
* `'easeInSine'`
* `'easeOutSine'`
* `'easeInOutSine'`
* `'easeInExpo'`
* `'easeOutExpo'`
* `'easeInOutExpo'`
* `'easeInCirc'`
* `'easeOutCirc'`
* `'easeInOutCirc'`
* `'easeInElastic'`
* `'easeOutElastic'`
* `'easeInOutElastic'`
* `'easeInBack'`
* `'easeOutBack'`
* `'easeInOutBack'`
* `'easeInBounce'`
* `'easeOutBounce'`
* `'easeInOutBounce'`

参考 [Robert Penner's easing equations](http://robertpenner.com/easing/).

## 动画回调

`onProgress`和`onComplete`回调对于外部操作同步到图表动画，回调传递一个`Chart.Animation`实例：

```javascript
{
    // Chart 对象
    chart: Chart,

    // 当前动画帧数
    currentStep: Number,

    // 动画帧数
    numSteps: Number,

    // easing动画使用
    easing: String,

    // 绘制图表
    render: Function,

    // 使用回调
    onAnimationProgress: Function,

    // 使用回调
    onAnimationComplete: Function
}
```

以下示例在图表动画期间填充进度条。
```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        animation: {
            onProgress: function(animation) {
                progress.value = animation.animationObject.currentStep / animation.animationObject.numSteps;
            }
        }
    }
});
```

这些回调的另一个例子可以在[Github](https://github.com/chartjs/Chart.js/blob/master/samples/animation/progress-bar.html)上找到：该示例显示一个进度条，显示动画的距离。