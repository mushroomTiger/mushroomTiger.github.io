## 概述
字符串操作是JavaScript编程中极其重要且频繁使用的技能。本文全面整理了字符串的属性和方法，旨在帮助开发者系统掌握相关技术。

## String对象属性

### length属性
获取字符串的长度，中文字符每个汉字代表一个字符。

```javascript
var str = 'abc';
console.log(str.length); // 返回3
```

### prototype属性
用于扩展String对象的方法，所有实例共享。

```javascript
// 添加去除两边空格的方法
String.prototype.trim = function(){
    return this.replace(/^\s*|\s*$/g, '');
}
```

## String对象方法

### 一、字符获取类方法

#### 1. charAt(index)
获取指定索引位置的字符。

```javascript
var str = 'abcde';
console.log(str.charAt(2));     // 返回 'c'
console.log(str.charAt(8));     // 返回空字符串
```

#### 2. charCodeAt(index)
返回指定位置字符的Unicode编码。

```javascript
var str = 'abcde';
console.log(str.charCodeAt(0)); // 返回 97
```

#### 3. String.fromCharCode(numX,...)
静态方法，将Unicode编码转换为字符。

```javascript
console.log(String.fromCharCode(97, 98, 99)); // 返回 'abc'
```

### 二、查找类方法

#### 4. indexOf(searchvalue, fromindex)
返回子字符串首次出现的位置，未找到返回-1。

```javascript
var str = 'abcdeabcde';
console.log(str.indexOf('a'));     // 返回 0
console.log(str.indexOf('a', 3));  // 返回 5
console.log(str.indexOf('bc'));    // 返回 1
```

#### 5. lastIndexOf(searchvalue, fromindex)
从后向前搜索，返回子字符串最后出现的位置。

```javascript
var str = 'abcdeabcde';
console.log(str.lastIndexOf('a'));     // 返回 5
console.log(str.lastIndexOf('a', 3));  // 返回 0
console.log(str.lastIndexOf('bc'));    // 返回 6
```

#### 6. search(substr/regexp)
检索与子字符串或正则表达式匹配的位置。

```javascript
var str = 'abcDEF';
console.log(str.search('c'));      // 返回 2
console.log(str.search('d'));      // 返回 -1
console.log(str.search(/d/i));     // 返回 3
```

#### 7. match(substr/regexp)
检索匹配的子字符串。

```javascript
var str = '1a2b3c4d5e';
// 非全局匹配
console.log(str.match('b'));       // 返回 ["b", index: 3, input: "1a2b3c4d5e"]
// 全局匹配
console.log(str.match(/\d/g));     // 返回 ["1", "2", "3", "4", "5"]
```

### 三、截取类方法

#### 8. substring(start, end)
截取开始到结束位置之间的字符串（参数不能为负值）。

```javascript
var str = 'abcdefg';
console.log(str.substring(1, 4));  // 返回 'bcd'
console.log(str.substring(1));     // 返回 'bcdefg'
console.log(str.substring(-1));    // 返回 'abcdefg'（负值视为0）
```

#### 9. slice(start, end)
与substring类似，但参数可以为负值。

```javascript
var str = 'abcdefg';
console.log(str.slice(1, 4));      // 返回 'bcd'
console.log(str.slice(-3, -1));    // 返回 'ef'
console.log(str.slice(1, -1));     // 返回 'bcdef'
```

#### 10. substr(start, length)
从指定位置开始截取指定长度的字符串。

```javascript
var str = 'abcdefg';
console.log(str.substr(1, 3));     // 返回 'bcd'
console.log(str.substr(2));        // 返回 'cdefg'
console.log(str.substr(-2, 4));    // 返回 'fg'
```

### 四、替换与分割类方法

#### 11. replace(regexp/substr, replacement)
字符串替换操作。

```javascript
var str = 'abcdeabcde';
// 单次替换
console.log(str.replace('a', 'A')); // 返回 'Abcdeabcde'
// 全局替换
console.log(str.replace(/a/g, 'A')); // 返回 'AbcdeAbcde'
// 正则替换（忽略大小写）
console.log(str.replace(/a/gi, '$')); // 返回 '$bcde$bcde'
```

#### 12. split(separator, howmany)
将字符串分割为数组。

```javascript
var str = 'a|b|c|d|e';
console.log(str.split('|'));       // 返回 ["a", "b", "c", "d", "e"]
console.log(str.split('|', 3));    // 返回 ["a", "b", "c"]
// 使用正则分割
var str2 = 'a1b2c3d4e';
console.log(str2.split(/\d/));     // 返回 ["a", "b", "c", "d", "e"]
```

### 五、大小写转换类方法

#### 13. toLowerCase()
转换为小写字母。

```javascript
var str = 'JavaScript';
console.log(str.toLowerCase());    // 返回 'javascript'
```

#### 14. toUpperCase()
转换为大写字母。

```javascript
var str = 'JavaScript';
console.log(str.toUpperCase());    // 返回 'JAVASCRIPT'
```

## 常用技巧与最佳实践

### 1. 字符串连接
```javascript
// 使用模板字符串（推荐）
const name = '张三';
const greeting = `你好，${name}！`;

// 使用加号操作符
const fullName = '张' + '三';
```

### 2. 去除空格
```javascript
const str = '  Hello World  ';
console.log(str.trim());           // 'Hello World'
console.log(str.trimStart());      // 'Hello World  '
console.log(str.trimEnd());        // '  Hello World'
```

### 3. 判断字符串包含
```javascript
const str = 'Hello World';
console.log(str.includes('World'));   // true
console.log(str.startsWith('Hello')); // true
console.log(str.endsWith('World'));   // true
```

### 4. 重复字符串
```javascript
console.log('abc'.repeat(3));     // 'abcabcabc'
```

## 性能注意事项

1. **字符串拼接**：大量字符串拼接时，建议使用数组的join()方法替代加号操作符
2. **正则表达式**：重复使用的正则表达式建议预编译，避免重复创建
3. **字符串不变性**：字符串一旦创建不可更改，所有修改操作都会返回新字符串

## 总结

掌握字符串操作是JavaScript开发的基本功。建议结合实际项目多加练习，形成肌肉记忆。定期回顾本文内容，能够帮助巩固知识点，提高开发效率