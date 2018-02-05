# 事件
以下属性定义图表如何事件交互。

| 名称 | 类别 | 默认值 | 描述
| ---- | ---- | ------- | -----------
| `events` | `String[]` | `["mousemove", "mouseout", "click", "touchstart", "touchmove", "touchend"]` |监听图表的悬停和工具提示 [更多...](#event-option)
| `onHover` | `Function` | `null` |当任何事件触发时调用。 在图表的上下文中调用，并传递事件和一系列活动元素（bars，points等）。
| `onClick` | `Function` | `null` |如果事件的类型为“mouseup”或“click”，则调用该函数。 在图表的上下文中调用，并传递事件和一系列活动元素。

## 事件选项 
例如，要让图表只响应点击事件，你可以这样做：

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        // 图表不会响应除click之外的事件
        events: ['click']
    }
});
```
