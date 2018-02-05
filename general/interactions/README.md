# 交互

hover配置通过`options.hover`改变。全局hover配置位于`Chart.defaults.global.hover`。要配置哪些事件触发图表交互，请参阅[事件](./events.md#events)。


| 名称 | 类型 | 默认值 | 描述
| ---- | ---- | ------- | -----------
| `mode` | `String` | `'nearest'` | 设置工具提示中出现的元素。有关详细信息，请参考[交互模式](./modes.md#interaction-modes)。
| `intersect` | `Boolean` | `true` | 如果为`true`，则hover仅适用于鼠标位置的图表进行相交。
| `animationDuration` | `Number` | `400` | hover动画时间（毫秒单位））