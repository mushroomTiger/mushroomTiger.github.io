## 概述
数组是JavaScript中最重要、最常用的数据结构之一，几乎在所有项目中都会频繁使用。掌握数组的各种操作方法不仅能提高编码效率，还能写出更优雅、性能更好的代码。本文系统整理了JavaScript数组的所有核心方法，从基础的ES5方法到现代的ES6+新增特性，涵盖创建、操作、遍历、转换等各个方面。通过详细的代码示例和分类说明，帮助开发者快速查阅、理解和掌握数组操作的每一个细节。

## 一、数组创建方式

### 字面量方式
```javascript
let arr1 = [];                 // 空数组
let arr2 = [5];                // 单元素数组
let arr3 = [5, 6, 7];          // 多元素数组
```

### 构造函数方式
```javascript
let arr1 = new Array();       // 空数组
let arr2 = new Array(5);      // 长度为5的空数组
let arr3 = new Array(5, 6, 7);// 多元素数组
```

## 二、数组方法汇总表

| 方法名 | 版本 | 功能描述 | 是否改变原数组 |
|--------|------|----------|----------------|
| concat() | ES5- | 合并数组 | 否 |
| join() | ES5- | 数组转字符串 | 否 |
| pop() | ES5- | 删除最后一项 | 是 |
| shift() | ES5- | 删除第一项 | 是 |
| unshift() | ES5- | 开头添加元素 | 是 |
| push() | ES5- | 末尾添加元素 | 是 |
| reverse() | ES5- | 反转数组 | 是 |
| slice() | ES5- | 截取数组 | 否 |
| sort() | ES5- | 数组排序 | 是 |
| splice() | ES5- | 增删改元素 | 是 |
| toString() | ES5- | 转为字符串 | 否 |
| valueOf() | ES5- | 返回原始值 | 否 |
| indexOf() | ES5 | 查找元素索引 | 否 |
| lastIndexOf() | ES5 | 反向查找索引 | 否 |
| forEach() | ES5 | 遍历数组 | 否 |
| map() | ES5 | 映射新数组 | 否 |
| filter() | ES5 | 过滤数组 | 否 |
| every() | ES5 | 全满足条件 | 否 |
| some() | ES5 | 任一满足条件 | 否 |
| reduce() | ES5 | 累计计算 | 否 |
| reduceRight() | ES5 | 反向累计 | 否 |

## 三、基础操作方法

### 1. concat() - 合并数组
```javascript
let arr1 = [1, 2, 3];
let arr2 = arr1.concat();              // 创建副本
console.log(arr1 === arr2);           // false
console.log(arr1.concat("hello"));    // [1,2,3,"hello"]
console.log(arr1);                    // [1,2,3] 原数组不变
```

### 2. join() - 数组转字符串
```javascript
let arr = [1, 2, 3];
console.log(arr.join());              // "1,2,3"
console.log(arr.join("-"));           // "1-2-3"
```

### 3. pop() - 删除最后元素
```javascript
let arr = [1, 2, 3];
console.log(arr.pop());               // 3
console.log(arr);                     // [1, 2]
```

### 4. shift() - 删除第一元素
```javascript
let arr = [1, 2, 3];
console.log(arr.shift());             // 1
console.log(arr);                     // [2, 3]
```

### 5. unshift() - 开头添加元素
```javascript
let arr = [1, 2, 3];
console.log(arr.unshift("a", "b"));   // 5 (新长度)
console.log(arr);                     // ["a","b",1,2,3]
```

### 6. push() - 末尾添加元素
```javascript
let arr = [1, 2, 3];
console.log(arr.push("x", "y"));      // 5 (新长度)
console.log(arr);                     // [1,2,3,"x","y"]
```

### 7. reverse() - 反转数组
```javascript
let arr = [1, 2, 3];
console.log(arr.reverse());           // [3, 2, 1]
console.log(arr);                     // [3, 2, 1] 原数组改变
```

### 8. slice() - 截取数组
```javascript
let arr = ["Tom", "Jack", "Lucy", "Lily"];
console.log(arr.slice(1, 3));         // ["Jack","Lucy"]
console.log(arr.slice(-2));           // ["Lily","May"]
console.log(arr.slice(1, -1));        // ["Jack","Lucy"]
```

### 9. sort() - 数组排序
```javascript
// 默认按字符排序
let arr1 = [6, 1024, 52];
console.log(arr1.sort());             // [1024, 52, 6]

// 数值排序
let arr2 = [6, 1024, 52];
console.log(arr2.sort((a, b) => a - b)); // [6, 52, 1024]
console.log(arr2.sort((a, b) => b - a)); // [1024, 52, 6] 降序
```

### 10. splice() - 增删改元素
```javascript
let arr = ["Tom", "Jack", "Lucy", "Lily"];

// 删除
console.log(arr.splice(1, 2));        // ["Jack","Lucy"]
console.log(arr);                     // ["Tom","Lily"]

// 替换
arr = ["Tom", "Jack", "Lucy", "Lily"];
console.log(arr.splice(1, 2, "A", "B")); // ["Jack","Lucy"]
console.log(arr);                     // ["Tom","A","B","Lily"]

// 插入
arr = ["Tom", "Jack", "Lucy"];
console.log(arr.splice(2, 0, "New")); // []
console.log(arr);                     // ["Tom","Jack","New","Lucy"]
```

### 11. toString() - 转为字符串
```javascript
let arr = [1, 2, 3];
console.log(arr.toString());          // "1,2,3"
```

### 12. valueOf() - 返回原始值
```javascript
let arr = [1, 2, 3];
console.log(arr.valueOf());           // [1, 2, 3]
console.log(arr.valueOf() === arr);   // true
```

## 四、查找和遍历方法

### 13. indexOf() - 查找元素索引
```javascript
let arr = ["h", "e", "l", "l", "o"];
console.log(arr.indexOf("l"));        // 2
console.log(arr.indexOf("l", 3));     // 3
console.log(arr.indexOf("x"));        // -1
```

### 14. lastIndexOf() - 反向查找
```javascript
let arr = ["h", "e", "l", "l", "o"];
console.log(arr.lastIndexOf("l"));    // 3
console.log(arr.lastIndexOf("l", 2)); // 2
```

### 15. forEach() - 遍历数组
```javascript
let arr = ["Tom", "Jack", "Lucy"];
let result = arr.forEach((value, index, array) => {
    console.log(`${value} - ${index} - ${array === arr}`);
});
// Tom - 0 - true
// Jack - 1 - true
// Lucy - 2 - true
console.log(result);                  // undefined
```

### 16. map() - 映射新数组
```javascript
let arr = [1, 2, 3];
let newArr = arr.map((value, index) => {
    return value * 2 + index;
});
console.log(newArr);                  // [2, 5, 8]
console.log(arr);                     // [1, 2, 3] 原数组不变
```

### 17. filter() - 过滤数组
```javascript
let arr = [1, 2, 3, 4, 5];
let filtered = arr.filter(value => value > 2);
console.log(filtered);                // [3, 4, 5]
```

### 18. every() - 全部满足条件
```javascript
let arr = [10, 20, 30];
let result1 = arr.every(value => value > 5);   // true
let result2 = arr.every(value => value > 15);  // false
```

### 19. some() - 任一满足条件
```javascript
let arr = [1, 2, 3, 4, 5];
let result1 = arr.some(value => value > 3);    // true
let result2 = arr.some(value => value > 10);   // false
```

### 20. reduce() - 累计计算
```javascript
let arr = [1, 2, 3, 4, 5];

// 求和
let sum = arr.reduce((prev, curr) => prev + curr, 0);
console.log(sum);                     // 15

// 求最大值
let max = arr.reduce((prev, curr) => Math.max(prev, curr));
console.log(max);                     // 5

// 数组扁平化
let arr2 = [[1, 2], [3, 4], [5]];
let flat = arr2.reduce((prev, curr) => prev.concat(curr), []);
console.log(flat);                    // [1, 2, 3, 4, 5]
```

### 21. reduceRight() - 反向累计
```javascript
let arr = ["a", "b", "c"];
let result = arr.reduceRight((prev, curr) => prev + curr);
console.log(result);                  // "cba"
```

## 五、ES6+新增方法（补充）

### 22. find() - 查找元素
```javascript
let arr = [5, 12, 8, 130, 44];
let found = arr.find(value => value > 10);
console.log(found);                   // 12
```

### 23. findIndex() - 查找索引
```javascript
let arr = [5, 12, 8, 130, 44];
let index = arr.findIndex(value => value > 10);
console.log(index);                   // 1
```

### 24. includes() - 是否包含
```javascript
let arr = [1, 2, 3];
console.log(arr.includes(2));         // true
console.log(arr.includes(4));         // false
```

### 25. flat() - 数组扁平化
```javascript
let arr = [1, [2, [3, [4]]]];
console.log(arr.flat());              // [1, 2, [3, [4]]]
console.log(arr.flat(2));             // [1, 2, 3, [4]]
console.log(arr.flat(Infinity));      // [1, 2, 3, 4]
```

### 26. flatMap() - 映射后扁平化
```javascript
let arr = [1, 2, 3];
let result = arr.flatMap(x => [x, x * 2]);
console.log(result);                  // [1, 2, 2, 4, 3, 6]
```

## 六、实用技巧

### 1. 数组去重
```javascript
// ES6 Set方式
let arr = [1, 2, 2, 3, 3, 4];
let unique1 = [...new Set(arr)];      // [1, 2, 3, 4]

// filter方式
let unique2 = arr.filter((value, index, array) => 
    array.indexOf(value) === index
);
```

### 2. 数组复制
```javascript
let arr = [1, 2, 3];
let copy1 = [...arr];                 // 扩展运算符
let copy2 = arr.slice();              // slice方法
let copy3 = Array.from(arr);          // Array.from
```

### 3. 数组合并
```javascript
let arr1 = [1, 2];
let arr2 = [3, 4];
let merged1 = [...arr1, ...arr2];     // [1, 2, 3, 4]
let merged2 = arr1.concat(arr2);      // [1, 2, 3, 4]
```

### 4. 数组判空
```javascript
let arr = [];
console.log(arr.length === 0);        // true
console.log(Array.isArray(arr) && !arr.length); // true
```

### 5. 获取最后元素
```javascript
let arr = [1, 2, 3];
let last1 = arr[arr.length - 1];      // 3
let last2 = arr.slice(-1)[0];         // 3
```

## 七、性能注意事项

1. **push/pop vs unshift/shift**: 在数组开头操作比在末尾操作慢
2. **for循环 vs forEach**: 大数据量时for循环性能更好
3. **slice vs splice**: slice不改变原数组，性能更好
4. **Set去重**: 大数据去重时Set性能最佳
5. **避免在循环中修改数组长度**: 可能导致意外结果

## 总结

数组是JavaScript中最常用的数据结构之一，掌握其各种方法对提升编程效率至关重要。建议：

1. 根据需求选择合适的方法
2. 注意方法是否改变原数组
3. 了解ES6+新增方法的兼容性
4. 在实际项目中多加练习，形成肌肉记忆