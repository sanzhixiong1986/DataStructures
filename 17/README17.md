# 第八天
### 重点知识（树查找）

会遍历了查找就很简单了

### 前序查找

```java
//前序查找
public HeroNode prologueFind(int no) {
  System.out.println("进入前序查找");
  //头
  if (this.no == no) {
    return this;
  }
  HeroNode resHero = null;
  //左节点递归
  if (this.left != null) {
    resHero = this.left.prologueFind(no);
  }
  if (resHero != null) {
    return resHero;
  }
  //右节点递归
  if (this.right != null) {
    resHero = this.right.prologueFind(no);
  }
  return resHero;
}

```

### 中序查找

```java
//中序列查找
public HeroNode midOrderFind(int no) {
  HeroNode resHero = null;//接受数据
  if (this.left != null) {
    resHero = this.left.midOrderFind(no);
  }
  if (resHero != null) {
    return resHero;
  }
  System.out.println("进入中序");
  if (this.no == no) {
    return this;
  }

  if (this.right != null) {
    resHero = this.right.midOrderFind(no);
  }
  return resHero;
}
```

### 后序查找

```java
//后序
public HeroNode backOrderFind(int no) {
  HeroNode resHero = null;//接受数据
  if (this.left != null) {
    resHero = this.left.backOrderFind(no);
  }
  if (resHero != null) {
    return resHero;
  }

  if (this.right != null) {
    resHero = this.right.backOrderFind(no);
  }
  if(resHero != null){
    return resHero;
  }

  System.out.println("进入后续");
  if (this.no == no) {
    return this;
  }
  return resHero;
}
```

#### 测试代码

```java
package dataStr.tree;

/**
 * @author joy
 * @date 2021/8/18
 * 二叉树
 */
public class BinaryTreeDemo {
    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();

        HeroNode node1 = new HeroNode(1, "宋江");
        HeroNode node2 = new HeroNode(2, "吴用");
        HeroNode node3 = new HeroNode(3, "卢俊");
        HeroNode node4 = new HeroNode(4, "林冲");
        binaryTree.setRoot(node1);
        node1.setLeft(node2);
        node1.setRight(node3);
        node3.setRight(node4);

        HeroNode res = binaryTree.backOrderFind(4);
        if (res != null) {
            System.out.println("找到");
        } else {
            System.out.println("没有找到");
        }
    }
}

//创建二叉树的根节点
class BinaryTree {
    private HeroNode root;//根节点

    public void setRoot(HeroNode root) {
        this.root = root;
    }

    //前序
    public void prologue() {
        if (this.root != null) {
            root.prologue();
        } else {
            System.out.println("二叉树没有根节点");
        }
    }

    //中序
    public void midOrder() {
        if (this.root != null) {
            root.midOrder();
        } else {
            System.out.println("二叉树没有根节点");
        }
    }

    //后序
    public void backOrder() {
        if (this.root != null) {
            root.backOrder();
        } else {
            System.out.println("二叉树没有根节点");
        }
    }

    public HeroNode prologueFind(int no) {
        if (this.root != null) {
            return root.prologueFind(no);
        } else {
            return null;
        }
    }

    public HeroNode midOrderFind(int no) {
        if (this.root != null) {
            return root.midOrderFind(no);
        } else {
            return null;
        }
    }

    public HeroNode backOrderFind(int no) {
        if (this.root != null) {
            return root.backOrderFind(no);
        } else {
            return null;
        }
    }
}


//二叉树的节点
class HeroNode {
    private int no;
    private String name;
    private HeroNode left;
    private HeroNode right;

    public HeroNode(int no, String name) {
        this.no = no;
        this.name = name;
    }

    public int getNo() {
        return no;
    }

    public void setNo(int no) {
        this.no = no;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public HeroNode getLeft() {
        return left;
    }

    public void setLeft(HeroNode left) {
        this.left = left;
    }

    public HeroNode getRight() {
        return right;
    }

    public void setRight(HeroNode right) {
        this.right = right;
    }

    @Override
    public String toString() {
        return "HeroNode{" +
                "no=" + no +
                ", name='" + name + '\'' +
                '}';
    }

    //前序（头在前面）
    public void prologue() {
        //输入头
        System.out.println(this);
        if (this.left != null) {
            this.left.prologue();
        }
        if (this.right != null) {
            this.right.prologue();
        }
    }

    //中序
    public void midOrder() {
        if (this.left != null) {
            this.left.prologue();
        }
        System.out.println(this);
        if (this.right != null) {
            this.right.prologue();
        }
    }

    //后续
    public void backOrder() {
        if (this.left != null) {
            this.left.prologue();
        }
        if (this.right != null) {
            this.right.prologue();
        }
        System.out.println(this);
    }

    //前序查找
    public HeroNode prologueFind(int no) {
        System.out.println("进入前序查找");
        //头
        if (this.no == no) {
            return this;
        }
        HeroNode resHero = null;
        //左节点递归
        if (this.left != null) {
            resHero = this.left.prologueFind(no);
        }
        if (resHero != null) {
            return resHero;
        }
        //右节点递归
        if (this.right != null) {
            resHero = this.right.prologueFind(no);
        }
        return resHero;
    }

    //中序列查找
    public HeroNode midOrderFind(int no) {
        HeroNode resHero = null;//接受数据
        if (this.left != null) {
            resHero = this.left.midOrderFind(no);
        }
        if (resHero != null) {
            return resHero;
        }
        System.out.println("进入中序");
        if (this.no == no) {
            return this;
        }

        if (this.right != null) {
            resHero = this.right.midOrderFind(no);
        }
        return resHero;
    }

    //后序
    public HeroNode backOrderFind(int no) {
        HeroNode resHero = null;//接受数据
        if (this.left != null) {
            resHero = this.left.backOrderFind(no);
        }
        if (resHero != null) {
            return resHero;
        }

        if (this.right != null) {
            resHero = this.right.backOrderFind(no);
        }
        if(resHero != null){
            return resHero;
        }

        System.out.println("进入后续");
        if (this.no == no) {
            return this;
        }
        return resHero;
    }
}
```

