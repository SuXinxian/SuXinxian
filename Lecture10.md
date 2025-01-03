## 10.1

# 1. 直接插入排序

原始序列：503、087、512、061、908、170、897、275、653、426

执行过程：
```
第1趟：087、503、512、061、908、170、897、275、653、426
第2趟：087、503、512、061、908、170、897、275、653、426
第3趟：061、087、503、512、908、170、897、275、653、426
第4趟：061、087、503、512、908、170、897、275、653、426
第5趟：061、087、170、503、512、908、897、275、653、426
第6趟：061、087、170、503、512、897、908、275、653、426
第7趟：061、087、170、275、503、512、897、908、653、426
第8趟：061、087、170、275、503、512、653、897、908、426
第9趟：061、087、170、275、426、503、512、653、897、908
```

# 2. 希尔排序(d[1]=5)

原始序列：503、087、512、061、908、170、897、275、653、426

执行过程：
```
分组：
组1：503、170
组2：087、897
组3：512、275
组4：061、653
组5：908、426

排序后各组：
组1：170、503
组2：087、897
组3：275、512
组4：061、653
组5：426、908

第1趟结果：170、087、275、061、426、503、897、512、653、908

直接插入排序：
最终结果：061、087、170、275、426、503、512、653、897、908
```

# 3. 快速排序

原始序列：503、087、512、061、908、170、897、275、653、426

执行过程：
```
第1趟：(以503为基准)
426、087、512、061、170、275、503、897、908、653

第2趟：(分别以170和897为基准)
061、087、170、275、426、503、512、653、897、908
```

# 4. 堆排序

原始序列：503、087、512、061、908、170、897、275、653、426

执行过程：
```
建立初始大顶堆：
908、653、897、275、426、170、512、061、087、503

逐步取出堆顶元素：
第1趟：503、653、897、275、426、170、512、061、087、908
第2趟：087、503、897、275、426、170、512、061、653、908
第3趟：061、503、512、275、426、170、087、897、653、908
第4趟：087、426、512、275、061、170、503、897、653、908
第5趟：170、275、061、087、426、512、503、897、653、908
第6趟：426、087、061、170、275、512、503、897、653、908
第7趟：503、087、061、170、275、426、512、897、653、908
第8趟：512、087、061、170、275、426、503、897、653、908
第9趟：653、087、061、170、275、426、503、512、897、908
第10趟：897、087、061、170、275、426、503、512、653、908

最终结果：061、087、170、275、426、503、512、653、897、908
```

# 5. 归并排序

原始序列：503、087、512、061、908、170、897、275、653、426

执行过程：
```
第1趟：(两两归并)
087,503 | 061,512 | 170,908 | 275,897 | 426,653

第2趟：(四四归并)
061,087,503,512 | 170,275,897,908 | 426,653

第3趟：(完全归并)
061,087,170,275,426,503,512,653,897,908
```

# 6. 基数排序

原始序列：503、087、512、061、908、170、897、275、653、426

执行过程：
```
个位：
170、061、512、503、653、275、426、087、897、908

十位：
503、908、512、426、653、061、170、275、087、897

百位：
061、087、170、275、426、503、512、653、897、908
```

所有排序的最终结果都是：061、087、170、275、426、503、512、653、897、908

## 10.3

# 稳定的排序算法

1. 直接插入排序（Insertion Sort）
- 在插入过程中，只有当新元素小于已排序序列中的元素时才会进行交换，相等元素的相对位置不会改变。

2. 冒泡排序（Bubble Sort）
- 只有当后一个元素小于前一个元素时才会交换，相等元素不会交换位置。

3. 归并排序（Merge Sort）
- 在归并过程中，当遇到相等的元素时，可以优先选择前面的序列中的元素，从而保持稳定性。

4. 基数排序（Radix Sort）
- 使用计数排序作为内部排序时，相同数字的相对顺序在每一趟排序中都不会改变。

# 不稳定的排序算法

1. 希尔排序（Shell Sort）
实例：设有序列 [3,3',4,1]，增量为2
- 第一趟比较3和4，3和1：得到 [1,3',4,3]
- 第二趟直接插入：得到 [1,3,3',4]
- 可以看到原序列中两个3的相对位置发生了改变

2. 快速排序（Quick Sort）
实例：序列 [2,2',1]，以2为基准
- 把小于2的数放左边，大于等于2的数放右边
- 得到 [1,2',2]
- 两个2的相对位置改变了

3. 堆排序（Heap Sort）
实例：序列 [2,2',1]
- 建立大顶堆过程中，第一个2会与1交换位置
- 最终序列变成 [1,2',2]
- 两个2的相对位置发生了改变

4. 选择排序（Selection Sort）
实例：序列 [2,2',1,3]
- 第一次选择最小值1与第一个2交换：[1,2',2,3]
- 可以看到两个2的相对位置改变了


## 10.6


# 1. 结束条件分析

奇偶交换排序的结束条件是：在连续的奇数趟和偶数趟比较中，都没有发生任何交换操作。

理由如下：
- 如果某一趟比较中发生了交换，说明序列仍然存在逆序对
- 只有当奇数位置和偶数位置的相邻元素都处于正确的顺序时，整个序列才能保证完全有序
- 因此需要连续两趟（一趟奇数位置，一趟偶数位置）都没有发生交换，才能确保整个序列已经完全有序

# 2. 比较次数分析

## 正序情况

当初始序列已经是正序时（例如：1,2,3,4,5）：
- 第一趟（奇数位置）：比较次数为⌊n/2⌋，无交换发生
- 第二趟（偶数位置）：比较次数为⌊(n-1)/2⌋，无交换发生
- 由于连续两趟都没有发生交换，算法终止

总比较次数 = ⌊n/2⌋ + ⌊(n-1)/2⌋

## 逆序情况

当初始序列完全逆序时（例如：5,4,3,2,1）：
- 每一趟都会发生尽可能多的交换
- 对于长度为n的序列，每趟比较次数分别为：
  - 奇数趟：⌊n/2⌋次比较
  - 偶数趟：⌊(n-1)/2⌋次比较
- 需要进行(n-1)趟才能完成排序

总比较次数 = (n-1) × (⌊n/2⌋ + ⌊(n-1)/2⌋)

这种排序方法在处理逆序序列时需要进行最多的比较次数，是其最坏情况。而处理已经有序的序列时只需要最少的比较次数，是其最好情况。这符合大多数排序算法的特征。


## 10.12

# 1. 序列（100、86、48、73、35、39、42、57、66、21）

这个序列不是小顶堆或大顶堆。我们可以将其调整为大顶堆：

第一步：画出完全二叉树
```
         100
      86     48
    73  35  39  42
  57 66 21
```

分析：这已经很接近大顶堆，只需要调整右子树。比较48和42，不需要交换。比较48和39，不需要交换。
因此这个序列实际上已经是大顶堆，不需要任何交换操作。

交换次数：0次

# 2. 序列（12、70、33、65、24、56、48、92、86、33）

这个序列既不是小顶堆也不是大顶堆。让我们调整为大顶堆：

第一步：画出完全二叉树
```
         12
      70    33
    65  24  56  48
  92 86 33
```

调整过程：
1. 12与70交换
2. 12与65交换
3. 12与92交换
4. 33与56交换

最终结构：
```
         92
      70    56
    65  24  33  48
  12 86 33
```

交换次数：4次

# 3. 序列（103、97、56、38、66、23、42、12、30、52、06、20）

第一步：画出完全二叉树
```
          103
      97      56
    38  66  23  42
  12 30 52 06 20
```

分析：这个序列在103作为根节点的情况下，很接近大顶堆。只需要在右子树进行少量调整：
1. 56与42比较，不需要交换
2. 23与52比较，需要交换

最终结构：
```
          103
      97      56
    38  66  52  42
  12 30 23 06 20
```

交换次数：1次

# 4. 序列（05、56、20、23、40、38、29、61、35、76、28、100）

第一步：画出完全二叉树
```
          05
      56     20
    23  40  38  29
  61 35 76 28 100
```

要调整为大顶堆，需要进行以下交换：
1. 05与56交换
2. 20与29交换
3. 20与76交换
4. 56与100交换
5. 29与76交换

最终结构：
```
          100
      76     76
    61  40  38  29
  23 35 20 28 05
```

交换次数：5次

## 10.33

``` C
// 定义链表节点结构
typedef struct LNode {
    int data;           // 数据域
    struct LNode *next; // 指针域
} LNode, *LinkList;

// 选择排序的链表实现
void SelectionSort(LinkList head) {
    if (head == NULL || head->next == NULL) {
        return;  // 空链表或只有一个节点时直接返回
    }
    
    LNode *p, *q, *min, *pre, *minPre;
    
    // 外层循环，p为已排序序列的最后一个节点
    for (p = head; p->next != NULL; p = p->next) {
        min = p->next;  // min指向未排序序列的第一个节点
        minPre = p;     // minPre指向min的前驱节点
        
        // 内层循环，查找最小值节点
        for (q = p; q->next != NULL; q = q->next) {
            if (q->next->data < min->data) {
                min = q->next;
                minPre = q;
            }
        }
        
        // 如果找到的最小值节点不是当前节点的后继，则进行交换
        if (min != p->next) {
            // 保存最小值节点的后继
            LNode *temp = min->next;
            // 将最小值节点插入到已排序序列的末尾
            min->next = p->next;
            p->next = min;
            // 连接最小值节点的前驱和后继
            minPre->next = temp;
        }
    }
}

// 创建链表的辅助函数
LinkList CreateList(int arr[], int n) {
    LinkList head = (LinkList)malloc(sizeof(LNode));
    head->next = NULL;
    LNode *p = head;
    
    for (int i = 0; i < n; i++) {
        LNode *node = (LNode*)malloc(sizeof(LNode));
        node->data = arr[i];
        node->next = NULL;
        p->next = node;
        p = node;
    }
    
    return head;
}

// 打印链表的辅助函数
void PrintList(LinkList head) {
    LNode *p = head->next;
    while (p != NULL) {
        printf("%d ", p->data);
        p = p->next;
    }
    printf("\n");
}
```