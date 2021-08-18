# 第八天
### 重点知识（树删除）

### 删除节点的方法

```java
//删除节点
public void delNode(int no) {
  //第一步是遍历左节点
  if (this.left != null && this.left.no == no) {
    this.left = null;
    return;
  }

  if (this.right != null && this.right.no == no) {
    this.right = null;
    return;
  }

  //递归操作
  if (this.left != null) {
    this.left.delNode(no);
  }

  if (this.right != null) {
    this.right.delNode(no);
  }
}
```

### 二叉树删除节点的方法

```java
//删除
public void delNode(int no) {
  if (root != null) {
    if (root.getNo() == no) {
      root = null;
    } else {
      root.delNode(no);
    }
  } else {
    System.out.println("树为空");
  }
}
```

### 测试

```java
System.out.println("删除前");
binaryTree.prologue();
binaryTree.delNode(4);
System.out.println("删除后");
binaryTree.prologue();
```

#### 测试结果

```java
删除前
HeroNode{no=1, name='宋江'}
HeroNode{no=2, name='吴用'}
HeroNode{no=3, name='卢俊'}
HeroNode{no=4, name='林冲'}
删除后
HeroNode{no=1, name='宋江'}
HeroNode{no=2, name='吴用'}
HeroNode{no=3, name='卢俊'}
```

