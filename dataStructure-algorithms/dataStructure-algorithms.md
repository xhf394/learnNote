# 数据和算法

## Linked List



#### Linked List 概述

linked list： 当数据的结构为Linked List 的时候，每一个收据与前面一个相连，与后面一个也相连。在数据结构中会包含一个头（head)和一个尾（tail）,头和尾可以不断的添加和减少。

linked list 可以实现的几个作用：

1. head 和 tail可以不断的添加和减少来加入数据；
2. 进行查询。查询linked list 中是否包含某个数据。

linked list 数据结构：

​	linked list 中的每一个node由JS中的 Object 对象组成，每个对象中必含的3个属性，分别为： value: 这个对象的值； next: 所相连的下一个对象；prev: 所相连的上一个对象。

1. LinkedList Function: 只包含：head 和 tail；

   ```javascript
   function LinkedList () {
       this.head = null;
       this.tail = null;
   }
   ```

2. Node Function: 包含 value, next, prev.

   ```javascript
   function Node (value, next, prev) {
       this.value = value;
       this.next = next;
       this.prev = prev;
   }
   ```


![1545017740602](C:\Users\Xiaozhou Huangfu\AppData\Roaming\Typora\typora-user-images\1545017740602.png)



#### How to use Linked List

##### addToHead Method

定义一个addToHead 方法，将这个方法加入prototype之中：

```javascript
LinkedList.prototype.addToHead = function (value) {
    //首先创建一个新node，值为输入值，后为原head,前为空
    var newNode = new Node(value, this.head, null);
    //判定这个list原本是否有值或为空
    //如为真，重新指向原head的前值
    if(this.head) this.head.prev = newNode;
    //若为假，原值为空，先指定tail;
    else this.tail = newNode;
    //无论原值是否为真，都重新指向同一head;
    this.head = newNode;
}
```

保证： 1. 更新了head,

2. 更新原head;
3. 确保如果为空，tail也重新指向

##### addToTail Method

定义一个addToTail的方法，并加入prototype,方法于前一个相同：

```javascript
LinkedList.prototype.addToTail = function (value) {
	var newNode = new Node(value, null, this.tail);
	if(this.tail) this.tail.next = newNode;
	else this.head = newNode;
	this.tail = newNode;
}
```



##### removeHead Method

定义一个removeHead Method, 加入到prototype当中，实现效果为移走head node,并返回head node 的值

```javascript
/**
 * removeHead() returns value of Linkedlist head node;
 * It will remove current head node;
 * @class LinkedList;
 * @return {value} value of head; 
 */
LinkedList.prototype.search = function () {
    if(!this.head) {
        return null;
    }
    var val = this.head.value;
    this.head = this.head.next;
    if(this.head) {
        this.head.prev = null;
    }
    else {
        this.tail = null;
    }
    return val;
}
```



##### removeTail Method

定义一个removeTail 方法，加入到prototype中，实现效果为：移走现有的tail node， 并返回tail node的值

```javascript
LinkedList.prototype.removeTail = function () {
    if(!this.tail) {
        return null;
    }
    var val = this.tail.value;
    this.tail = this.tail.prev;
    if(this.tail) {
        this.tail.next = null;
    }
    else {
        this.head = null;
    }
    return val;
}
```

## Binary Search Trees

### Recursion

binary search 的思想基于递归的方法。

递归函数的使用：

```javascript
function factorial(num) {
    //base case
    if(num === 1) {
        return num;
    }
    //recursive part
    else {
        return num * factorial(num - 1);
    }
}
```



### Binary Search Tree 含有的几种必备方法

Binary Search Tree (BST) 是一种树形的数据结构。一般包含几种必备的数据处理方式，包括：添加，查询，排序（按从小到大的顺序，先parent node 再child node, 先children nodes 再parent nodes），获取最小值和最大值。在每一种方法中基本都可以用到recursion来完成数据处理。



#### BST的标准结构

BST的标准结构为图下的树形，每一个分支上都含有一个父级node和两个子级node，左边小，右边大。

![1549333818270](C:\Users\huangx\AppData\Roaming\Typora\typora-user-images\1549333818270.png)

When initiates BST constructor, we need to include these three nodes as follow:

​	

```javascript
function BST(value) {
    this.value = value;
    this.left = null;
    this.right = null;
}
```



#### 添加功能

要将



-++