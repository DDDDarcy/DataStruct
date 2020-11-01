# 二叉查找树

### 二叉查找树 又称 二叉搜索树 或 二叉排序树


###  定义：
言简意赅，就是左右子树非空条件下，满足左小右大，相对于当前节点下。

如下图所示：

![tu](https://github.com/DDDDarcy/DataStruct/blob/main/pict/%E4%BA%8C%E5%8F%89%E6%8E%92%E5%BA%8F.jpg)


对于给定一个无重复数组，转换成二叉查找树，步骤就是创建一个初始根节点```root```,置空初始化，进行依次序插入，直至最后一个元素

完成创建。

#### 下面给出创建代码：
树结点```结构体```：
```
typedef struct Tree
{
    int data;
    struct Tree* left;    //左子树 遵循 非空 即 left->data < data
    struct Tree* right;   //右子树 遵循 非空 即 right->data >data
}TreeNode,*Tree;
```
初始化根节点：
```
Tree initTree(Tree& root)
{
  root = new TreeNode;
  root->left = NULL;
  root->right = NULL;
  root->data = 0;
  return root;
}
```
二叉查找树插入操作：
```
Tree InsertTree(Tree t,int& n)
{
  if(!t){       //找到当前要插入的叶子结点位置
    t = new TreeNode;
    t->data = n;
    t->left = NULL;
    t->right = NULL;
    return t;
 }
 if(t)        //若结点存在则判断大小，指引n应该往左还是右子树前进。
    if(t->data > n)       // n比结点数小，往左走,并且如果创建了新结点会返回给左子树
      t->left = InsertTree(t->left,n);
    else
      t->right = InsertTree(t->right,n);   // n比结点数大，往右走，并且如果创建了新结点会返回给右子树
 return;
}
```

创建操作：
```
Tree CreateBSTree(Tree& tree,int array[], int n)
{ 
    initTree(tree);
    tree = array[0];
    for(int i = 1; i < n; i++)
    {
      InsertTree(tree,array[i]);
    }
    
    return tree;
}
```
