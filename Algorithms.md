# Algorithms

## 算法复杂度分析
待完成

## Sorting
#### 选择排序 Selection Sort
- 思想：最开始，找到数组中最小的元素，将其和数组第一个元素交换位置；然后在剩下的元素中找到最小的元素，将其和数组的第二个元素交换位置，如此往复。。。简单地说，就是不断在剩余元素中选取最小者放到剩余元素的首位。
- 复杂度：大约会进行N次交换以及N^2次比较

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