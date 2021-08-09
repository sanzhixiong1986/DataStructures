# 第四天
### 重点知识

- 冒泡的基本思想（画图）
- 冒泡的演化
- 冒泡的优化

------

### 冒泡的思想

就是每一次进行对比，对比以后根据你的需求进行两个数据的交换，排序的次数刚好是数组的n-1次

------

### 冒泡的演化

```java
package dataStr.sort;

import java.util.Arrays;

/**
 * @author joy
 * @date 2021/8/9
 * 冒泡
 */
public class Bubble {
    public static void main(String[] args) {
        int arr[] = {3, 9, -1, 10, -2};
        //中间变量
        int temp = 0;
        for (int i = 0; i < arr.length - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        System.out.println("第一次排序后");
        System.out.println(Arrays.toString(arr));

        for (int i = 0; i < arr.length - 1 - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        System.out.println("第二次排序后");
        System.out.println(Arrays.toString(arr));

        for (int i = 0; i < arr.length - 1 - 2; i++) {
            if (arr[i] > arr[i + 1]) {
                temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        System.out.println("第三次排序后");
        System.out.println(Arrays.toString(arr));

        for (int i = 0; i < arr.length - 1 - 3; i++) {
            if (arr[i] > arr[i + 1]) {
                temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        System.out.println("第四次排序后");
        System.out.println(Arrays.toString(arr));
    }
}
```

#### 提炼重复部分

```java
int i = 0; i < arr.length - 1 - 3; i++
//这里是有一个arr.length -1 -(0-3)的4次操作，提炼称另一个循环
for (int i = 0; i < arr.length - 1; i++) {
    for (int j = 0; j < arr.length - 1 - i; j++) {
        if (arr[j] > arr[j + 1]) {
            temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
        }
    }
    System.out.println("第" + (i + 1) + "次排序后");
    System.out.println(Arrays.toString(arr));
}
```

------

### 优化代码

```java
int flag = false;
for (int i = 0; i < arr.length - 1; i++) {
    for (int j = 0; j < arr.length - 1 - i; j++) {
        if (arr[j] > arr[j + 1]) {
          	flag = true;
            temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
        }
    }
  	
  	if(!flag){
      break;
    }else{
      flag = false;
    }
    System.out.println("第" + (i + 1) + "次排序后");
    System.out.println(Arrays.toString(arr));
}
```

