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
```

## deepFlatten
深度拍平一个数组。
使用递归。将`Array.concat()`和一个空数组(`[]`)以及扩展运算符(`...`)来拍平一个数组。递归的拍平数组中的每个元素。
```
const deepFlatten = arr => [].concat(...arr.map(v => Array.isArray(v) ? deepFlatten(v) : v))
// deepFlatten([1,[2],[[3],4],5]) -> [1,2,3,4,5]
```

## difference
返回两个数组的不同值。
基于`b`创建一个`Set`，然后对`a`使用`Array.filter()`只保留不包含于`b`中的值。
```
const difference = (a, b) => {const s = new Set(b); return a.filter(x => !s.has(x))}
// difference([1,2,3], [1,2,4]) -> [3]
```

## differenceWith
过滤比较函数中不返回`true`的数组中的所有值。
使用`Array.filter()`和`Array.find()`来找出合适的值。
```
const differenceWith = (arr, val, comp) => arr.filter(a => !val.find(b => comp(a, b)))
// differenceWith([1, 1.2, 1.5, 3], [1.9 ,3], (a, b) => Math.round(a) == Math.round(b)) -> [1, 1.2]
```

## distinctValuesOfArray
返回数组中的所有不同值。
使用ES6`Set`和`...rest`操作符来除去所有重复的值。
```
const distinctValuesOfArray => arr => [...new Set(arr)]
// distinctValuesOfArray([1,2,2,3,4,4,5]) -> [1,2,3,4,5]
```

## dropElements
删除数组中的元素，直到传递的函数返回`true`。
返回数组的剩余元素。
遍历这个数组，使用`Array,slice()`删除数组的第一个元素直到函数的返回值为`true`。返回数组的剩余元素。
```
const dropElements = (arr, func) => {
  while (arr.length > 0 && !func(arr[0])) arr = arr.slice(1)
  return arr
}
// dropElements([1, 2, 3, 4], n => n >= 3) -> [3, 4]
```

## dropRight
返回从右边删除`n`个元素的新数组。
检查`n`是否比给定数组长度小，并且使用`Array.slice()`来相应的切片或返回一个空数组。
```
const dropRight = (arr, n = 1) => n < arr.length ? arr.slice(0, arr.length - n) : []
// dropRight([1,2,3]) -> [1,2]
// dropRight([1,2,3], 2) -> [1]
// dropRight([1,2,3], 42) -> []
```

