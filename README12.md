# 第七天
### 重点知识

- 递归的基本介绍

  递归就是一个函数调用函数，调用参数会发生变化从而达到循环调用的方式

- 规则

  一定要有一个退出条件，不然会有死循环产生

------

### 简单的例子(1加到100)

```java
package dataStr.rekursion;

/**
 * @author joy
 * @date 2021/8/13
 */
public class RekDemo {
    private static int sum = 0;
    public static void main(String[] args) {
        oneToHundred(100);
    }
  
    private static void oneToHundred(int n) {
        //结束条件
      	if (n < 1) {
            return;
        }
        sum += n;
        System.out.println("sum=" + sum);
        //变化的参数n-1; 没有这两个条件一定是死归
      	oneToHundred(n - 1);
    }
}

```

------

### 迷宫

```java
package dataStr.rekursion;

import java.util.Arrays;

/**
 * @author joy
 * @date 2021/8/13
 */
public class MiGong {
    public static void main(String[] args) {
        //地图大小
        int[][] map = new int[8][7];
        //1为墙，2为走过的路径，3为死胡同
        //上方
        for (int i = 0; i < 7; i++) {
            map[0][i] = 1;
        }
        //下方
        for (int i = 0; i < 7; i++) {
            map[7][i] = 1;
        }

        //左边
        for (int i = 1; i < 7; i++) {
            map[i][0] = 1;
        }

        //右边
        for (int i = 1; i < 7; i++) {
            map[i][6] = 1;
        }

        map[3][1] = 1;
        map[3][2] = 1;
        setWay(map, 1, 1);
        showMap(map);
    }

    private static boolean setWay(int[][] map, int i, int j) {
        //设置终点
        if (map[6][5] == 2) {
            return true;
        } else {
            //这些地方没有做过
            if (map[i][j] == 0) {
                map[i][j] = 2;//走路的径路点
                if (setWay(map, i + 1, j)) {
                    return true;//向下走
                } else if (setWay(map, i, j + 1)) {//往右
                    return true;
                } else if (setWay(map, i - 1, j)) {//向上
                    return true;									
                } else if (setWay(map, i, j - 1)) {//向左
                    return true;
                } else {
                  	//其中这是退出条件1
                    map[i][j] = 3;//完全走不通
                    return false;
                }
            } else {
              	//退出条件2
              	//1，2，3 这三种都是不让走的情况
                return false;
            }
        }
    }

    private static void showMap(int[][] map) {
        for (int i = 0; i < 8; i++) {
            for (int j = 0; j < 7; j++) {
                System.out.print(map[i][j] + " ");
            }
            System.out.println();
        }
    }
}

```
