# Algorithms

## 算法复杂度分析
待完成

## Sorting
#### 选择排序 Selection Sort
- 思想：最开始，找到数组中最小的元素，将其和数组第一个元素交换位置；然后在剩下的元素中找到最小的元素，将其和数组的第二个元素交换位置，如此往复。。。简单地说，就是不断在剩余元素中选取最小者放到剩余元素的首位。
- 复杂度：大约会进行N次交换以及N^2次比较
- 特点：
    - 运行时间和输入无关；不管初始输入是有序数组还是随机排列的数组，排序时间都是一样长的
    - 数据的移动最少，只需N次移动

Python版：
```py
def select_sort(lst):
    if not lst:
        return []
    for i in range(len(lst) - 1):
        smallest = i
        for j in range(i, len(lst)):
            if lst[j] < lst[smallest]:
                smallest = j
            lst[i], lst[smallest] = lst[smallest], lst[i]
    return lst
```

Golang版：
```go
func SelectionSort(lst []int) []int {
    if len(lst) == 0 {
        return lst
    }
    for i := 0; i < len(lst); i++ {
        smallest := i
        for j := i + 1; j < len(lst); j++ {
            if lst[j] < lst[smallest] {
                smallest = j
            }
        }
        lst[i], lst[smallest] = lst[smallest], lst[i]
    }
    return lst
}
```

#### 插入排序 Insertion Sort
- 思想：指针从数组的左边到右边，指针的左边总是排好序的，每次都将指针右边的第一个元素插入到指针左边已经排好序的数组中（方法是依次和前面的元素比较直到位置固定），然后将指针向右移动，当指针到达整个数组最右端时，说明排序已经完成
- 时间复杂度：
    - 比较：O(N^2)；最好情况：O(N-1)
    - 交换：O(N^2)；最好情况：0次
- 优点：如果一个数组中的元素都是有序的，使用插入排序能够在线性时间内完成排序，不需要对元素进行移动。对于部分有序的数组和小规模数组很有效

Python版：
```py
def insert_sort(lst):
    if not lst:
        return []
    for i in range(1, len(lst)):
        j = i
        while j > 0 and lst[j] < lst[j-1]:
            lst[j-1], lst[j] = lst[j], lst[j-1]
            j -= 1
    return lst
```

Golang版：
```go
func InsertionSort(lst []int) []int {
    if len(lst) == 0 {
            return lst
    }
    for i := 1; i < len(lst); i++ {
        for j := i; j > 0 && lst[j] < lst[j-1]; j-- {
            lst[j-1], lst[j] = lst[j], lst[j-1]
        }
    }
    return lst
}
```

#### 希尔排序 Shell Sort
- 简介：这是一个比前两种排序算法要复杂一些的算法，它对于很多随机数组都非常高效，对于大型数组的表现也非常好。它的运行时间达不到平方级别。对其性质的数学论证很复杂，至今无法准确描述其性能，无法证明对其最好的递增序列，不知道其所需要的平均比较次数
- 思想：首先介绍**h有序数组**的概念，一个h有序数组是指数组种任意间隔为h的两个元素是有序的（注意是说这两个元素有序，不是说这两个元素之间的所有元素是有序的）；一个h有序数组可以看作由h个互相独立的有序数组编织在一起组成的一个数组，下面是例子：
![h-sorted array](_v_images/20200123101638188_30997.png)
- 插入排序的思想是交换相邻的元素使之有序，而希尔排序的思想是交换间隔为h的元素，使数组变成一个h有序数组。然后，逐渐减小h的值，最终使之变成一个1-有序数组，那么整个数组就排好序了。那么如何选取h的下降规则呢，一个比较常用的是将h从N/3开始递减至1，这个序列就叫做递增序列
- 和插入排序对比：对于大规模数组，插入排序的元素只能一点一点从数组一端移到另一端；而希尔排序考虑了子数组的规模和有序性，比插入排序更快。希尔排序的代码就是在插入排序代码的基础上把移动元素的距离改为h

Python版：
```py
def shell_sort(lst):
    if not lst:
        return []
    h = 1
    while h < len(lst)/3:
        h = 3*h + 1  # 1, 4, 13, 40, 121, 364...
    while h >= 1:
        for i in range(h, len(lst)):
            j = i
            while j >= h and lst[j] < lst[j-h]:
                lst[j], lst[j-h] = lst[j-h], lst[j]
                j -= h
        h /= 3
    return lst
```

Golang版：
```go
func ShellSort(lst []int) []int {
    if len(lst) == 0 {
            return lst
    }
    h := 1
    for h < len(lst)/3 {
        h = h*3 + 1  // 1, 4, 13, 40, 121, 364...
    }
    for h >= 1 {
        for i := h; i < len(lst); i++ {
            for j := i; j >= h && lst[j] < lst[j-h]; j -= h {
                lst[j], lst[j-h] = lst[j-h], lst[j]
            }
        }
        h /= 3
    }
    return lst
}
```

#### 归并排序 Merge Sort
- 思想：采用了分治算法（divide-and-concur）的思想，将待排序的数组分为两半，对这两半数组**递归**地使用归并排序。两边排好序之后，从首元素开始比较，哪边的元素小就将其取出放入新数组，然后两边的首元素继续比较，最后得到的新数组就是排序好的数组。
- 时间复杂度：最坏情况下的时间复杂度为O(nlog n)

Python版：
```py
def merge_sort(lst):
    if not lst:
        return []
    mid = len(lst) // 2
    left = merge_sort(lst[:mid])
    right = merge_sort(lst[mid:])
    return merge(left, right)

def merge(left, right):
    l, r, res = 0, 0, []
    while l < len(left) and r < len(right):
        if left[l] < right[r]:
            res.append(left[l])
            l += 1
        else:
            res.append(right[r])
            r += 1
    return res + left[l:] + right[r:]
```

Golang版：
```go
func Merge(left []int, right []int) []int {
    var (
        l = 0
        r = 0
        res []int
    )
    for l < len(left) && r < len(right) {
        if left[l] < right[r] {
            res = append(res, left[l])
            l += 1
        } else {
            res = append(res, right[r])
            r += 1
        }
    }
    res = append(res, left...)
    res = append(res, right...)
    return res
}
```