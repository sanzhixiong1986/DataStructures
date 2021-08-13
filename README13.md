# 第七天
### 重点知识

- 栈的特点

  栈是先入后出，使用数组来模拟栈的操作


------

### 入门简单代码

```java
class ArrayStack {
  private int size;
  private int[] stack;
  private top;
  
  public ArrayStack(int size){
    this.size = size;
    this.stack = new int[size];
    this.top = -1;
  }
  
  //首先判断数据溢出，和空的情况
  public boolean isFull(){
    return top == size - 1;
  }
  
  public boolean isEmpty(){
    return top == -1;
  }
  
  //入栈
  public int push(int value){
    //判断是否满
    if(isFull()){
      System.out.println("已经满了");
      return;
    }
    this.top ++;
    stack[top] = value;
    return 0;
  }
  
  //出栈
  public int pop(){
    if(isEmpty()){
      System.out.println("栈已经为空了");
      return;
    }
    int value = stack[top];
    top--;
    return value;
  }
}

```

------

### 测试代码

```java
 //测试
ArrayStack arrayStack = new ArrayStack(4);
arrayStack.push(1);
arrayStack.push(2);
arrayStack.push(3);
arrayStack.push(4);
arrayStack.list();
//删除
arrayStack.pop();
arrayStack.list();
```

结果

```
4	3	2	1	
3	2	1	
```

