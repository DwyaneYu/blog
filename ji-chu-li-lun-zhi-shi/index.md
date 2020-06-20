# 数据结构与算法

## 数组

### 什么是数组

一个存储元素的线性集合。JavaScript中的数组是一种特殊的对象，所以效率不如其他语言中的数组高

索引：数字索引在内部被转换为字符串类型，因为JavaScript中对象中的属性名必须是字符串

## 列表

### 什么是列表

列表是一组有序的数据。每个列表中的数据项称为元素。在 JavaScript 中，列表中的元素 可以是任意数据类型。列表中可以保存多少元素并没有事先限定，实际使用时元素的数量 受到程序内存的限制。

### 列表的实现

```text

function List() {
    this.listSize = 0;
    this.pos = 0;
    this.dataStore = []; // 初始化一个空数组来保存列表元素 
    this.clear = clear;
    this.find = find; 
    this.toString = toString; 
    this.insert = insert; 
    this.append = append; 
    this.remove = remove; 
    this.front = front;
    this.end = end;
    this.prev = prev;
    this.next = next;
    this.length = length;
    this.currPos = currPos;
    this.moveTo = moveTo;
    this.getElement = getElement;
    this.length = length;
    this.contains = contains;
}
function append(element) {
    this.dataStore[this.listSize++] = element;
}
function find(element) {
    for (var i = 0; i < this.dataStore.length; ++i) {
       if (this.dataStore[i] == element) {
          return i;
    } }
    return -1; 
}
function remove(element) {
    var foundAt = this.find(element); 
    if (foundAt > -1) {
       this.dataStore.splice(foundAt,1);
       --this.listSize;
       return true;
    }
    return false;
}
```

### 使用迭代器访问列表

使用迭代器可以不必关系数据的内部存储方式，以实现对列表的遍历。front\(\)、end\(\)、prev\(\)、next\(\)和currPos\(\)就实现了一个列表类的一个迭代器。

### 和使用数组索引的方式相比，使用迭代器的一些优点

* 访问列表元素时不必关心底层的数据结构
* 当为列表添加一个元素时，索引的值就不对了，此时只用更新列表而不用更新迭代器
* 可以使用不同类型的数据存储方式实现列表类，迭代器为访问列表里的元素提供了一种统一的方式 

## 栈

### 什么是栈

栈是一种高效的数据结构\(LIFO，后入先出\)，数据只能在栈顶添加或删除，然和不在栈顶的元素无法访问，为了得到栈底的元素必须拿掉上面的元素

### 对栈的操作

对栈的主要操作是将一个元素压入栈和将一个元素弹出栈，入栈使用push\(\)方法，出栈使用pop\(\)方法。peek\(\)方法只返回栈顶元素而不删除它。

### 栈的实现

```text
function Stack() {
   this.dataStore = [];
   this.top = 0;
   this.push = push;
   this.pop = pop;
   this.peek = peek;
   this.clear = clear;
   this.length = length;
}
function push(element) {
   this.dataStore[this.top++] = element;
}
function peek() {
   return this.dataStore[this.top-1];

}
function pop() {
   return this.dataStore[--this.top];
}
function clear() {
   this.top = 0;
}
function length() {
   return this.top;
}
```

### 使用栈的场景

#### 数制间的相互转换

```text
function mulBase(num, base) {
     var s = new Stack();
     while (num > 0){
        s.push(num % base);
        num = Math.floor(num /= base);
     };
     var converted = "";
     while (s.length() > 0) {
        converted += s.pop();
     }
     return converted;
  }
```

#### 回文

一个单词、短语或数字，从前往后写和从后往前写都是一样的。 比如，单词“dad”、“racecar”就是回文;

```text
    function isPalindrome(word) {
        var s = new Stack();
        for (var i = 0; i < word.length; ++i) {
           s.push(word[i]);
        }
        var rword = "";
        while (s.length() > 0) {
           rword += s.pop();
        }
        if (word == rword) {
           return true;
        } else {
           return false;
        }
      }
```

## 队列

队列是一种列表，只能在队尾插入元素，队首删除元素。队列用于存储按顺序排列的的数据，先进先出。

### 对队列的操作

队列的两种主要操作是:向队列中插入新元素和删除队列中的元素。插入操作也叫做入 队，删除操作也叫做出队。队列的另外一项重要操作是读取队头的元素。这个操作叫做 peek\(\)。该操作返回队头元 素，但不把它从队列中删除。除了读取队头元素，我们还想知道队列中存储了多少元素， 可以使用 length 属性满足该需求;要想清空队列中的所有元素，可以使用 clear\(\) 方法来 实现。

### 队列的实现

```text
 function Queue() {
  this.dataStore = [];
  this.enqueue = enqueue; // 向队尾添加一个元素
  this.dequeue = dequeue; // 方法删除队首的元素
  this.front = front; // 读取队首元素
  this.back = back; // 读取队尾元素
  this.toString = toString; // 
  this.empty = empty;
 } 
```

### 使用队列的场景

#### 方块舞的舞伴分配问题

#### 数据排序

#### 优先队列

## 链表

### 数组的缺点

* 在很多语言中，数组的长度是固定的
* 添加和删除需要将其他元素进行平移
* JavaScript中的数据是一种特殊的对象，相较于其他语言效率较低

### 什么是链表

链表是由一组节点组成的集合，每个节点都使用一个对象的引用指向它的后继，指向另一 个节点的引用叫做链。数组元素靠它们的位置进行引用，链表元素则是靠相互之间的关系进行引用

### 链表的实现

```text
function Node(element) {
  this.element = element;
  this.next = null;
}
function LList() {
  this.head = new Node("head"); 
  this.find = find;
  this.insert = insert; 
  this.display = display; 
  this.findPrevious = findPrevious; 
  this.remove = remove;
}
function find(item) {
  var currNode = this.head;
  while (currNode.element != item) {
     currNode = currNode.next;
  }
  return currNode;
}
function insert(newElement, item) { 
  var newNode = new Node(newElement); 
  var current = this.find(item); 
  newNode.next = current.next; 
  current.next = newNode;
}
function display() {
  var currNode = this.head;
  while (!(currNode.next == null)) {
     print(currNode.next.element);
     currNode = currNode.next;
  }
}
function findPrevious(item) {
  var currNode = this.head;
  while (!(currNode.next == null) && (currNode.next.element != item)) {
    currNode = currNode.next;
  }
  return currNode;
}
function remove(item) {
  var prevNode = this.findPrevious(item);
  if (!(prevNode.next == null)) {
      prevNode.next = prevNode.next.next;
  }
}
```

## 字典

## 散列

## 集合

## 二叉树与二叉查找树



