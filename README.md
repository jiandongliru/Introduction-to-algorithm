听b站大神左成云算法课做的笔记

https://www.bilibili.com/video/BV13g41157hK/?p=7&spm_id_from=333.1007.top_right_bar_window_history.content.click
### 复杂度
### 位运算
#### 异或
> 异或运算的性质
> 1. 相同的数异或为0，一个数和0异或为它本身
> 2. 异或运算满足交换率和结合率

**注意：go中没有按位与的符号，可以通过^n来实现**
**取某个数n的最右边的1**`rightone := n&(^n+1)`
###### 拓展
```
1. 一个数组，只有一个数为奇数个，其他均为偶数个，求这个数
```
leetcode:https://leetcode.cn/problems/single-number/
> https://github.com/xianren68/Introduction-to-algorithm/tree/main/bitwise/01_异或.go
```
2. 一个数组中，有两个数位奇数个，求这两个数
```


### 排序
#### 1.选择排序
> 从0开始进行n次循环，每次循环从当前值到数组末位，选择出一个最大或最小的值与当前位置进行交换
> 时间复杂度O(n^2)，空间复杂度o(1)

> https://github.com/xianren68/Introduction-to-algorithm/tree/main/basic_sort/1.选择排序.go
#### 2.冒泡排序
> 与选择排序相似，每次循环找出最小或最大的值，将其移动到数组末位，不过选择排序会记录最小或最大的值
> 一次循环只进行一次交换，而冒泡排序则对相邻元素比较，交换
> 时间复杂度o(n^2),空间复杂度o(1)

> https://github.com/xianren68/Introduction-to-algorithm/tree/main/basic_sort/2.冒泡排序.go
#### 3.插入排序
> 将要排序的值插入到已排序的值中，从第二值个开始遍历数组，将当前值前面的数作为已排序的序列，将当前值插入其中，
> 从而让有序序列的长度再次加1，然后再继续向下遍历,相比较于前面两个排序，插入排序的性能因为数据而有所不同，
> 当数据较为有序时，它的遍历次数会小很多，而选择与冒泡不会发生变化
> 时间复杂度o(n^2),空间复杂度o(1)

> https://github.com/xianren68/Introduction-to-algorithm/tree/main/basic_sort/3.插入排序.go
#### 4.归并排序
> 通过递归的方式，将给定的数据分为左右两个序列，分别让它们有序，然后将其合并，形成一个新的有序序列
> 时间复杂度,根据master公式为O(N*logN)，空间复杂度为O(N)

> https://github.com/xianren68/Introduction-to-algorithm/tree/main/basic_sort/4.归并排序.go
###### 拓展
```
1.求一个数组的小和 数组小和的定义如下：
例如，数组s = [1, 3, 5, 2, 4, 6]，在s[0]的左边小于或等于s[0]的数的和为0；在s[1]的左边小于或等于s[1]的数的和为1；在s[2]的左边小于或等于s[2]的数的和为1+3=4；在s[3]的左边小于或等于s[3]的数的和为1；
在s[4]的左边小于或等于s[4]的数的和为1+3+2=6；在s[5]的左边小于或等于s[5]的数的和为1+3+5+2+4=15。所以s的小和为0+1+4+1+6+15=27
给定一个数组s，实现函数返回s的小和
2.求数组逆序对
在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对
```
#### 5.快速排序
> 1.荷兰国旗问题：给定一个数组，并给定一个值num，将比num大的数放到数组前段，将=num的数放到数组中段，大于
> num的数放到数组后段
> 解法：
> 1. 给定两个指针l,r,用来指定<区的后一位和>区的前一位
> 2. 通过索引i遍历数组,如果小于num,将当前位置与l位置交换，扩充<区，l++
> 3. 如果小于num,将当前位置与l位置交换，扩充>区，r--,不知道交换回值的大小，所以i应保持不变
> 4. 当i=r时，所有的数已经排列完毕
###### 快速排序2.0：
>1. 将数组的最后一位作为指定数，然后通过递归将数组转化为三块，再将指定数放到等于区
>2. 通过递归将数组各个部分都执行上述操作，最后得到有序的数组
###### 快速排序3.0：
>因为2.0版本的快排很受数据的影响，时间复杂度为O(n^2),3.0基于2.0将指定数num从最后一位，换成随机取，然后再与最后
>一位进行交换，因为随机，所以不会受数据状况影响，时间复杂度为O(n * logN),空间复杂度为O(logN)

> https://github.com/xianren68/Introduction-to-algorithm/tree/main/basic_sort/5.快速排序.go
#### 6.堆排序
##### 堆（heap）
> 一个存储了一棵完全二叉树的数组（从左到右来添值）
> 如果每个子树的根节点都比其子节点大，则称为大根堆，根节点是整个树中的最大值，反之则为小根堆
##### 性质
> 1. 当前值在数组中的索引为i，则其左子节点的索引为（i*2)+1,右子节点为（i*2)+2
> 2. 当前值在数组中的索引为i,其父节点的索引为（i-1)/2
##### 操作（以大根堆为例）
> 1. 将数据入堆，heapsize +1 ,数据加入到二叉数的最后一个节点，然后判断其与父节点的大小，若大，则交换位置，
> 重复这个过程，直到没有父节点或父节点比它大，
> 2. 将数据出堆，弹出数组首位最大值，二叉树的最后一个节点提到头节点的位置，然后将heapsize - 1,
> 头节点判断其左右子树中最大的一个是否比自己大，若是，则交换位置，然后重复此操作，直到没有子节点或字节点都比小
##### 堆排序
> 1. 将指定数组遍历，让每个值都经历一次入堆操作，得到一个大根堆
> 2. 再次遍历大根堆，每次将头节点交换到堆的最后，然后再通过出堆的操作让剩余的数据依然形成大根堆，头节点为最大值
> 3. 重复二操作，直至堆中没有数据，此时数组成为升序序列
> 时间复杂度O(N*logN),空间复杂度O(1)

> https://github.com/xianren68/Introduction-to-algorithm/tree/main/basic_sort/6.堆排序.go
###### 拓展
```
已知一个几乎有序的数组，几乎有序是指一个数距离它排好序的距离不超过k,并且k相对数组长度较小，请选择合适的排序算法
进行排序
```
#### 7. 桶排序
> 前面的排序方式都是通过比较来进行排序的，我们也可以不进行比较来排序
##### 1.计数排序
> 首先，知道数组值的范围，定义出一个此范围的辅助数组，遍历原数组，原数组中的每个数都对应辅助数组上的一位
> 所以，可以统计出每个数出现的次数，然后根据辅助数组记录的计录的次数将数据填入源数组接口完成排序
> 时间复杂度O(N)，空间复杂度O(N)
##### 2.基数排序（桶排序）
> 根据数据的位数来进行排序，
> 1. 判断数据位数（十百千这种），根据数据的进制准备一个长度等于进制数的数组
> 2. 从最低位开始,将它们从小到大装到准备好的数组中，得到一个最低位升序的序列，将其放回原数组
> 3. 然后上升一位，再对原数组重复2操作，得到当前位得有序序列，将其放回原数组，一直重复上述操作，直到最高位也有序

> https://github.com/xianren68/Introduction-to-algorithm/tree/main/basic_sort/7.基数排序.go
**注意：不通过比较的排序对数据的要求很高，如果数组中数的范围很大，就不适用，而比较排序可以适用于任何数组**
```
marst公式
在计算涉及递归的算法的时候，计算复杂度就会变得有些麻烦。Master公式就是用来进行剖析递归行为和递归行为时间复杂度的估算的

Master公式：T(N) = a*T(N/b) + O(N^d)

公式解释：n表示问题的规模，a表示递归的次数也就是生成的子问题数，N/b表示子问题的规模。O(N^d)表示除了递归操作以外其余操作的复杂度

结论（证明省略）：
①当d<logb a时，时间复杂度为O(N^(logb a))
②当d=logb a时，时间复杂度为O((N^d)*logN)
③当d>logb a时，时间复杂度为O(N^d)

注意：子问题规模必须等分，不管你是分成几部分
```
#### 排序算法稳定性
> 排序之后相等的值与排序下之前相对位置保持不变

|排序|时间复杂度|空间复杂度|稳定性|
|---|---|---|---|
|选择排序|O(N^2)|O(1)|不稳定|
|冒泡排序|O(N^2)|O(1)|相等值不换位置可以稳定|
|插入排序|O(N^2)|O(1)|相等值不换位置可以稳定|
|归并排序|O(NlogN)|O(N)|合并数组时相等时，先将左边的加入数组，稳定|
|快速排序|O(NlogN)|O(logN)|不稳定|
|堆排序|O(NlogN)|O(1)|不稳定|

#### 排序总结
> 1. 不基于比较的排序，对样本数据的要求高，不易改写
> 2. 基于比较的排序，只要规定好如何比较就可以直接复用
> 3. 基于比较的排序，时间复杂度最小为O(N*logN)
> 4. 绝对速度选快排，节省空间用堆排，稳定选归并


### .查找
#### 1.二分法
> 通常用来在有序集合中查找某个值，将数组为三，当前值，左边的，右边的
> 如果当前值是要找的值，则直接返回，否则判断左右哪个符合条件，再将其一分为3继续重复上述过程
> 最后总能找到要查找的值，时间复杂度O(logN)
> 其实只要能确定要查找的值必然在数组分隔的两端
> 就可以用二分法

> https://github.com/xianren68/Introduction-to-algorithm/tree/main/search/01_二分法.go
###### 拓展
```
一个数组，求局部最小值(左右都比当前值大)
```

###  表
##### 有序表
> 其中所有元素以递增或递减方式有序排列
##### 哈希表
> 顺序存储的结构类型需要一个一个地按顺序访问元素，当这个总量很大且我们所要访问的元素比较靠后时，性能就会很低
> hash通过键值对映射的方式来加快访问记录，它是无序的
#### 链表
> 链表有一系列节点组成，节点主要包括当前节点值和它下一个节点的位置，由此链接成的链式结构
> 相比于数组，它的插入操作更快，但获取操作较慢
##### 重要技巧
> 笔试，以时间复杂度为要求
> 面试， 需要考虑时间复杂度
###### 常用方法
>1. 通过额外空间记录
>2. 快慢指针
###### 题目
```
1. 判断一个链表是否为回文链表
```
leetcode:https://leetcode.cn/problems/palindrome-linked-list/
> https://github.com/xianren68/Introduction-to-algorithm/tree/main/link_list/1.回文链表.go
```
2. 给定一个值，将链表分为小于给定值，等于给定值，大于给定值的三部分
```
leetcode:https://leetcode.cn/problems/partition-list-lcci/
> https://github.com/xianren68/Introduction-to-algorithm/tree/main/link_list/2.链表分区.go
```

3. 定义一种特殊的链表节点
{
    value,
    rand,
    next
}
rand是一个指针，可能指向某个节点或为空，给定一个由此节点构成的无环单链表，请将其复制，并返回头节点
```
leetcode:https://leetcode.cn/problems/copy-list-with-random-pointer/comments/
> https://github.com/xianren68/Introduction-to-algorithm/tree/main/link_list/3.复制链表.go




