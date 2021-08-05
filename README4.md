# 第三天
### 基础

#### 特点

有序的列表，但是在内存上不是一个连续存储的空间

#### 分类

- 带头节头的链表
- 不带节头的链表
- 每个节点分成两个部分
  1. data部分，这个部分是存储数据的
  2. next是指向下一个节点的对象引用

#### 重点

1. 理解链表的基础创建
2. 链表的结构图
3. 链表的增加，删除，查找，修改等基础操作

------

### 单链表（基础）

#### 创建节点

```java
class HeroNode {
    public int no;          //序列号
    public String name;     //名字
    public String nickName; //外号
    public HeroNode next;   //next指针或者引用
    //构造函数
    public HeroNode(int no,String name,String nickName){
        this.no = no;
        this.name = name;
        this.nickName = nickName;
    }

    @Override
    public String toString() {
        return "HeroNode{" +
                "no=" + no +
                ", name='" + name + '\'' +
                ", nickName='" + nickName + '\'' +
                '}';
    }
}
```

#### 创建头节点类

```java
//头节点
class LinkedList{
    private HeroNode head;
    public LinkedList(){
        head = new HeroNode(0,"","");
    }

    //增加节点
    public void addNode(HeroNode heroNode){
        //判断是否是最后一个
        HeroNode tmpe = head;
        while (true){
            if(tmpe.next == null){
                break;
            }
            //移动
            tmpe = tmpe.next;
        }
        //加入到后面
        tmpe.next = heroNode;
    }

    //显示
    public void showNode(){
        if(head.next == null){
            System.out.println("没有数据");
            return;
        }
        HeroNode tmpe = head;
        while(true){
            if(tmpe.next == null){
                break;
            }
            System.out.println(tmpe);
            tmpe = tmpe.next;
        }
    }
}
```

#### 测试

```java
public class LinkedListDemo {
    public static void main(String[] args) {
        HeroNode heroNode1 = new HeroNode(1,"宋江","及时雨");
        HeroNode heroNode2 = new HeroNode(2,"林冲","豹子头");
        HeroNode heroNode3 = new HeroNode(3,"宋江","及时雨");

        LinkedList linkedList = new LinkedList();
        linkedList.addNode(heroNode1);
        linkedList.addNode(heroNode2);
        linkedList.addNode(heroNode3);

        linkedList.showNode();
    }
}
```

------

#### 插入

思路

1. 找到插入的位置
2. 插入的时候插入节点的next指向后面一个节点的对象
3. 插入前面的对象的next指向插入节点的地址
4. 这个有一个做比较的操作

#### 代码

```java
public void addOrder(HeroNode heroNode){
	//把头节点增加出来
	HeroNode temp = head;
	//定义一个找到重复操作的
	boolean flag = false;
	while(true){
		//没有数据的情况
		if(temp.next == null){
			break;
		}
		//是否是temp的下个节点的编号大于插入进来的
		if(temp.next.no > heroNode.no){
			break;
		}
		else if(temp.next.no == heroNode.no){
			break;
		}
		//非常关键的地方
		temp = temp.next;
	}
	//判断是否有重复情况
	if(flag){
		printf("编号%d已经存在",heroNode.no);
	}else{
		//断开temp.next和temp之间的链接
		temp.next = heroNode.next;
		//链接temp和heroNode
		temp.next = heroNode;
	}
}
```

#### 测试结果

```
编号3已经存在
HeroNode{no=1, name='宋江', nickName='及时雨'}
HeroNode{no=2, name='林冲', nickName='豹子头'}
HeroNode{no=3, name='李逵', nickName='黑旋风'}
```

------

#### 查找

思路

- 传入一个参数知道要找到那个对象比如上面使用唯一的no进行查找
- 返回找到的对象，如果没有找到就返回null

```java
public HeroNode findNode(int no){
	//头节点
	HeroNode temp = head;
	boolean isFind = false;
	while(true){
		if(temp.next == null){
			isFind = false;
			break;
		}
		if(temp.next.no == no){
			isFind = true;
			break;
		}
		temp = temp.next;
	}
	if(isFind){
		return temp.next;
	}
	return null;
}
```

#### 测试

```java
HeroNode heroNode = linkedList.findNode(4);
//修改
if(heroNode != null){
    System.out.println("找到了\n" + heroNode);
}else{
    System.out.println("不存在\n");
}
```

------

#### 删除

思路：删除思路刚好和添加相反

```java
//删除
public boolean delNode(HeroNode heroNode){
  HeroNode temp = head;
  boolean isDel = false;
  while(true){
      if(temp.next == null){
          isDel = false;
          break;
      }
      if(temp.next.no == heroNode.no){
          isDel = true;
          break;
      }
      temp = temp.next;
  }
  if(isDel){
      temp.next = null;//断开
      if(temp.next.next != null){
          temp.next = temp.next.next;
      }
      else{
          temp.next = null;
          heroNode = null;
      }
      return true;
  }
  return false;
}
```

#### 测试

```java
boolean bool = linkedList.delNode(heroNode3);
if(bool){
    System.out.println("删除成功");
}else{
    System.out.println("删除失败");
}
```

------

#### 修改

思路和查找差不多，具体的要主题的时候不能让用户修改no这个属性，如果修改了这个属性一定要判断一下是否链表有重复没有。

------

