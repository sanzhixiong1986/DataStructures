# 第六天
### 重点知识

- 必须是有序数组
- 演化思路
- 存在的意义：使用算法减少递归的次数（但是要在一个比较均匀的数组中合适）
- 代码

------

### 演化思路

```
[1,2,3,4,5,6]
第一次：
int mid = life + (findVal - arr[life]) / (arr[right] - arr[life]) * (right - life); 
midVal = arr[mid] = 4;
if findVal > arr[mid]
mid +1
else if findVal < arr[mid]
mid -1;
else 
return mid;
return -1
```

重点：mid = int mid = life + (findVal - arr[life]) / (arr[right] - arr[life]) * (right - life);

------

### 差值算法递归操作

```java
int[] arr = {1,2,3,4,5,6}
//算法方法
public int BinarSeach(int arr,int left,int right,int findVal){
  //递归首先需要把几种情况退出想法
  int mid = left + (findVal - arr[left]) / (arr[right] - arr[left]) * (right - left);
  //1.超出边界
  if(left>rigjt || findVal > arr[right] || findVal < arr[left]){
    return -1;
  }
  int midVal = arr[mid];
  //2.如果正常找到退出
  if(findVal > midVal){
    //数据在mid的右边那么mid需要++
    return BinarSeach(arr,mid+1,right,findVal);
  }else if(findVal < midVal){
    return BinarSeach(arr,left,mid-1,findVal)
  }else{
    return mid;//找到
  }
}
```

------



### 
