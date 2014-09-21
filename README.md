comman-parent-indentifiaction
=============================

#include <stdio.h>
#include <stdlib.h>
 
struct node
{
    int data;
    struct node* left, *right;
};
 

struct node *lca(struct node* root, int n1, int n2)
{
    if (root == NULL) return NULL;
 
    // If both n1 and n2 are smaller than root, then parent lies in left
    if (root->data > n1 && root->data > n2)
        return lca(root->left, n1, n2);
 
    // If both n1 and n2 are greater than root, then parent lies in right
    if (root->data < n1 && root->data < n2)
        return lca(root->right, n1, n2);
 
    return root;
}
 

struct node* make(int data)
{
    struct node* node = (struct node*)malloc(sizeof(struct node));
    node->data  = data;
    node->left  = node->right = NULL;
    return(node);
}
 

int main()
{
	printf("\n");
	

    struct node *root        = make(20);
    root->left               = make(8);
    
    root->left->left         = make(4);
    root->left->right        = make(12);
    root->left->right->left  = make(10);
    root->left->right->right = make(14);
     root->right              = make(22);
	root->right->left    =make(55);
    root->right->right       =make(11);
     root->right->right->left =make(9);

    int n1 = 10, n2 = 14;
 struct node *t = lca(root, n1, n2);
    printf("comman parent of %d and %d is %d \n", n1, n2, t->data);
 
    n1 = 14, n2 = 8;
    t = lca(root, n1, n2);
    printf("comman parent of %d and %d is %d \n", n1, n2, t->data);
 
    n1 = 10, n2 = 22;
    t = lca(root, n1, n2);
    printf("comman parent  of %d and %d is %d \n", n1, n2, t->data);
 
    n1 = 9, n2 = 55;
    t = lca(root, n1, n2);
    printf("comman parent  of %d and %d is %d \n", n1, n2, t->data);
 

    getchar();
    return 0;
}
//end of program
