# 第四天
### 重点知识

- 选择排序思路
- 代码的演化（需要有一个理解的过程）

------

### 选择排序

先找到最小的数据，然后在进行交换，交换以后的后面数据继续找最小（大）数据进行交换，交换次数是n-1次

```
原始[101,34,119,1]
第一轮：1,34,119,101
第二轮：1,34,119,101
第三轮：1,34,101,119
```

------

### 选择的代码演化

```java
package dataStr.sort;

import java.util.Arrays;

/**
 * @author joy
 * @date 2021/8/9
 */
public class SelectSort {
    public static void main(String[] args) {
        int[] arr = {101, 34, 119, 1};
        selectSort(arr);
    }

    //推到过程
    public static void selectSort(int[] arr) {
        //第一次
        int minIndex = 0;//最小的数值的下标
        int min = arr[0];//加入最小的数据

        for (int j = 0 + 1; j < arr.length; j++) {
            if (min > arr[j]) {
                //修改索引
                minIndex = j;
                //修改当前最小数据
                min = arr[j];
            }
        }

        //交换两个数值
        arr[minIndex] = arr[0];
        arr[0] = min;
        System.out.println("第一次");
        System.out.println(Arrays.toString(arr));

        minIndex = 1;//最小的数值的下标
        min = arr[1];//加入最小的数据

        for (int j = 1 + 1; j < arr.length; j++) {
            if (min > arr[j]) {
                //修改索引
                minIndex = j;
                //修改当前最小数据
                min = arr[j];
            }
        }

        //交换两个数值
        arr[minIndex] = arr[1];
        arr[1] = min;
        System.out.println("第二次");
        System.out.println(Arrays.toString(arr));


        minIndex = 2;//最小的数值的下标
        min = arr[2];//加入最小的数据

        for (int j = 2 + 1; j < arr.length; j++) {
            if (min > arr[j]) {
                //修改索引
                minIndex = j;
                //修改当前最小数据
                min = arr[j];
            }
        }

        //交换两个数值
        arr[minIndex] = arr[2];
        arr[2] = min;
        System.out.println("第三次");
        System.out.println(Arrays.toString(arr));
    }
}
```

#### 提炼重复部分

```java
for (int i = 0; i < arr.length - 1; i++) {
    int minIndex1 = i;
    int min1 = arr[i];
    for (int j = i + 1; j < arr.length; j++) {
        if (min1 > arr[j]) {
            minIndex1 = j;
            min1 = arr[j];
        }
    }

    arr[minIndex1] = arr[i];
    arr[i] = min1;
    System.out.println("第" + (i + 1) + "次");
    System.out.println(Arrays.toString(arr));
}
```

------

