## Double pointers (type_t**)
主要是举了一个从单向链表里删除元素的函数的例子
感觉他有个地方写错了，我重新写一个
```C
typedef struct node_t node_t;
struct node_t {
    int32_t data;
    node_t* next;
}
// reuturn 0 on success, -1 on failure
int32_t delete_node(node_t** head, note_t* remove) {
    for (node_t** find=head; *find->next!=remove; find=&(*find)->next) {
        if (*find->next==NULL) return -1;
    }
    *find->next=remove->next;
    // if needed, free the memory of remove
    return 0;
})
```
想想看如果不用double pointer会咋样
```C
int32_t delete_node(node_t* head, node_t* remove) {
    for (node_t* find=head; find->next!=remove; find=find->next) {
        if (find->next==NULL) return -1;
    }
    find->next=remove->next;
    // if needed, free the memory of remove
    return 0;
})
```
> 所以为什么不行？？？



## Error Taxonomy
- Specification ambiguity $\leftarrow$ can be very challenging; spec says nothing about what to do, so people tend to make different assumptions, and those assumptions are incompatible.
- Algorithmic error $\leftarrow$ usually harder; programmer didn't think of some kinds of inputs, so the algorithm chosen doesn't actually work for everything.
- Semantic error $\leftarrow$ ok with compiler, but not what you meant to write
- Syntax errors $\leftarrow$ simple mis-expressions, cautht by compiler


## BST example
```C
typedef struct BST_Node BST_Node;
struct BST_Node {
    int32_t key; // key value for this node
    BST_Node* left; // left child
    BST_Node* right; // right child
};
int32_t BST_insert (BST_Node** rptr, int32_t value) { 
    if (NULL = *rptr) {
        *rptr = (BST_Node*)malloc(sizeof(BST_Node));
        if (NULL == *rptr) {
            return 0;
        }
        (*rptr)->value = value;
        (*rptr)->left = NULL;
        (*rptr)->right = NULL;
    }
    // WIP
}

```