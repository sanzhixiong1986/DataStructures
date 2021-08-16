# 第八天
### 重点知识（快速排序）

- 特点：它也是冒泡排序的一种改良版


------

### 思路

它是找到一个支点，根据支点把数组分成了两个部分，通过两个部分数据和支点进行对比以后在进行分配数组，然后在对两个数组进行递归排序，排序以后就可以得到一个有序的数组

```java
int temp = 0;
//找到你要的中间数据
int c = (left + right)/2;
//记录当前的最左边和右边的坐标
int l = left;
int r = right;
while(l < r)//找一轮
while(arr[l]<c)//找左边
l+=1
while(arr[r]>c)//找右边
r-=1
//交换
temp = arr[l];
arr[l] = arr[r];
arr[r] = temp;
得到[-9, -267, 0, 23, 78, 70]
//判断退出条件
if(l >= r) break;//一轮了
if(arr[l] == arr[c]) r-=1;//继续后移
if(arr[r] == arr[c]) l+=1;//继续前进
//如果两个都相等了以后的情况
if(l == r) l+=1;r-=1;//防止死循
//判断递归的条件
if(left < r) (arr,left,r)
if(l < right) (arr,l,right)
```

------

### 代码编写

```java
public void quickSeach(int[] arr,int left,int right){
  int temp = 0;					//变量
  int c = arr[(left+right)/2];
  //记录
  int l = left;
  int r = right;
  //扫一轮
  while(l<r){
    //判断条件出去
    if(l>=r){
      break;
    }
    //左搜寻
    if(arr[l] < c){
      l+=1;
    }
    //右搜索
    if(arr[r] > c){
      r-=1;
    }
    //交换
    temp = arr[l];
    arr[l] = arr[r];
    arr[r] = temp;
    
    //判断数值相等
    if(arr[l] == c){
      r-=1;
    }
    
    if(arr[r] == c){
      l+=1;
    }
  }
  //判断移动的下标是否相等
  if(l == r){
    l+=1;
    r-=1;
  }
  
  //递归条件
  if(l < right){
    quickSeach(arr,l,right);
  }
  
  if(r > life){
    quickSeach(arr,left,r);
  } 
}
```

### 测试8000000个数据时间

```java
int[] arr = new int[8000000];
for (int i = 0; i < 8000000; i++) {
  arr[i] = (int) (Math.random() * 8000000); // 生成一个[0, 8000000) 数
}
System.out.println("排序前");
Date data1 = new Date();
SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
String date1Str = simpleDateFormat.format(data1);
System.out.println("排序前的时间是=" + date1Str);

quickSort(arr, 0, arr.length-1);

Date data2 = new Date();
String date2Str = simpleDateFormat.format(data2);
System.out.println("排序前的时间是=" + date2Str);

//时间
排序前的时间是=2021-08-16 12:02:04
排序后的时间是=2021-08-16 12:02:06
大概2秒钟还是非常快
```

