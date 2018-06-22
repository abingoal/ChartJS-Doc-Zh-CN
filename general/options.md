# 选项

## 可编写脚本的选项

可编写脚本的选项还接受为每个数据调用的函数，并采用表示上下文信息的唯一参数`context`(参见[option context](options.md#选项上下文))。

示例:

```javascript
color: function(context) {
    var index = context.dataIndex;
    var value = context.dataset.data[index];
    return value < 0 ? 'red' :  // draw negative values in red
        index % 2 ? 'blue' :    // else, alternate values in blue and green
        'green';
}
```

> **注意:** 只有几个气泡图选项支持脚本选项

## 可索引选项

可索引选项也接受一个数组，其中每个项目与相同索引处的元素相对应。 请注意，此方法需要提供与数据一样多的项目，因此，在大多数情况下，如果支持，则使用[function](#可编写脚本的选项)更为适用。

示例:

```javascript
color: [
    'red',    // color for data at index 0
    'blue',   // color for data at index 1
    'green',  // color for data at index 2
    'black',  // color for data at index 3
    //...
]
```

## 选项上下文

选项上下文用于在解析选项时提供上下文信息，并且当前仅适用于[scriptable options](#可脚本化选项)

上下文对象包含以下属性：

- `chart`: 相关的图表
- `dataIndex`: 当前数据的索引
- `dataset`: 位于索引`datasetIndex`处的数据集
- `datasetIndex`: 当前数据集的索引

**重要**: 由于上下文可以表示不同类型的实体（数据集，数据等），因此某些属性可能是 `undefined` ，因此在使用它之前一定要测试任何上下文属性。
