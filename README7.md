# 第五天
### 重点知识

- 插入排序思路
- 代码的演化（需要有一个理解的过程）

------

### 插入排序

分成两个列表，每次比较以后把对应的数据插入到有序列表中的响应位置上。

```
[17,3,25,14,20,9]
第一次：(3,17)[25,14,20,9]
第二次：(3,17,25)[14,20,9]
第三次：(3,14,17,25)[20,9]
第四次：(3,14,17,20,25)[9]
第五次：(3,9,14,17,20,25)
```

------

### 选择的代码演化

```java
package dataStr.sort;

import java.util.Arrays;

/**
 * @author joy
 * @date 2021/8/10
 */
public class InsertSort {
    public static void main(String[] args) {
        int[] arr = {17, 3, 25, 14, 20, 9};
        insertSort(arr);
    }

    public static void insertSort(int[] arr) {
        //第一轮
        int insertVal = arr[1];
        //插入数据的前面一个索引
        int idx = 1 - 1;
        //操作不能超出数组边界
        while (idx >= 0 && insertVal < arr[idx]) {
            //后移
            arr[idx + 1] = arr[idx];
            //防止无限循环操作
            idx--;
        }
        arr[idx + 1] = insertVal;

        System.out.println("第1轮");
        System.out.println(Arrays.toString(arr));

        insertVal = arr[2];
        idx = 2 - 1;

        while (idx >= 0 && insertVal < arr[idx]) {
            //后移
            arr[idx + 1] = arr[idx];
            //防止无限循环操作
            idx--;
        }
        arr[idx + 1] = insertVal;

        System.out.println("第2轮");
        System.out.println(Arrays.toString(arr));

        insertVal = arr[3];
        idx = 3 - 1;

        while (idx >= 0 && insertVal < arr[idx]) {
            //后移
            arr[idx + 1] = arr[idx];
            //防止无限循环操作
            idx--;
        }
        arr[idx + 1] = insertVal;

        System.out.println("第3轮");
        System.out.println(Arrays.toString(arr));

        insertVal = arr[4];
        idx = 4 - 1;

        while (idx >= 0 && insertVal < arr[idx]) {
            //后移
            arr[idx + 1] = arr[idx];
            //防止无限循环操作
            idx--;
        }
        arr[idx + 1] = insertVal;

        System.out.println("第4轮");
        System.out.println(Arrays.toString(arr));


        insertVal = arr[5];
        idx = 5 - 1;

        while (idx >= 0 && insertVal < arr[idx]) {
            //后移
            arr[idx + 1] = arr[idx];
            //防止无限循环操作
            idx--;
        }
        arr[idx + 1] = insertVal;

        System.out.println("第5轮");
        System.out.println(Arrays.toString(arr));
    }
}
```

#### 提炼重复部分

```java
for (int i = 1; i < arr.length; i++) {
    //外层循环
    int value = arr[i];
    int idx = i - 1;
    while (idx >= 0 && value < arr[idx]) {
        //后移
        arr[idx + 1] = arr[idx];
        //防止死循环
        idx--;
    }
    arr[idx + 1] = value;
}
```

------

