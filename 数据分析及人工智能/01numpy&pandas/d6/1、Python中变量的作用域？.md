1、Python中变量的作用域？变量查找顺序？

```
x = 1
def outer():
    y = 2
    def inner():
        a = 1
        print(a)
        return inner
```



2、代码中经常遇到的*args和**kwargs的含义及用法*arg代表任意个位置参数，**kwargs代表任意个关键字参数，使用顺序为def 函数名（位置参数，args，默认参数，\**kwargs），即arg一定在**kwargs之前。

3、

```
a = 10
b = 20
c = [a]
a = 15
print(c)
会输出什么?为什么?
```



4、择一实现快速排序、冒泡排序、选择排序  写法一：平均空间复杂度为O(nlonn)  设置基准值，分区，合并子列

```
def quickSort(a_list):
    if len(a_list) <=1:
        return a_list
    # 设置基本值
    pivot = a_list[0]
    
    left = []
    right = []
    for i in range(1, len(a_list)):
        if a_list[i] > pivot:
            right.append(a_list[i])
        if a_list[i] <= pivot:
            left.append(a_list[i]))
     return quickSort(left) + [pivot] + quickSort(right)
```























































```python
写法一：平均空间复杂度为O(nlonn)
def quickSort(a_list):
    if len(a_list) <= 1:
        return a_list
    pivot = a_list[0]
    # 生成式写法
    # left = [a_list[i] for i in range(1,len(a_list)) if a_list[i] < pivot]
    # right = [a_list[i] for i in range(1,len(a_list)) if a_list[i] >= pivot]
    # 常规写法
    left = []
    right = []
    for i in range(1, len(a_list)):
        if a_list[i] < pivot:
            left.append(a_list[i])
        if a_list[i] >= pivot:
            right.append(a_list[i])
    return quickSort(left) + [pivot] + quickSort(right)


a_list = [2, 3, 4, 2, 3, 41, 34, 656, 7, 45, 34, 45]
print(quickSort(a_list))

写法二：平均空间复杂度为 O(logn) 
def quickSort(a_list, left, right):
    """
    :param a_list: 待排序数组
    :param left:  数组上界  这里是0？
    :param right: 数组下界  这里是数组长度-1？
    :return:
    """

    # 分区
    def partition(a_list, left, right):
        # 设置基准值
        pivot = a_list[left]

        while left < right:

            while left < right and a_list[right] >= pivot:
                # 条件成立，右侧指针左移一位
                right -= 1
            # 比基准值小的交换到基准前面
            a_list[left] = a_list[right]
            
            while left < right and a_list[left] <= pivot:
                left += 1
            # 比基准值大的交换到基准后面面
            a_list[right] = a_list[left]
        # 校验基准，也可以是a_list[right] = pivot
        a_list[left] = pivot
        # 返回基准索引  return right
        return left

    # 递归
    if left < right:
        pivotIndex = partition(a_list, left, right)
        # 左序列
        quickSort(a_list, left, pivotIndex - 1)
        # 右序列
        quickSort(a_list, pivotIndex + 1, right)
        return a_list


a_list = [23, 4, 34, 54, 23, 43, 34, 54, 657, 34, 2, 232]
print(quickSort(a_list, 0, len(a_list) - 1))
```

