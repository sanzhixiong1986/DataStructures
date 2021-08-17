# 第八天
### 重点知识（树基础）

- 为什么要有树结构
- 树的常用术语
- 二叉树
- 二叉树的遍历


------

### 为什么要有树的结构

数组的优点：访问速度快，算法多

数组的缺点：插入删除比较麻烦，扩容性比较差，其中扩容可以参考ArrayList的数组扩容

链表优点：删除，插入性能比较好

缺点：遍历的性能不是很好

树：在这种情况下就可以利用树，优秀的算法存储结构都是利用了树。比如哈希表

------

### 树的常用术语

- 节点
- 根节点
- 父节点
- 子节点
- 叶子节点（没有子节点的节点）
- 节点权
- 路径（查找节点所走的过程）
- 层
- 子树
- 树的高度

------

### 二叉树

定义：每一个节点只能有两个子节点的树

满二叉树：所有的子节点都满足2n-1这个公式就是满二叉树

------

### 二叉树的遍历

- 前序
- 中序
- 后序

创建树的节点对象

```java
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
}
```

#### 创建根节点

```java
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
}
```

#### 测试代码

```java
BinaryTree binaryTree = new BinaryTree();

HeroNode node1 = new HeroNode(1, "宋江");
HeroNode node2 = new HeroNode(2, "吴用");
HeroNode node3 = new HeroNode(3, "卢俊");
HeroNode node4 = new HeroNode(4, "林冲");
binaryTree.setRoot(node1);
node1.setLeft(node2);
node1.setRight(node3);
node3.setRight(node4);

//前
System.out.println("前");//1,2,3,4
binaryTree.prologue();

//中
System.out.println("中");//2，1，3，4
binaryTree.midOrder();

//后
System.out.println("后");//2，3，4，1
binaryTree.backOrder();
```

#### 结果

```
前
HeroNode{no=1, name='宋江'}
HeroNode{no=2, name='吴用'}
HeroNode{no=3, name='卢俊'}
HeroNode{no=4, name='林冲'}
中
HeroNode{no=2, name='吴用'}
HeroNode{no=1, name='宋江'}
HeroNode{no=3, name='卢俊'}
HeroNode{no=4, name='林冲'}
后
HeroNode{no=2, name='吴用'}
HeroNode{no=3, name='卢俊'}
HeroNode{no=4, name='林冲'}
HeroNode{no=1, name='宋江'}
```

