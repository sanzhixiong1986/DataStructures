# 第五天
### 重点知识

- 希尔排序是插入排序的一种优化，减少了插入排序的次数
- 代码的演化（需要有一个理解的过程），交换，移动

------

### 演化思路

```
[8, 9, 1, 7, 2, 3, 5, 4, 6 ,0] 10/2 = 5
第一次：[8,3][9,5][1,4][7,6][2,0] => 3,5,1,6,0,8,9,4,7,2                
第二次：[3,1,0,9,7][5,6,8,4,2] => 0,2,1,4,3,5,7,6,9,8
第三次：[0,1,2,3,4,5,6,7,8,9]
```

------

### 希尔的代码演化(交换)

```java
int[] arr = {8, 9, 1, 7, 2, 3, 5, 4, 6};//初始化数组

public void shellSort(int[] arr){
  int gap = arr.length/2;//第一次 4
  int temp = 0;
  //后面的数组部分
  for(int i = 4; i<arr.length;i++){
    //前面数组部分
    for(int j = i - 4;j>=0;j-=4){
      //往后移动多少个数据
			if(arr[j] > arr[j+4]){
        temp = arr[j];
        arr[j] = arr[j+4];
        arr[j+4] = temp
      }
    }
  }
}
```

#### 提炼重复部分

```java
for(int gap = arr.length/2;gap>0;gap/=2){
  for(int i = gap; i<arr.length;i++){
    //前面数组部分
    for(int j = i - gap;j>=0;j-=gap){
      //往后移动多少个数据
			if(arr[j] > arr[j+gap]){
        temp = arr[j];
        arr[j] = arr[j+gap];
        arr[j+gap] = temp;
      }
    }
  }
}
```

------

### 移动操作的优化方案

```java
for(int gap = arr.length/2;gap>0;gap/=2){
  for(int i = gap;i>=0;i-=gap){
    //借鉴的插入算法
    int j = i;
    int value = arr[j];
    //j - gap 数组的前面不分
    if(arr[j] > arr[j - gap]){
      while((j-gap)>=0 && temp > arr[j - gap]){
        //后移
        arr[j] = arr[j - gap];
        j -= gap;
      }
      //赋值
			arr[j] = value;
    }
  }
}
```

