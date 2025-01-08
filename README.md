1a. #include <stdio.h>
    #include <stdlib.h>
    #define SIZE 5
 
void push();
int pop();
void display();
 
int s[SIZE], i, top = -1, ch, item, item_deleted;
 
void main() 
{
    while (1)
	  {
        printf("1. push   2. pop   3. display   4. exit\n");
        scanf("%d", &ch);
        switch (ch) 
        {
            case 1: push();break;
            case 2: pop(); break;
            case 3: display(); break;
            case 4: exit(0);
            default: printf("Invalid choice, please try again.\n");
        }
    }
}
 
void push() 
{
    if (top == SIZE - 1)
        printf("Stack is Full\n");
    else 
    {
        printf("Enter the element to insert\n");
        scanf("%d", &item);
        top = top + 1;
        s[top] = item;
    }
}
 
int pop() {
    if (top == -1) 
    {
        printf("Stack is empty\n");
        return -1;
    } 
    else 
    {
        int deleted_item = s[top];
        top--;
        printf("Item deleted = %d\n", deleted_item);
        return deleted_item;
    }
}
 
void display() 
{
    if (top == -1) 
    {
        printf("Stack is empty\n");
    } 
    else 
    {
        printf("Contents of stack:\n");
        for (i = 0; i <= top; i++) 
        {
            printf("%d\t", s[i]);
		    }
    }
}
1b. #include<stdio.h>
#include<string.h>
#include <ctype.h>
 
char stack[50];
char infix[20];
char postfix[20];
int top=-1,i=0,j=0;
 
void push(char x)
{
    top++; 
    stack[top] = x;
}
 
int pop()
{
    return(stack[top--]);
}
 
int prior(char x)
{
    int p;
    if(x=='('||x=='#') p=1;
    if(x=='+'||x=='-') p=2;
    if(x=='*'||x=='/') p=3;
    if(x=='^'||x=='$') p=4;
    return p;
}
 
void main()
{
    printf("Enter an infix expression:\n");
    scanf("%s", infix);
    push('#');
    for(i=0;i<strlen(infix);i++)
    {
        if(isalnum(infix[i]))
            postfix[j++]=infix[i];
        else if(infix[i]=='(')
            push(infix[i]);
        else if(infix[i]==')')
        {
            while(stack[top]!='(')
	            postfix[j++]=pop();
            pop();
        }
        else
        {
        while(prior(stack[top])>=prior(infix[i]))
            postfix[j++]=pop();
        push(infix[i]);
        }
    }
    while(stack[top]!='#')
        postfix[j++]=pop();
    postfix[j]='\0';
    printf("\nPostfix expression is:\n");
    printf("%s",postfix);
}
2a. #include<stdlib.h>
#include<stdio.h>
#define SIZE 5
 
void qinsert(int, int*, int[]);
void qdelete(int*, int*, int[]);
void display(int, int, int[]);
 
void main() 
{
    int q[SIZE], rear = -1, front = 0, item, ch;
    while (1)
    {
        printf("\n1: INSERT  2: DELETE  3: DISPLAY  Otherwise EXIT\n");
        scanf("%d", &ch);
        switch (ch) 
        {
            case 1:
                printf("Enter the element:\n");
                scanf("%d", &item);
                qinsert(item, &rear, q);
                break;
 
            case 2: qdelete(&rear, &front, q);
                break;
 
            case 3:
                display(front, rear, q);
                break;
 
            default:
                printf("Invalid operation\n");
                exit(0);
        }
    }
}
 
void qinsert(int item, int *rear, int q[]) {
    if (*rear == SIZE - 1) {
        printf("Queue is Full\n");
    } else {
        *rear = *rear + 1;
        q[*rear] = item;
    }
}
 
void qdelete(int *rear, int *front, int q[]) {
    if (*front > *rear) {
        printf("Queue is Empty\n");
    } else {
        printf("The deleted element is %d\n", q[*front]);
        *front = *front + 1;
    }
}
 
void display(int front, int rear, int q[]) {
    if (front > rear) {
        printf("Queue is Empty\n");
    } else {
        printf("The status of Queue:\n");
        for (int i = front; i <= rear; i++) {
            printf("Queue[%d] = %d\n", i, q[i]);
        }
    }
}
2b.#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#define SIZE 10
 
struct queue
{
    int front;
    int rear;
    char data[SIZE][100];
};
 
int send(struct queue* q, char message[]) // Replaced 'info' with 'message'
{
    if(q->rear - q->front == SIZE)
    {
        printf("Queue is full\n\n");
        return 0;
    }
 
    strcpy(q->data[q->rear % SIZE], message); 
    printf("SENT: %s\n\n", q->data[q->rear % SIZE]);
    q->rear += 1;
    return 1;
}
 
int recieve(struct queue* q)
{
    if(q->rear - q->front == 0)
    {
        printf("Queue is Empty\n\n");
        return 0;
    }
 
    printf("RECIEVED: %s\n\n", q->data[q->front % SIZE]);
    q->front += 1;
    return 1;
}
 
int display(struct queue *q)
{
    printf("\nCONTENTS:\n");
    if (q->front == q->rear)
    {
        printf("Queue is Empty\n");
        return 0;
    }
    for (int i = q->front; i < q->rear; i++)
    {
        printf("%s\n", q->data[i % SIZE]);
    }
    return 1;
}
 
int main()
{
    int in;
    char message[100];
    struct queue* q = (struct queue*)malloc(sizeof(struct queue));
    q->front = 0;
    q->rear = 0;
 
    while (1)
    {
        printf("\n1. Send\n2. Recieve\n3. Display\nEnter your choice: ");
        scanf("%d", &in);
 
        switch (in)
        {
            case 1: 
                printf("Enter the message: ");
                scanf("%s", message);
                send(q, message); // Directly pass 'message'
                break;
            case 2: 
                recieve(q);
                break;
            case 3: 
                display(q);
                break;
            default:
                printf("Exiting..\n");
                return 0;
        }
    }
}
3a. #include<stdio.h>
#include<stdlib.h>
 
struct node {
    int info;
    struct node *link;
}; typedef struct node * NODE;
 
NODE head = NULL;
 
// Insert at a specific position
void insert_at_position() {
    int pos, i;
    NODE temp, cur = head;
    temp = (NODE)malloc(sizeof(struct node));
    temp->link = NULL;
 
    printf("\nEnter the position: ");
    scanf("%d", &pos);
    printf("\nEnter the data: ");
    scanf("%d", &temp->info);
 
    if(pos == 1) 
    { // Insert at the beginning
        temp->link = head;
        head = temp;
        return;
    }
 
    for(i = 1; i < pos - 1 && cur != NULL; i++) 
    { 
        cur = cur->link;
    }
 
    temp->link = cur->link; // Insert in the middle or at the end
    cur->link = temp;
}
 
void delete_front() 
{
    NODE temp;
    if(head == NULL)
    {
        printf("\nList is empty\n");
        return;
    }
    temp = head;
    head = head->link;
    printf("\nDeleted element is %d\n", temp->info);
    free(temp);
}
 
// Display the list
void display() {
    NODE cur = head;
    if(head == NULL) {
        printf("\nList is empty\n");
        return;
    }
    printf("\nList elements are: ");
    while(cur != NULL) {
        printf("%d\t", cur->info);
        cur = cur->link;
    }
    printf("\n");
}
 
void main() {
    int ch;
    for(;;) {
        printf("\n1. Insert at specific position\n2. Delete from beginning\n3. Display\n4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &ch);
        switch(ch) {
            case 1: insert_at_position(); break;
            case 2: delete_front(); break;
            case 3: display(); break;
            case 4: exit(0);
            default: printf("\nInvalid choice\n");
        }
    }
}
3b.#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
struct node
{
    int data;
    struct node *link;
}; typedef struct node *NODE;
 
NODE convert(char *number)
{
    NODE head=NULL;
    for (int i=0; i<strlen(number); i++)
    {
        NODE root= (NODE) malloc(sizeof(struct node));
        root->data= number[i]-'0';
        root->link=head;
        head=root;
    }
    return head;
}
 
NODE add(NODE head1, NODE head2)
{
    int carry=0;
    NODE head=NULL;
 
    while (head1!=NULL || head2!=NULL || carry!=0)
    {
        int sum=carry;
 
        if (head1!=NULL)
        {
            sum=sum+ head1->data;
            head1= head1->link;
        }
 
        if (head2!=NULL)
        {
            sum=sum+ head2->data;
            head2= head2->link;
        }
 
        NODE root= (NODE) malloc(sizeof(struct node));
        root->data=sum %10;
        root->link= head;
        head=root;
 
        carry = sum / 10;
    }
    return head;
}
 
void display(NODE head)
{
    NODE cur=head;
    if (cur==NULL)
    {
        printf("The list is empty");
        return;
    }
    while (cur!=NULL)
    {
        printf("%d", cur->data);
        cur=cur->link;
    }
}
 
int main()
{
    char number1[100], number2[100];
 
    printf("Enter the first number");
    scanf("%s", number1);
    printf("Enter the second number");
    scanf("%s", number2);
 
    NODE head1= convert(number1);
    NODE head2=convert(number2);
 
    NODE result= add(head1, head2);
 
    display(result);
 
    return 0;
}
4a.#include <stdio.h>
#include <stdlib.h>
 
struct node
{
    int info;
    struct node *prev;
    struct node *next;
}; typedef struct node *NODE;
 
NODE head = NULL;
 
void insert_at_front()
{
    NODE temp = (NODE)malloc(sizeof(struct node));
    printf("Enter the element to insert at the front: ");
    scanf("%d", &temp->info);
    temp->prev = NULL;
    temp->next = head;
 
    if (head != NULL) 
        head->prev = temp;
 
    head = temp;  // Move the head pointer to the new node
}
 
void delete_node()
{
    int data;
    NODE cur = head;
    printf("Enter the data to delete: ");
    scanf("%d", &data);
 
    while (cur != NULL && cur->info != data)
        cur = cur->next;
 
    if (cur == NULL)  // If the node is not found
    {
        printf("Node with data %d not found!\n", data);
        return;
    }
 
    // If the node is found, adjust the pointers to remove it
    if (cur->prev != NULL)
        cur->prev->next = cur->next;
    else
        head = cur->next;  // If the node to delete is the first node, update head
 
    if (cur->next != NULL)
        cur->next->prev = cur->prev;
 
    free(cur);  // Free the memory of the deleted node
    printf("Node with data %d deleted successfully.\n", data);
}
 
void display()
{
    NODE cur = head;
    if (head == NULL)
    {
        printf("The list is empty.\n");
        return;
    }
 
    printf("The contents of the doubly linked list are:\n");
    while (cur != NULL)
    {
        printf("%d <-> ", cur->info);
        cur = cur->next;
    }
    printf("NULL\n");
}
 
int main()
{
    int ch;
    while (1)
    {
        printf("1. Insert at front  2. Delete a node  3. Display  4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &ch);
        switch(ch)
        {
            case 1: insert_at_front(); break;
            case 2: delete_node(); break;
            case 3: display(); break;
            case 4: exit(0); break;
            default: printf("Invalid choice! Please try again.\n"); break;
        }
    }
    return 0;
}
4b. #include <stdio.h>
#include <stdlib.h>
 
struct node
{
    int row,col, data;
    struct node *link;
}; typedef struct node *NODE;
 
NODE insert_at_end(NODE head, int row, int col, int data)
{
    NODE temp;
    temp=(NODE) malloc(sizeof(struct node));
    temp->row=row;
    temp->col=col;
    temp->data=data;
    temp->link=NULL;
 
    if (head==NULL)
        return temp;
 
    NODE cur=head;
    while (cur->link!=NULL)
    {
        cur=cur->link;
    }
 
    cur->link=temp;
 
    return head;
}
 
NODE display(NODE head, int row, int col)
{
    int i, j;
    NODE temp=head;
 
    for(i=1; i<=row; i++)
    {
        for(j=1; j<=col; j++)
        {
            if(temp!=NULL && temp->row==i && temp->col==j)
            {
                printf("%d\t", temp->data);
                temp=temp->link;
            }
            else
            {
                printf("0\t");
            }
        }
        printf("\n");
    }
}
 
int main()
{
    int row, col, m, n, num, i, item;
    NODE head=NULL;
 
    printf("ENter the order of matrix (m and n):");
    scanf("%d%d", &m, &n);
 
    printf("ENter number of non zero entries:");
    scanf("%d",&num);
 
    for (i=1; i<=num; i++)
    {
        printf("enter the row index");
        scanf("%d", &row);
        printf("enter the col index");
        scanf("%d", &col);
        printf("enter the element");
        scanf("%d", &item);
        head=insert_at_end(head,row,col,item);
    }
 
    display(head, m, n);
    return 0;
}
5a. #include <stdio.h>
#include <stdlib.h>
#define SIZE 10
 
int a[SIZE], n=0, c=0, p=-1;
 
void bst(int ele)
{
    if (n==0)
    {
        a[0]=ele;
        n++;
        return;
    }
 
    c=0;  (---------------------------NEW-------)
    while (c< SIZE && a[c]!=-1)
    {
        p=c;
        if (ele<a[c])
            c=2*c+1;
        else
            c=2*c+2;
        if (c>=SIZE) break;
    }
 
    if (ele< a[p])
        a[2*p+1]=ele;
    else
        a[2*p+2]=ele;
    n++;
}
 
void display()
{
    int i;
    for (i=0; i <SIZE; i++)
    {
        if (a[i]!=-1) (---------------------------NEW-------)
        {
            printf("a[%d]= %d\n", i, a[i]);
        }
    }
}
 
 
void main()
{
    int ch, i, j, ele;
 
    for (i=0; i<SIZE; i++)
        a[i]=-1; (---------------------------NEW-------)
 
    while(1)
    {
        printf("1. creation of bst     2. displaying it");
        scanf("%d", &ch);
        switch(ch)
        {
            case 1: printf("enter the number of elements");
                    scanf("%d", &j);
                    for (i=0; i<j;i++)
                    {
                        scanf("%d", &ele);
                        bst(ele);
                    }
                    break;
 
            case 2: display(); break;
            default: printf("Exiting the program");
 
        }
    }
}
5b.#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
 
struct node
{
    char info;
    struct node *left;
    struct node *right;
}; typedef struct node *NODE;
 
struct stack
{
    int top;
    NODE data[10];
}; typedef struct stack STACK;
 
int preced(char item)
{
    switch(item)
    {
        case '^': return 5;
        case '*': 
        case '/': return 3;
        case '+': 
        case '-': return 1;
        default: return 0;
    }
}
 
void preorder(NODE root)
{
    if (root!=NULL)
    {
        printf("%c\t", root->info);
        preorder(root->left);
        preorder(root->right);
    }
}
 
void inorder(NODE root)
{
    if (root!=NULL)
    {
        inorder(root->left);
        printf("%c\t", root->info);
        inorder(root->right);
    }
}
 
void postorder(NODE root)
{
    if (root!=NULL)
    {
        postorder(root->left);
        postorder(root->right);
        printf("%c\t", root->info);
    }
}
 
void push(STACK *s, NODE temp)
{
    s->top=s->top+1;
    s->data[s->top]=temp;
}
 
NODE pop(STACK *s)
{
    NODE val=s->data[s->top];
    s->top=s->top-1;
    return val;
}
 
NODE createnode(char item)
{
    NODE temp;
    temp=(NODE) malloc (sizeof(struct node));
    temp->info=item;
    temp->left=NULL;
    temp->right=NULL;
    return temp;
}
 
NODE createEXPTree(char expr[20])
{
    STACK operator, tree;
    tree.top=-1;
    operator.top=-1;
    char symbol;
    int i;
    NODE temp, t, r, l;
 
    for (i=0; expr[i]!='\0'; i++)
    {
        symbol=expr[i];
        temp=createnode(symbol);
        if (isalnum(symbol))
            push(&tree, temp);
        else
        {
            if (operator.top==-1)
            {
                push(&operator, temp);
            }
            else 
            {
                while( operator.top!=-1 && preced((operator.data[operator.top])-> info) >= preced(symbol))
                {
                    t=pop(&operator);
                    r=pop(&tree);
                    l=pop(&tree);
                    t->right= r;
                    t->left=l;
                    push(&tree, t);
                }
                push(&operator, temp);
            }
        }
    }
 
    while (operator.top!=-1)
    {
        t=pop(&operator);
        r=pop(&tree);
        l=pop(&tree);
        t->right= r;
        t->left=l;
        push(&tree, t);
    }
    return pop(&tree);
}
 
int main()
{
    NODE root=NULL;
    char expr[20];
    printf("\n enter infix expression");
    scanf("%s", expr);
    root= createEXPTree(expr);
    printf("pre");
    preorder(root);
    printf("post");
    postorder(root);
    printf("in");
    inorder(root);
    return 0;
}
6a.#include <stdio.h>
#include <stdlib.h>
 
struct node
{
    int data;
    struct node *right;
    struct node *left;
}; typedef struct node *NODE;
 
NODE createBST(NODE root, int);
void preorder(NODE root);
void postorder(NODE root);
void inorder(NODE root);
 
void main()
{
    NODE root=NULL;
    int ele, ch, i, n;
 
    while (1)
    {
        printf("1. create   2.pre  3. post    4. in");
        scanf("%d", &ch);
        switch(ch)
        {
            case 1: printf("Enter the number of nodes");
                    scanf("%d", &n);
                    printf("Enter the elements");
                    for (i=0; i<n; i++)
                    {
                        scanf("%d", &ele);
                        root=createBST(root, ele);
                    }
                    break;
 
            case 2: printf("The preorder traversal is: ");
                    preorder(root); 
                    break;
 
            case 3: printf("The postorder traversal is: ");
                    postorder(root); 
                    break;
 
            case 4: printf("The inorder traversal is: ");
                    inorder(root); 
                    break;
 
            default: printf("this is an invalid option");
        }
    }
}
 
NODE createBST(NODE root, int ele)
{
    if (root==NULL)
    {
        NODE root=(NODE) malloc (sizeof(struct node));
        root->data=ele;
        root->left=NULL;
        root->right=NULL;
        return root;
    }
 
    else
    {
        if (ele< root->data)
        {
            root->left=createBST(root->left, ele);
        }
        else if (ele> root->data)
        {
            root->right=createBST(root->right, ele);
        }
        else
            printf("duplicates not allowed");
        return root;
    }
}
 
void preorder(NODE root)
{
    if (root!=NULL)
    {
        printf("%d", root->data);
        preorder(root->left);
        preorder(root->right);
    }
}
 
void postorder(NODE root)
{
    if (root!=NULL)
    {
 
        postorder(root->left);
        postorder(root->right);
        printf("%d", root->data);
    }
}
void inorder(NODE root)
{
    if (root!=NULL)
    {
 
        inorder(root->left);
        printf("%d", root->data);
        inorder(root->right);
    }
}
6b. #include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
struct node
{
    int emp_id;
    char name[50];
    char login[20];
    struct node *left;
    struct node *right;
}; typedef struct node *NODE;
 
NODE createBST(NODE root, int emp_id, char *name, char *login);
void inorder(NODE root);
 
void main()
{
    NODE root=NULL;
    int ch, n, i, emp_id;
    char name[50], login[20];
 
    printf("Enter the number of employees");
    scanf("%d", &n);
 
    for (i=0; i<n; i++)
    {
        printf("Enter the emp id\n");
        scanf("%d", &emp_id);
        printf("Enter the name\n");
        scanf("%s", name);
        printf("Enter the login time\n");
        scanf("%s", login);
        root=createBST(root, emp_id, name, login);
    }
 
    printf("the report in ascending order is: \n");
    inorder(root);
}
 
NODE createBST(NODE root, int emp_id, char *name, char *login)
{
    if (root==NULL)
    {
        root= (NODE) malloc(sizeof(struct node));
        root->emp_id=emp_id;
        strcpy(root->name,name);
        strcpy(root->login,login);
        root->left=NULL;
        root->right=NULL;
        return root;
    }
    else
    {
        if(emp_id < root->emp_id)
            root->left=createBST(root->left, emp_id, name, login);
        if(emp_id > root->emp_id)
            root->right=createBST(root->right, emp_id, name, login);
        else
            printf("duplicate values not allowed");
        return root;
    }
}
 
void inorder(NODE root)
{
    if (root!=NULL)
    {
        inorder(root->left);
        printf("Emp_id= %d    Name= %s          Login Time=%s", root->emp_id, root->name, root->login);
        inorder(root->right);
    }
}