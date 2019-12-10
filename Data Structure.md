# Data Structure

## Arrays

使用 Python 的 List（列表）实现：

```
array_a = []
```

- size() —— 数组元素的个数
  
  ```
  return len(array_a)
  ```

- is_empty() —— 判断数组是否为空
  
  ```
  return True if not array_a else False
  # other ways: 1. array_a == [] ; 2. len(array_a) == 0
  ```

- at(index) —— 返回对应索引的元素，若越界则报错
  
  ```
  return array_a[index]
  ```

- push(item) —— 在数组末尾插入元素
  
  ```
  array_a.append(item)
  return array_a
  ```

- insert(index, item) —— 在指定索引中插入元素，并把后面的元素依次后移
  
  ```
  array_a.insert(index, item)
  return array_a
  ```

- pop() —— 删除在数组末端的元素，并返回其值
  
  ```
  return array_a.pop()
  ```

- delete(index) —— 删除指定索引的元素，并把后面的元素依次前移
  
  ```
  array_a.pop(index)
  return array_a
  ```

- remove(item) —— 删除指定值的元素，并返回其索引（即使有多个元素）
  
  ```
  index_list = []
  item_count = array_a.count(item)
  for i in range(item_count):
      index_list.append(array_a.index(item))
      array_a.remove(item)
  return index_list
  ```

- find(item) —— 寻找指定值的元素并返回其中第一个出现的元素其索引，若未找到则返回 -1
  
  ```
  if item in array_a:
    return array_a.index(item)
  else:
    return -1
  ```

- get_slice(start, end) —— 获得数组中的片段，包含 start 不包含 end
  
  ```
  return array_a[start:end]
  ```

- reverse() —— 翻转数组
  
  ```
  temp = []
  size = len(array_a)
  for i in range(size):
      temp.append(array_a[size-1-i])
  return temp
  ```

- sort() —— 数组排序 O(nlogn)
  
  ```
  return array_a.sort()    # array_a.sort(reverse = True) 为降序 
  ```

时间复杂度：

- 在数组的**末尾插入/删除**、**更新**、**获取**某个位置的元素，都是 O(1) 的时间复杂度
- 在数组的任何其它地方**插入/删除**元素，都是 O(n) 的时间复杂度

空间复杂度：O(n)
