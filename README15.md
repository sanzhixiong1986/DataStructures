# 第八天
### 重点知识（归并排序）

- 特点：分而治之


------

### 思路

它是把要排序的数组分成最小的单位进行排序，然后根据最小的单位然后还原到一个有序的数组（分开，然后还原（治理））

```java
参数 int[] arr，int left,int mid，int right，int[] temp
//原数组，左边索引，右边索引，中间索引，拷贝数组
int i = left;
int j = mid + 1;
int t = 0;	//拷贝数组操作
while(i <= mid && j <= right)
if(arr[i] < arr[j])
temp[t] = arr[i];i++,t++;
else temp[t] = arr[j];j++;t++;
//剩下的进行复制
while(i<=mid) temp[t]=arr[i];i++,t++
while(j<=right) temp[t] = arr[j];j++;t++;
//组合
t = 0;
int tempLeft = left;
while(tempLeft<=right)
arr[tempLeft] = temp[t];tempLeft++;t++;
```

### 分开

------

```java
参数 int[] arr，int left，int right，int[] temp
if left < right
int mid = (left + right)/2;
函数 （arr,left,mid,right,temp);
函数 （arr,mid+1,right,temp);
合并函数(arr,left,mid,right,temp);
```

------

### 代码编写

```java
//合并
public static void merge(int[] arr, int left, int mid, int right, int[] temp) {
  //初始化
  int i = left;
  int j = mid + 1;
  int t = 0;//拷贝参数
  //合并条件判断
  while (i <= mid && j <= right) {
    //左拷贝
    if (arr[i] <= arr[j]) {
      temp[t] = arr[i];
      i+=1;
      t+=1;
    } else {
      temp[t] = arr[j];
      t+=1;
      j+=1;
    }
  }

  //剩余的拷贝
  while (i <= mid) {
    temp[t] = arr[i];
    t+=1;
    i+=1;
  }

  while (j <= right) {
    temp[t] = arr[j];
    t+=1;
    j+=1;
  }
  //回复操作
  t = 0;
  int tempLeft = left;
  while (tempLeft <= right) {
    arr[tempLeft] = temp[t];
    tempLeft+=1;
    t+=1;
  }
}
```

### 分开

```java
public static void mergeSort(int[] arr,int left,int right,int[] temp){
  if(left < right){
    int mid = (left + right) / 2;
    mergeSort(arr,left,mid,temp);
    mergeSort(arr,mid+1,right,temp);
    merge(arr,left,mid,right,temp);
  }
}
```

### 测试代码

```java
package dataStr.sort;

import java.text.SimpleDateFormat;
import java.util.Arrays;
import java.util.Date;

/**
 * @author joy
 * @date 2021/8/16
 */
public class MergeSort {
    public static void main(String[] args) {
        int[] arr = new int[8];
        int temp[] = new int[arr.length];

        for (int i = 0; i < 8; i++) {
            arr[i] = (int) (Math.random() * 500000); // 生成一个[0, 8000000) 数
        }
        Date data1 = new Date();
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String date1Str = simpleDateFormat.format(data1);
        System.out.println("排序前的时间是=" + date1Str);

        mergeSort(arr, 0, arr.length - 1, temp);

        Date data2 = new Date();
        String date2Str = simpleDateFormat.format(data2);
        System.out.println("排序后的时间是=" + date2Str);

        System.out.println(Arrays.toString(arr));

    }

    public static void mergeSort(int[] arr, int left, int right, int[] temp) {
        if (left < right) {
            int mid = (left + right) / 2;
            mergeSort(arr, left, mid, temp);
            mergeSort(arr, mid + 1, right, temp);
            merge(arr, left, mid, right, temp);
        }
    }

    //合并
    public static void merge(int[] arr, int left, int mid, int right, int[] temp) {
        //初始化
        int i = left;
        int j = mid + 1;
        int t = 0;//拷贝参数
        //合并条件判断
        while (i <= mid && j <= right) {
            //左拷贝
            if (arr[i] <= arr[j]) {
                temp[t] = arr[i];
                i+=1;
                t+=1;
            } else {
                temp[t] = arr[j];
                t+=1;
                j+=1;
            }
        }

        //剩余的拷贝
        while (i <= mid) {
            temp[t] = arr[i];
            t+=1;
            i+=1;
        }

        while (j <= right) {
            temp[t] = arr[j];
            t+=1;
            j+=1;
        }
        //回复操作
        t = 0;
        int tempLeft = left;
        while (tempLeft <= right) {
            arr[tempLeft] = temp[t];
            tempLeft+=1;
            t+=1;
        }
    }
}
```

