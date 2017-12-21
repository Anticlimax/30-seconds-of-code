# 30秒可理解的代码段译文版([原文](https://chalarangelo.github.io/30-seconds-of-code/))

## arrayMax

返回一个数组里的最大值。
使用`Math.max()`配合扩展操作符(`...`)来获得一个数组里的最大值。
```
const arrayMax = arr => Math.max(...arr);
// arrayMax([10, 1, 5]) -> 10
```

## arrayMin

返回一个数组里的最小值。
使用`Math.min()`配合扩展操作符(`...`)来获得一个数组里的最小值。
```
const arrayMin = arr => Math.min(...arr);
// arrayMin([10, 1, 5]) -> 1
```

## chunk

把一个数组分成指定大小的小数组。
使用`Array.from()`创建一个新的、符合将要生成chunk数量的数组。使用`Array.slice()`将新数组中的每个元素映射成长度为`size`的chunk。如果原来的数组不能被均匀分割，最后一个chunk将包含剩余的元素。
```
const chunk = (arr, size) => 
  Array.from({length: Math.ceil(arr.length / size)}, (v, i) => arr.slice(i * size, i * size + size));
// chunk([1,2,3,4,5], 2) -> [[1,2],[3,4],[5]]
```

## compact

移除数组中错误的值。
使用`Array.filter()`过滤出错误的值(`false`, `null`, `0`, `""`, `undefined`和`NaN`)
```
const compact = (arr) => arr.filter(Boolean)
// compact([0, 1, false, 2, '', 3, 'a', 'e'*23, NaN, 's', 34]) -> [1, 2, 3, 'a', 's', 34]
```

## countOccurrences

计算数组中一个值的出现次数。
每次遇到数组中的特定值时，使用`Array.reduce()`来递增计数器。
```
const countOccurrences = (arr, value) => arr.reduce((a, v) => v === value ? a + 1: a + 0, 0)
// countOccurrences([1,1,2,1,2,3], 1) -> 3