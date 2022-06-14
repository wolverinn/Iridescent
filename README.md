# Iridescent
Solid data structure and algorithms in Python

<div align="center">
<img src="_v_images/20200102113345622_12587.jpg" width="640px">
</div>

目前进度：数据结构部分已完成，算法部分即将开始完善链表和二叉树相关算法。Star this repo and come back later :）  
（2022-06更新：终于更新了算法练习的部分）

## Data Structure
数据结构我跟的主要知识体系是浙江大学的MOOC《[数据结构](https://www.icourse163.org/course/ZJU-93001)》，以及[这个GitHub仓库](https://github.com/jwasham/coding-interview-university/blob/master/translations/README-cn.md)中的数据结构部分

#### [数据结构分析](Data%20Structure.md)
每种数据结构都用Python实现了常用操作，并分析了时间复杂度（其实通过代码也能分析出来），部分复杂的数据结构（红黑树/B树/堆/哈希表...）有我自己学习过程中的一些理解。完整代码在下面的```ipynb```文件中。

- 数组
- 链表
- 堆栈
- 队列
    - 循环队列
- 二叉树
    - 二叉树的遍历
- 二叉搜索树
- 平衡查找树
    - AVL 树
    - 红黑树
    - B树、B+树
- 堆
- 字典树
- 并查集
- 哈希表

#### [数据结构完整代码实现，含测试用例和注释](Data%20Structure%20code%20complete.ipynb)
（建议在本地查看```.ipynb```文件，方便运行和页内跳转）

建议自己亲自实现一遍数据结构的所有操作，然后用我写的测试用例运行一下。自己写一遍能够掌握得更牢固。写的时候最好先看原理，理解每种操作怎么实现再自己写，我的代码仅仅作为参考，需要思路的时候再看我的代码，最好不要先看。

## Algorithm
算法我跟的主要知识体系是 Robert Sedgewick 的《算法-第四版》，以及Coursera上面配套的Princeton的网课。部分知识点已经在数据结构当中用代码实现过了，所以就进行了省略。

大部分算法我都用了 Python 和 Golang 两种语言去实现，这样做不仅是熟悉语言的一种方式，也可以让你对算法对掌握更加牢固，同时如果有些地方不太看得懂，可以试试看另一种语言对实现，说不定能够获得更清晰的思路

#### [算法分析](Algorithms.md)
* 算法复杂度分析
* 排序算法
  * 冒泡排序
  * 选择排序
  * 插入排序
  * 希尔排序
  * 归并排序
  * 快速排序
  * 堆排序
* 查找
  * 二分查找
  * 二叉搜索树
  * 红黑树
  * 散列表
* 链表相关算法
* 二叉树相关算法
* 图相关算法
* 字符串相关算法

#### [算法练习](Algorithm%20practice.ipynb)
（建议在本地查看```.ipynb```文件，方便运行和页内跳转）

主要是为了方便算法的练习，一些测试代码用的数据结构已经在文件里构造好了。并且只练习最高频最经典的一些算法，方便快速找到手感。
