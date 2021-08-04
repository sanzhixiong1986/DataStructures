# 第二天
### 应用场景

凡是二维数组，并且有大量没有关系的数据，这种都可以应用稀疏数组来进行转换。

范例：五子棋的保存退出

思路：五子棋的棋盘是一个二维数组，每一个落子的地方都可用对应的数字进行记录

稀疏数组作用：缩小数据量

### 使用方式

- 第一行第一列存储二维数组的行数，第一行第二列二维数组的列，第一行第三列存储有效数字的个数
- 第二行第一列存储有效第一个数组的行，第二行第二列存储第一个有效数字的列，第二行第三列存储有效数字，后面以此类推

### 重点学习（必须掌握）

- 稀疏数组转二维数组
- 二维数组转稀疏数组

### 伪代码

```java
//1.初始化二维数组,这样就会出现11*11个0
int originalArr[][] = new int [11][11];
//2.对应的位置进行数据赋值,1是代表黑子 2代表蓝子
originalArr[行][列] = 1
originalArr[行][列] = 2
//end 对原始数据进行初始化
//3.找到原始数组所有非0的个数用来初始化稀疏数组的行数
int sum = 0;
for i < originalArr.length;
for j < originalArr.length;
if(originalArr[i][j] != 0)
sum ++;
//找到个数sum
//3.初始化稀疏数组的
int sparseArr[][] = new int[sum+1][3];
sparseArr[0][0] = 11;
sparseArr[0][1] = 11;
//4.找到原始数据不为0的数据
int count = 0;
for i < originalArr.length;
for j < originalArr.length;
if(originalArr[i][j] != 0)
count ++;
sparseArr[count][0] = i;
sparseArr[count][1] = j;
sparseArr[count][2] = originalArr[i][j];
//结束后打印
//5.稀疏数组转二维数组
//（1）获得二维数组的大小
int originalArr1 = int [sparseArr[0][0]][sparseArr[0][1]];
//(2)赋值
for int i= 1; i<sparseArr.length;i++
originalArr1[sparseArr[i][0]][sparseArr[i][1]] = sparseArr[i][2];
//在打印数据 
```

### 代码验证

```java
package com.dataStruct;

import java.util.Arrays;

/**
 * @author joy
 * @date 2021/8/4
 */
public class SparseArrDemo {
    static final int ROW_COL = 11;
    public static void main(String[] args) {
        int originlArr[][] = new int[ROW_COL][ROW_COL];
        originlArr[1][2] = 1;
        originlArr[2][3] = 2;
        //end
        int sum = 0;
        for (int i = 0; i < ROW_COL; i++) {
            for (int j = 0; j < ROW_COL; j++) {
                if(originlArr[i][j] != 0){
                    sum++;
                }
            }
        }
        //初始化稀疏数组
        int sparseArr[][] = new int[sum+1][3];
        sparseArr[0][0] = ROW_COL;
        sparseArr[0][1] = ROW_COL;
        sparseArr[0][2] = sum;
        int cout = 0;
        for (int i = 1; i < ROW_COL; i++) {
            for (int j = 1; j < ROW_COL; j++) {
                if(originlArr[i][j] != 0){
                    cout++;
                    sparseArr[cout][0] = i;
                    sparseArr[cout][1] = j;
                    sparseArr[cout][2] = originlArr[i][j];
                }
            }
        }

        //验证sparseArr
        for (int i = 0; i <sparseArr.length ; i++) {
            System.out.print(sparseArr[i][0]+"\t"+ sparseArr[i][1]+"\t"+sparseArr[i][2]+"\n");
        }

        //稀疏数组转二维数组初始化
        int originlArr1[][] = new int[sparseArr[0][0]][sparseArr[0][1]];
        //赋值
        for (int i = 1; i < sparseArr.length; i++) {
            originlArr1[sparseArr[i][0]][sparseArr[i][1]] = sparseArr[i][2];
        }

        //验证
        for (int i = 0; i < originlArr1.length; i++) {
            System.out.print(Arrays.toString(originlArr1[i])+"\n");
        }
    }
}
```

