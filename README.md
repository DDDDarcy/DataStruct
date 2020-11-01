# DataStruct
基本数据结构
```
int nodedepth(Tree t, int n)
{
  if(!t) return 0;
  if(t->left == NULL && t->right == NULL)
    printf("level:%d,data:%c",n,t->data);
  nodedepth(t->left,n+1);
  nodedepth(t->right,n+1);
  return 0;
}
```
