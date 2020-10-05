---
title: Ucloud面经整理
copyright: false
tags: [Interview, hexo]
categories: 面经
---
## 为什么学前端 

自己很喜欢前端，前端做出来的东西可以马上展现出来，可以带来最直接的成就感

社区比较开放，有很多新的设计思想

对视觉设计比较感兴趣，熟练使用Adobe软件，熟练使用Photoshop、Adobe XD

## 数组有哪些原生方法

### 1. 赋值方法

这些方法直接修改数组自身

#### push和pop

`pop()`方法删除数组最后一个元素，返回被删除的元素

`push()`方法将一个或多个元素添加到数组的末尾，并返回该数组的新长度

#### shift 和 unshift

`shift()` 方法从数组中删除**第一个**元素，并返回该元素的值。此方法更改数组的长度。

`unshift()` 方法将一个或多个元素添加到数组的**开头**，并返回该数组的**新长度**(该方法修改原有数组)

#### splice

**`splice()`** 方法通过删除或替换现有元素或者原地添加新的元素来修改数组,并以数组形式返回**被修改的内容**。此方法会改变原数组。

```javascript
Array.splice(index , howMany[, element1[, ...[, elementN]]]);
```

参数：

`index` 规定从何处添加/删除元素。

`howmany` 规定应该删除多少元素。

`elements` 规定要添加到数组的新元素，从 index 所指的下标处开始插入。

#### reverse

`reverse()` 方法颠倒数组中元素的顺序，并返回逆序后的数组。该方法会改变原数组。

#### sort

`sort()` 方法用原地算法对数组的元素进行排序，并返回数组。默认排序顺序是在将元素转换为字符串，然后比较它们的UTF-16代码单元值序列时构建的

```javascript
arr.sort([compareFunction])
```

`compareFunction`可选

用来指定按某种顺序进行排列的函数。如果省略，元素按照转换为的字符串的各个字符的Unicode位点进行排序。

`firstEl` 第一个用于比较的元素。

`secondEl` 第二个用于比较的元素。

```javascript
arr.sort(function (x, y) {
    if (x < y) {
        return -1;
    }
    if (x > y) {
        return 1;
    }
    return 0;
});
console.log(arr); // [1, 2, 10, 20]
```

也可以简写为

```javascript
arr.sort((a, b) => a - b); 
```

最后友情提示，`sort()`方法会直接对`Array`进行修改，它返回的结果仍是当前`Array`

### 2. 访问方法

这些方法只是返回相应的结果，而不会修改数组本身

#### concat

```javascript
Array.concat(value1, value2, ..., valueN); 
```

链接2个或多个数组，并返回合并后的数组

#### join

```javascript
string = Array.join(separator);   
```

把数组中的所有元素放入一个字符串。其中，元素之间是通过指定的分隔符进行分隔的。

默认的分隔符是逗号(,)，返回值是合并后字符串。

Array.join()方法，实际上是String.splite()的逆向操作。

#### slice

```javascript
Array.slice(begin[, end]);
```

数组中返回选定的元素

#### toString

转化为字符串

#### indexOf

`indexOf()`方法返回在数组中可以找到一个给定元素的第一个索引，如果不存在，则返回-1。

```javascript
arr.indexOf(searchElement[, fromIndex])
```

`searchElement`要查找的元素

### 3. 迭代方法

#### forEach

`forEach()` 方法对数组的每个元素执行一次给定的函数。

```javascript
Array.forEach(callback[, thisArg]);    // 从头到尾遍历一次数组，并为数组中的每个元素，调用指定的函数
```

参数：
`callback`：遍历数组时调用的函数
`thisArg`：指定 callback 的作用域

另外，callback会调用三个参数：
`value`：数组元素
`index`：数组索引
`array`：数组本身

```javascript
const array1 = ['a', 'b', 'c'];

array1.forEach(element => console.log(element));

// expected output: "a"
// expected output: "b"
// expected output: "c"
```

### map

`map()` 方法创建一个新数组，其结果是该数组中的每个元素是调用一次提供的函数后的返回值。

```javascript
Array.map(callback[, thisArg]);    // 遍历数组元素，调用指定函数，并以数组返回所有结果
```

参数：

`callback`：遍历数组时调用的函数
`thisObject`：指定 callback 的作用域

```javascript
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
```

### filter()

`filter()` 方法创建一个新数组, 其包含通过所提供函数实现的测试的所有元素。 

```javascript
Array.filter(callback[, thisObject]);    // 遍历数组调用方法，满足条件(返回true)的元素，将被添加到返回值的数组中
```

参数：

`callback`：遍历数组时调用的函数

`thisObject` ：指定 callback 的作用域

```javascript
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

### reduce 和 reduceRight

```javascript
Array.reduce(callback[, initialValue]); // 使用指定的方法将数组元素进行组合，按索引从低到高（从左到右）
```

```javascript
Array.reduceRight(callback[, initialValue]);    // 使用指定的方法将数组元素进行组合，按索引从高到低（从右到左）
```

参数：

`callback`：遍历数组时调用的函数

`initialValue`：第一个次调用callback时传入的previousValue

另外，callback会调用四个参数：

`previousValue`：到目前为止的操作累积结果

`currentValue`：数组元素

`index`：数组索引

`array`：数组本身

```javascript
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15
```

## 数组的map和forEach的区别 

MDN 上对 Map 和 ForEach 的定义：

- `forEach()`: 针对每一个元素执行提供的函数
- `map()`: 创建一个新的数组，其中每一个元素由调用数组中的每一个元素执行提供的函数得来

`forEach()`方法不会返回执行结果，而是`undefined`。也就是说，`forEach()`会修改原来的数组。而`map()`方法会得到一个新的数组并返回。

**示例：**

```javascript
let arr = [1, 2, 3, 4, 5];
```

#### forEach

`forEach`是不会返回有意义的值的，我们在回调函数中直接修改`arr`的值

```javascript
arr.forEach((num, index) => {
    return (arr[index] = num * 2);
});
// arr = [2,4,6,8,10]
```

#### Map

```javascript
let doubled = arr.map(num => {
    return num * 2;
});
// doubled = [2,4,6,8,10]
```

#### 对比

`forEach`适合于你并不打算改变数据的时候，而只是想用数据做一些事情 – 比如存入数据库或则打印出来。

```javascript
let arr = ["a", "b", "c", "d"];
arr.forEach(letter => {
    console.log(letter);
});
// a
// b
// c
// d
```

`map()`适用于你要改变数据值的时候。不仅仅在于它更快，而且返回一个新的数组。这样的优点在于你可以使用复合(composition)(map(), filter(), reduce()等组合使用)来玩出更多的花样。

```javascript
let arr = [1, 2, 3, 4, 5];
let arr2 = arr.map(num => num * 2).filter(num => num > 5);
// arr2 = [6, 8, 10]
```

#### 核心要点

- 能用`forEach()`做到的，`map()`同样可以。反过来也是如此。
- `map()`会分配内存空间存储新数组并返回，`forEach()`不会返回数据。
- `forEach()`允许`callback`更改原始数组的元素。`map()`返回新的数组。

## 数组去重实现 

### 利用ES6 Set去重（ES6中最常用的方法）

```javascript
function unique(arr) {
    return Array.from(new Set(arr))
}
```

简化为最简单的方式

```javascript
[...new Set(arr)]
```

### 利用for嵌套for，然后splice去重（ES5中最常用）

双层循环，外层循环元素，内层循环时比较值。值相同时，则删除这个值

```javascript
function unique(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = i + 1; j < arr.length; j++) {
            if (arr[i] == arr[j]) {
                arr.splice(j,1);
                j --;
            }
        }
    }
    return arr;
}
```

### 利用indexOf()去重

新建一个空的结果数组，for循环原数组，判断结果数组是否存在当前元素，如果有相同的值则跳过，不相同则push进数组

```javascript
function unique(arr) {
    if (!Array.isArray(arr)) {
        console.log('type error!')
        return
    }
    var array = []
    for (let i = 0; i < arr.length; i++) {
        console.log(arr[i])
        if (array.indexOf(arr[i]) === -1) {
            array.push(arr[i])
        }
    }
    return array;
}
```

### 利用sort()

```javascript
function unique() {
    if (!Array.isArray(arr)) {
        console.log('type error!')
        return;
    }
    arr = arr.sort()
    var array = [arr[0]]
    for (var i = 1; i < arr.length; i++) {
        if(arr[i]!==arr[i-1]) {
            array.push(arr[i])
        }
    }
    return array
}
```

## 闭包

### 1. 相关概念

**变量作用域**：全局变量拥有全局作用域，在js代码的任何地方都可见。在函数内部声明的变量只在该函数体内可见，被称为局部变量。

**函数作用域**：在函数内声明的所有变量在该函数体内始终是可见的。

**作用域链**：作用域链是一个对象。作用域链中定义了该作用域内的变量，它保证了该作用域中变量、函数的有序访问。

**作用域链的创建**：定义一个函数时，会保存一个作用域链。调用一个函数时，会创建一个新的对象来存储其局部变量，并将该对象添加至保存的作用域链上，同时创建一个新的更长的表示函数调用作用域的链。对于嵌套函数来说，每调用一次外部函数，都会创建一个新的作用域链，所以每次调用外部函数，虽然其内部代码相同，但是调用的作用域链是不同的。

**垃圾回收机制**：js具有自动垃圾回收机制，会定期把不再使用的变量销毁，释放其占用的内存。（只会销毁局部变量，全局变量的生命周期只有在页面或浏览器关闭时才会结束）

### 2. 闭包的概念

#### 定义：

> 闭包是指有权访问另一个函数作用域中的变量的函数。——《js高程》
> 闭包是函数和声明该函数的词法环境的组合。——《MDN》

![img](https://user-gold-cdn.xitu.io/2018/7/20/164b3513e183f890?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

#### 网络上的解释:

> **闭包**就是指当前函数可以记住并访问所在的词法作用域，并且保持着对词法作用域的引用，即使函数是在当前作用域之外执行，就会产生闭包
> 一言以蔽之：一个持有外部环境变量的函数就是闭包。
>
> 闭包就是能够读取其他函数内部变量的函数

理解闭包通常有着以下几个关键点：
1.函数
2.自由变量
3.环境

#### 变量的作用域

> **静态作用域**又叫做词法作用域，采用词法作用域的变量叫**词法变量**。词法变量有一个在编译时静态确定的作用域。词法变量的作用域可以是一个函数或一段代码，该变量在这段代码区域内可见（visibility）；在这段区域以外该变量不可见（或无法访问）。词法作用域里，取变量的值时，会检查函数定义时的文本环境，捕捉函数定义时对该变量的绑定。

大多数现在程序设计语言都是采用静态作用域规则，如C/C++、C#、Python、Java、JavaScript……

变量的作用域无非就是两种：全局变量和局部变量

Javascript语言的特殊之处，就在于函数内部可以直接读取全局变量。

```javascript
var n = 999;
function f1() {
    console.log(n)
}
f1()   /// 999
```

另一方面，在函数外部自然无法读取函数内的局部变量。

```javascript
function f1() {
    var n = 999;
}
console.log(n)   // error
```

这里有一个地方需要注意，函数内部声明变量的时候，一定要使用var命令。如果不用的话，你实际上声明了一个全局变量！

```javascript
function f1(){
　　n=999;
}
f1();
alert(n); // 999
```

### 3. 闭包的原理

函数的执行依赖于函数定义时的作用域链，即js函数执行时用的作用域链是该函数定义时创建的作用域链。大多数时候定义函数时的作用域链在函数执行时仍然有效。但是如果定义函数时的作用域链和执行函数时的作用域链不同时，就会出现问题。即当一个函数中嵌套了另一个函数，并把嵌套的函数对象作为返回值返回时，就会产生这种情况。

#### 定义函数的作用域链和执行时相同:

```javascript
var myName = 'my name is window'
function checkScope() {
    var myName = 'my name is local';
    function fn() {
        return myName
    }
    return fn()
}
checkScope()   // my name is local
```

#### 外部函数把嵌套函数作为返回值返回时

```javascript
var myName = 'my name is window'
function checkScope() {
    var myName = 'my name is local';
    function fn() {
        return myName
    }
    return fn
}
checkScope()()   // my name is local
```

第二个，可以看到当外部函数把嵌套函数作为返回值返回时，其执行结果仍然是局部变量的值，而不是全局变量的值。这就是因为函数执行时用到的作用域链，其实是函数定义时创建的。不管该函数在何时何地执行，它通过作用域链最先找到的变量就是相同外部函数中定义的变量。而闭包正是利用这种特性实现的：闭包可以捕捉到局部变量或参数，并一直保存下来，使其不会被当成垃圾回收

### 4. 闭包和垃圾回收的关系

调用函数时，会创建一个对象来保存其局部变量，并且把这个对象添加到作用域链上。当函数返回时（即执行完成了），就会从作用域链中把绑定局部变量的对象删除，这个对象就会被当作垃圾回收。但是如果定义了嵌套函数，那么嵌套函数也会有自己相应的作用域链，它与外部函数一样，把其局部变量保存到一个对象上，如果嵌套函数是作为返回值返回的或者存储在某处的属性里，那么就会有一个外部引用指向这个嵌套函数，那么外部函数就不会被当作垃圾回收，它在作用域链中绑定局部变量的对象也不会被回收。

### 5. 闭包的作用

JS规定在一个函数作用域内，程序执行完以后变量就会被销毁，这样可节省内存；使用闭包时，按照作用域链的特点，闭包（函数）外面的变量不会被销毁，因为函数会一直被调用，所以一直存在，如果闭包使用过多会造成内存销毁

#### 作用

- 实现私有成员
- 保护命名空间
- 避免污染全局变量
- 可以使变量长期驻留在内存中

#### 缺点

- 导致变量不会被垃圾回收机制回收，造成内存消耗
- 不恰当的使用闭包可能会造成内存泄露的问题

