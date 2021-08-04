# 第二天
### 队列的特点

先进先出，可以想象我们排队买票

### 案例

银行排队叫号

### 伪代码

```java
class Queue
//属性
private int head //投指针
private int re   //尾部
private int maxSize;//最大范围
private int[] arr;  //数组

//构造函数
Queue(int max)
 maxSize = max;
 arr = new int[maxSize];
 head = -1;
 re = -1;

//是否为空
isNull()
	return re == head;

//是否满
isFull()
	return re == maxSize - 1;

//添加数据
addQueue(int value)
	//判断是否超过了
	if isFull
	re++;
	arr[re] = value;

//获得数据
getQueue()
	//判断是否为空
	if isNull
	//打印提示，或者抛出错误
	head++
	return arr[head];
```

### 问题

数组不能重复使用，重复使用累加以后使用%进行操作可以回复原来的数据，下面是优化以后的伪代码

### 伪代码

```java
//构造函数
Queue(int max)
	maxSize = max;
	 arr = new int[maxSize];

//判断是否满
isFull()
	return (re+1)%maxSize;//每次加完以后又重新来过

addQueue(int value)
	if isFull
	arr[re] = value;
	re = (re+1)%maxSize;

getQueue()
	if isNull
	int value = arr[head];
	head = (head+1)%maxSize;
```

### 总结

- 队列的特点（掌握）
- 代码的运行基础思想（必须掌握）

