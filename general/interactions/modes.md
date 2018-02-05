# 交互模式

通过配置与图形悬停或工具提示的交互时，可以使用多种不同的模式。

这些模式将在下面详细说明，以及它们与交点设置的结合方式。

## 交叉点
显示交叉点上的数据

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'point'
        }
    }
})
```

## nearest
获取最接近点的项目。最近的项目是根据与图表项目中心的距离（point, bar）确定的。如果2个以上的条目距离相同，则使用最小面积的条目。
如果`intersect`为true，则仅当鼠标位置与图形中的项目相交时触发。这对于组合图非常有用，其中点隐藏在bars后面。

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'nearest'
        }
    }
})
```

## single (已废弃)
Finds the first item that intersects the point and returns it. Behaves like 'nearest' mode with intersect = true.

## label (已废弃)
参考 `'index'` 

## 索引
查找相同索引项。如果`intersect`为true，则第一个相交项用于确定数据中的索引。如果 `intersect`为false，则使用最近的项来确定索引。

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'index'
        }
    }
})
```

## x轴 (已废弃)
类似设置`intersect = false`的`'index'`模式

## 数据集
查找相同索引项。如果`intersect`为true，则第一个相交项用于确定数据中的索引。如果 `intersect`为false，则使用最近的项来确定索引。

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'dataset'
        }
    }
})
```

## x
返回基于`X`坐标相交的所有项目。对于垂直游标实现将是有用的。仅适用于笛卡尔图表。

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'x'
        }
    }
})
```

## y
返回基于`Y`坐标相交的所有项目。这对于水平光标实现将是有用的。仅适用于笛卡尔图表。

```javascript
var chart = new Chart(ctx, {
    type: 'line',
    data: data,
    options: {
        tooltips: {
            mode: 'y'
        }
    }
})
```