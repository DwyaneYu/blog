# 数据结构与算法

## 数组

> 一个存储元素的线性集合。JavaScript中的数组是一种特殊的对象，所以效率不如其他语言中的数组高

索引：数字索引在内部被转换为字符串类型，因为JavaScript中对象中的属性名必须是字符串

## 列表

> 列表中使用的元素不是太多，同时不需要在一个很长的列表中查找元素或对其进行排序

### 实现列表类

> function List\(\){
>
>   this.listSize = 0; // 列表元素个数

> this.pos = 0;  // 列表当前位置
>
>   this.dataStore = \[\]; // 初始化一个空数组来保存列表数据
>
>   this.clear = clear; // 清空列表所有数据
>
>   this.find = find; // 在列表中查找某一元素
>
>   this.toString = toString; //返回列表的字符串形式
>
>   this.insert = insert; // 在现有元素后插入新元素
>
>   this.append = append; //在列表的末尾添加新元素
>
>   this.remove = remove; // 从列表中删除元素
>
>   this.front = front;  // 将列表的当前位置移动到第一个元素 
>
>   this.end = end; // 将当前列表位置移动到最后一个元素
>
>   this.prev = prev; // 将当前位置后移一位
>
>   this.next = next; // 将当前位置前移一位
>
>   this.length = length; // 返回当前列表元素个数
>
>   this.currPos = currPos; 
>
>   this.moveTo = moveTo; 
>
>   this.getElement = getElement; 
>
>   this.contains = contains;

> }

### 使用迭代器访问列表

使用迭代器可以不必关系数据的内部存储方式，以实现对列表的遍历。front\(\)、end\(\)、prev\(\)、next\(\)和currPos\(\)就实现了一个列表类的一个迭代器。

### 和使用数组索引的方式相比，使用迭代器的一些优点

* 访问列表元素时不必关心底层的数据结构
* 当为列表添加一个元素时，索引的值就不对了，此时只用更新列表而不用更新迭代器
* 可以使用不同类型的数据存储方式实现列表类，迭代器为访问列表里的元素提供了一种统一的方式 

## 栈

> 栈是一种高效的数据结构\(LIFO，后入先出\)，数据只能在栈顶添加或删除，然和不在栈顶的元素无法访问，为了得到栈底的元素必须拿掉上面的元素

### 对栈的操作

对栈的主要操作是将一个元素压入栈和将一个元素弹出栈，入栈使用push\(\)方法，出栈使用pop\(\)方法。peek\(\)方法只返回栈顶元素而不删除它。

### 栈的实现

> function Stack\(\) {
>
>   this.dataStore = \[\];
>
>   this.top = 0;
>
>   this.push = push;
>
>   this.pop = pop;
>
>   this.peek = peek;
>
>   this.clear = clear;
>
>   this.length = length;

> }

### 使用Stack的场景

#### 数制间的相互转换

> function mulBase\(num, base\) {
>
>   var s = new Stack\(\);      
>
>   while\(num !== 0\){
>
>     s.push\(num%base\) ;
>
>     num = Math.floor\(num/base\)
>
>   }
>
>   var converted = "";
>
>   while\(s.length\(\) &gt; 0\){
>
>     converted += s.pop\(\)
>
>   }
>
>   return converted;
>
> }

#### 回文

一个单词、短语或数字，从前往后写和从后往前写都是一样的。 比如，单词“dad”、“racecar”就是回文;

> function isPalindrome\(word\){
>
>   var s = new Stack\(\);
>
>   for\(var i=0;i&lt; word.length;i++\){ 
>
>     s.push\(word\[i\]\)
>
>   }
>
>  var rword = "";
>
>   while\(s.length\(\) &gt; 0\){
>
>     rword += s.pop\(\);
>
>   }
>
>  if\(rword === word\){ 
>
>     return true
>
>   } else {
>
>     return false;
>
>   }

> }

#### 模拟递归

#### 队列

#### 链表

#### 字典

#### 散列

#### 集合

#### 二叉树与二叉查找树



