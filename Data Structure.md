# Data Structure

## Array

使用 Python 的 List（列表）实现：

```
class Array:
    def __init__(self, x):
        self.data = list(x)

array1 = Array([1,2,3])
```

- size() —— 数组元素的个数
  
  ```
  def size(self):
      return len(self.data)
  ```

- is_empty() —— 判断数组是否为空
  
  ```
  def is_empty(self):
      return True if not self.data else False
      # other ways: 1. self.data == [] ; 2. len(self.data) == 0
  ```

- at(index) —— 返回对应索引的元素，若越界则报错
  
  ```
  def at(self,index):
      if index >= len(self.data):
          raise IndexError("Array index out of range.")
      return self.data[index]
  ```

- push(item) —— 在数组末尾插入元素
  
  ```
  def push(self,item):
      self.data.append(item)
  ```

- insert(index, item) —— 在指定索引中插入元素，并把后面的元素依次后移
  
  ```
  def insert(self, index, item):
      self.data.insert(index, item)
  ```

- pop() —— 删除在数组末端的元素，并返回其值
  
  ```
  def pop(self):
      return self.data.pop()
  ```

- delete(index) —— 删除指定索引的元素，并把后面的元素依次前移
  
  ```
  def delete(self,index):
      self.data.pop(index)
  ```

- remove(item) —— 删除指定值的元素，并返回其索引（即使有多个元素）
  
  ```
  def remove(self, item):
      index_list = []
      item_count = self.data.count(item)
      for i in range(item_count):
          index_list.append(self.data.index(item))
          self.data.remove(item)
      return index_list
  ```

- find(item) —— 寻找指定值的元素并返回其中第一个出现的元素其索引，若未找到则返回 -1
  
  ```
  def find(self, item):
      if item in self.data:
          return self.data.index(item)
      else:
          return -1
  ```

- reverse() —— 翻转数组
  
  ```
  def reverse(self):
      temp = []
      size = len(self.data)
      for i in range(size):
          temp.append(self.data[size-1-i])
      self.data = temp
  ```

- sort() —— 数组排序（升序） O(nlogn)
  
  ```
  def sort(self):
      return self.data.sort()    # self.data.sort(reverse = True) 为降序 
  ```

时间复杂度：

- 在数组的**末尾插入/删除**、**更新**、**获取**某个位置的元素，都是 O(1) 的时间复杂度
- 在数组的任何其它地方**插入/删除**元素，都是 O(n) 的时间复杂度

空间复杂度：O(n)

## Linked List

单向链表:

```
class listNode:        # 链表中的结点
    def __init__(self, x):
        self.val = x
        self.next = None

class LinkedList:        # 链表类
    def __init__(self):
        self.head = None

l1 = LinkedList()
l1.add(1)
l1.add(2)
```

- size() —— 返回链表中数据元素的个数/链表长度
  
  ```
  def size(self):
      size = 0
      head = self.head
      while head:
          size += 1
          head = head.next
      return size
  ```

- empty() —— 若链表为空则返回一个布尔值 true
  
  ```
  def empty(self):
      return True if self.head else False
  ```

- value_at(index) —— 返回第 n 个元素的值（从0开始计算），若索引超过链表长度则报错
  
  ```
  def value_at(self, index):
      if not self.head:
          raise IndexError("Index out of range.")
      head = self.head
      while index > 0:
          if not head:
              raise IndexError("Index out of range.")
          head = head.next
          index -= 1
      return head.val
  ```

- add(value) —— 添加元素到链表的首部
  
  ```
  def add(self, value):
      new_node = listNode(value)
      new_node.next = self.head
      self.head = new_node
  ```

- pop_front() —— 删除首部元素并返回其值，若链表为空则报错
  
  ```
  def pop_front(self):
      if not self.head:
          raise IndexError("Pop from empty list")
      value = self.head.val
      self.head = self.head.next
      return value
  ```

- append(value) —— 添加元素到链表的尾部
  
  ```
  def append(self, value):
      new_node = listNode(value)
      if not self.head:
          self.head = new_node
          return
      head = self.head
      while head.next:
          head = head.next
      head.next = new_node
  ```

- pop_back() —— 删除尾部元素并返回其值，若链表为空则报错
  
  ```
  def pop_back(self):
      if not self.head:
          raise IndexError("Pop from empty list")
      if not self.head.next:
          value = self.head.val
          self.head = None
          return value
      head = self.head
      while head.next.next:
            head = head.next
      value = head.next.val
      head.next = None
      return value
  ```

- front() —— 返回首部元素的值，若链表为空则报错
  
  ```
  def front(self):
      if not self.head:
          raise ValueError("Linked list is empty")
      return self.head.val
  ```

- back() —— 返回尾部元素的值，若链表为空则报错
  
  ```
  def back(self):
      if not self.head:
          raise ValueError("Linked list is empty")
      head = self.head
      while head.next:
            head = head.next
      return head.val
  ```

- insert(index, value) —— 插入值到指定的索引，若索引超出链表长度则报错
  
  ```
  def insert(self, index, value):
      if not self.head:
          raise IndexError("Index out of range")
      head = self.head
      new_node = listNode(value)
      if index == 0:
          new_node.next = head
          self.head = new_node
          return
      while index - 1 > 0:
          head = head.next
          if not head:
              raise IndexError("Index out of range")
          index -= 1
      temp = head.next
      head.next = new_node
      new_node.next = temp
  ```

- erase(index) —— 删除指定索引的节点，若索引超出链表长度则报错
  
  ```
  def erase(self, index):
      if not self.head:
          raise IndexError("Index out of range")
      head = self.head
      if index == 0:
          self.head = head.next
      while index - 1 > 0:
          index -= 1
          head = head.next
          if not head:
              raise IndexError("Index out of range")
      temp = head.next
      head.next = temp.next
  ```

- reverse() —— 逆序链表
  
  ```
  def reverse(self):
      prev = None
      head = self.head
      while head:
          temp = head.next
          head.next = prev
          prev = head
          head = temp
      self.head = prev
  ```

- remove(value) —— 删除链表中指定值的第一个元素
  
  ```
  def remove(self,value):
      if not self.head:
          return
      head = self.head
      if head.val == value:
          self.head = head.next
          return
      while head.next:
          if head.next.val == value:
              temp = head.next.next
              head.next = temp
              return
          head = head.next
  ```
  
  时间复杂度：
  
     - 在链表的**首部插入/移除结点**、获得**链表首部的值**，都是O(1)时间复杂度
     - 获取/移除/插入任一结点、尾部结点，都是O(n)时间复杂度

## Stack

使用数组实现栈（使用 Python 的 list 实现）：

```
class Stack:
    def __init__(self):
        self.data = []

s1 = Stack()
s1.push(1)
s1.push(2)
```

- push(item) —— 向栈顶添加元素
  
  ```
  def push(self, item):
      self.data.append(item)
  ```

- pop() —— 弹出栈顶的元素，若栈为空则报错
  
  ```
  def pop(self):
      if self.data:
          return self.data.pop()
      else:
          raise PopError("Pop from empty stack.")
  `
  ```

- peek() —— 返回栈顶的元素（但是不弹出），若栈为空则报错
  
  ```
  def peek(self):
      if self.data:
          return self.data[-1]
      else:
          raise IndexError("Stack is empty.")
  ```

- size() —— 返回栈的长度
  
  ```
  def size(self):
      return len(self.data)
  ```

- is_empty() —— 判断栈是否为空
  
  ```
  def is_empty(self):
      return self.data == []
  ```

栈满足**后进先出 LIFO**的原则，时间复杂度：压栈、出栈都是 O(1)

## Queue

**单链队列**，使用 Python 中的列表 List 实现：

- enqueue(item) —— 将一个元素入队（在队尾添加元素）
  
  ```
  def enqueue(self, item):
      self.data.append(item)
  ```

- dequeue() —— 将队首的元素出队，若队列为空则报错
  
  ```
  def dequeue(self):
      if self.data:
          return self.data.pop(0)
      else:
          raise DequeueError("Queue is empty.")
  ```

- size() —— 返回队列长度
  
  ```
  def size(self):
      return len(self.data)
  ```

- is_empty() —— 判断队列是否为空
  
  ```
  def is_empty(self):
      return self.data == []
  ```
