# 第六天
### 重点知识

- 必须是有序数组
- 演化思路
- 代码

------

### 演化思路

```
[1,2,3,4,5,6]
第一次：
mid = arr.length / 2; mid = 3
midVal = arr[mid] = 4;
if findVal > arr[mid]
mid +1
else if findVal < arr[mid]
mid -1;
else 
return mid;
return -1
```

------

### 二叉算法递归操作

```java
int[] arr = {1,2,3,4,5,6}
//算法方法
public int BinarSeach(int arr,int left,int right,int findVal){
  //递归首先需要把几种情况退出想法
  int mid = (left + right) >> 1;
  //1.超出边界
  if(left>rigjt || mid < 0){
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

#### 习题找到数组[1,2,3,4,5,6,6,6,6,7];中重复出现的数的下标

```java
int[] arr = {1,2,3,4,5,6,6,6,6,7}
//思路：就是找到和你需要找的数据相同的个数添加到arrayList里面返回这个arraylist就可以
//修改上面的代码
//1.超出边界
if(left>rigjt || mid < 0){
  return new ArrayList<>();
}

//找到以后
if(findVal > midVal){
  //数据在mid的右边那么mid需要++
  return BinarSeach(arr,mid+1,right,findVal);
}else if(findVal < midVal){
  return BinarSeach(arr,left,mid-1,findVal)
}else{
  //定一个arraylist
  ArrayList<Integer> list = new ArrayList<>();
  //定一个变量
  int temp = mid - 1; //往左移动
  while(true){
    //判断退出条件
    if(temp < 0 || findVale != arr[temp]){
      break;
    }
    list.add(temp);
    temp -= 1;
  }
  //把找到的数据加入
  list.add(mid);
  //往右查找
  temp = mid + 1;
  while(true){
    if(temp > arr.length - 1 || findVale != arr[temp]){
      break;
    }
    list.add(temp);
    temp+=1;
  }
  return list;
}


```

------

### 不使用递归的方法

```java
public int BinarSeach1(int[] arr,int findVal){
  int life = 0;
    int right = arr.length - 1;
    int mid = (life + right) >> 1;
		//这里要注意边界问题
    while (mid < right && mid >= life) {
        if (findVal > arr[mid]) {
            mid += 1;
        } else if (findVal < arr[mid]) {
            mid -= 1;
        } else {
            return mid;
        }
    }
    return -1;
}
```

