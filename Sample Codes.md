#include<stdio.h>
#include<stdlib.h>

// circular queue using linked list

struct queue{
    int data;
    struct queue *link;
} *front = NULL , *rear = NULL;

void push(int x ){
    struct queue *temp;
    if(front == NULL && rear == NULL){
        temp = (struct queue *)malloc(sizeof(struct queue));
        temp->data = x;
        temp->link = front;
        front = temp;
        rear = temp;
    }
    else{
        temp = (struct queue *)malloc(sizeof(struct queue));
        temp ->data = x;
        temp->link = front;
        rear->link = temp;
        rear = temp;
    }
}

void pop(){
    struct queue *temp;
    if(front==NULL && rear == NULL){
        printf("\n UNNDERFLOW   ");
    }
    else if(front != rear){
        temp = front;
        front = temp->link;
        // printf("\n%d is popped", temp->data);
        free(temp);
        rear->link = front;
    }else{
        // printf("\n%d is popped", front->data);
        free(front);
        front = NULL;
        rear = NULL;
         
    }
}

void display(){
    struct queue *temp ;
    if(front == NULL && rear == NULL){
        printf("\nQUEUE is empty ");
    }
    else {
        temp = front ;
        while(temp != rear){
            printf("\n%d ", temp->data);
            temp = temp->link;
            if(temp==rear){
                printf("\n%d",temp->data);
            }
        }
        
    }
}

void main(){
    display();
    push(10);
    push(20);
    push(30);
    push(40);
    push(50);
    display();
    pop();
    pop();
    pop();
    pop();
    pop();
    display();

}

—---------------------------------------------------------------------------------
// circular queue using array
#include<stdio.h>
#include<stdlib.h>
#define size 5

int queue[size];
int front = -1 , rear = -1;

void push(int x){
    if(front == -1 && rear == -1){
        front = front +1;
        rear = rear + 1;
        queue[rear] = x;
    }
    else if(front != (rear+1)%size){
        rear = (rear+1)%size;
        queue[rear] = x;
    }
    else 
        printf("\nOVERFLOW");
}

void pop(){
    if(front == -1 && rear == -1){
        printf("\n UNDERFLOW");
    }
    else if(rear != (front)%size) {
        printf("\n%d is popped ", queue[front]);
        front = (front+1)%size;
    }
    else{
        printf("\n%d is popped", queue[front]);
        front = -1 ;
        rear =-1;
    }
}

void display(){
    if(front == -1 && rear == -1){
        printf("\nQUEUE is empty ");
    }
    else{
        while(rear != (front)% size){
            printf("\n%d ", queue[front]);
            front = (front+1)%size;
        }
        if(front == rear){
            printf("\n%d ", queue[front]);
            front = (front+1)%size;
        }
}
}
void main(){
    // display();
    push(10);
    push(20);
    push(30);
    push(40);
    push(50);
    push(60);
    display();
    pop();
    push(60);
    pop();
    pop();
    pop();
    pop();
    // pop();
    display();


}

—--------------------------------------------------------------------------------------------------
// queue using linked list
#include<stdio.h>
#include<stdlib.h>

struct Queue{
    int data ;
    struct Queue *link;
}*front = NULL , *rear = NULL;

void push( int x){
    struct Queue *temp;
    if(front == NULL && rear == NULL){
        temp = (struct Queue *)malloc(sizeof(struct Queue));
        temp->data = x;
        temp ->link = NULL;
        front = temp;
        rear = temp;
    }else {
        // temp2 = front ;
        temp = (struct Queue *)malloc(sizeof(struct Queue));
        temp ->data = x;
        rear->link = temp;
        temp->link = NULL;
        rear = temp;
    }

}
void pop(){
    struct Queue *temp;
    if(front == NULL && rear == NULL)
        printf ("\nUNDERFLOW");
    else if (front == rear){
        free(front);
        front = NULL;
        rear = NULL;
    }else{
        temp = front;  //1000
        front = temp->link;  //2000
        free(temp);
    }
}
void display(){
    if(front == NULL && rear == NULL)
        printf ("\nqueue is empty "); 
    else{
        struct Queue *temp = front ;
        while(temp != NULL){
            printf("\n%d ", temp->data);
            temp = temp->link;
        }
    }  
}

void main(){
    push(10);
    push(20);
    push(30);
    push(40);
    push(50);
    display();
    pop();
    pop();
    pop();
    pop();
    pop();
    pop();
    display();
    return ;
}

—-------------------------------------------------------------------------------------------------------
// queue using array
#include<stdio.h>
#include<stdlib.h>

#define size 5

int Queue[size];
int Front = -1;
int Rear = -1;
void push(int x){
    if (Front ==-1 && Rear == -1){
        Front = Front +1; // front = 0 
        Rear = Rear +1; // rear =0
        Queue[Rear] = x; 
    }else if ( Rear < (size-1)){
        Rear = Rear + 1;
        Queue[Rear] = x;
        
    }else {
        printf("\nOVERFLOW ");
    }
}

void pop(){
    if(Front == -1 && Rear == -1){
        printf("\nUNDERFLOW");
    }else if(Front < Rear){
        printf("\n%d is popped", Queue[Front++]);
    }else if(Front ==Rear) {
        printf("\n%d is popped", Queue[Front]);
        Front = -1;
        Rear = -1;
    }
}
void display(){
    if (Front == -1 && Rear == -1){
        printf("\nQueue is empty"); 
    }else {
        for(int i = Front ; i<=Rear;i++){
            printf("\n%d ", Queue[i]);
        }
    }
}
void main(){
    push(10);
    push(20);
    push(30);
    push(40);
    push(50);
    push(60);
    display();
    pop();
    pop();
    pop();
    pop();
    pop();
    pop();
    display();
    return ;
}
—--------------------------------------------------------------------------
// stack using linked list
#include<stdio.h>
#include<stdlib.h>

struct  stack{
    int data;
    struct stack *link;
}*TOP = NULL;

void push(int x){
    struct stack *temp ;
    if(TOP ==NULL){
        temp = (struct stack *)malloc( sizeof(struct stack));
        temp->data = x;
        temp->link = NULL;
        TOP = temp;
    }else{
       
        temp = (struct stack*)malloc(sizeof(struct stack));
        temp->data = x;
        temp->link = TOP;
        TOP = temp;
    }
}
void pop(){
    struct stack *temp;
    if(TOP == NULL)
        printf("\nUNDERFLOW ");
    else{
        temp = TOP;
        TOP = temp->link;
        free(temp);
    }
    
}

void display(){
    struct stack *temp;
    if(TOP== NULL){
        printf("\nstack is empty");
    }else{
        temp = TOP;
        while(temp != NULL){
            printf("\n%d ", temp->data);
            temp = temp->link;
        }
    }
}
void main(){
    display();
    push(10);
    push(20);
    push(30);
    push(40);
    push(50);
    display();
    pop();
    pop();
    pop();
    pop();
    pop();
    display();
}


—------------------------------------------------------------------
// stack using array
#include<stdio.h>
#include<stdlib.h>

#define size 5
int STACK[size];
int Top  = -1;

void push(int x ){ 
    if(Top ==-1)
        printf("STACK is empty !! \n");
    if(Top>=size-1){
        printf("stack in overflow !!\n");
    }else{
        STACK[++Top] = x;
    }

}

void pop(){
    if(Top ==-1)
        printf("stack in underflow !! \n");
    else{
        printf("%d is popped . \n", STACK[Top--]) ;
    }
}

int TOP(){
    return STACK[Top];
}

void main(){
    push(5);
    push(6);
    push(7);
    push(8);
    push(9);    
  
    // printf("The peak element in the stack is =  %d \n", TOP());
    pop();
    pop();
    pop();
    pop();
    pop();
    pop();
        // printf("The peak element in the stack is =  %d  %d \n", TOP() , Top);
    }

—---------------------------------------------------------------------------------------------------
#include<stdio.h>
#include<stdlib.h>

struct doubly{
    int data;
    struct doubly *pre , *next;
};

struct doubly *First = NULL , *Last = NULL;
void insert(int x){
    struct doubly *temp;
       
    if(First ==NULL){
        temp = (struct doubly *)malloc(sizeof(struct doubly));
        temp->data = x;
        temp->pre =First;
        temp->next = Last;
        First = temp;
        Last = temp;
    }
    else{
        temp = Last;
        temp =  (struct doubly*)malloc(sizeof(struct doubly));
        temp->data  =x;
        temp->pre = Last;
        Last->next = temp;
        temp->next = NULL;
        Last = temp;
        Last = temp;
        }


}
void displayfromfirst (){
    struct doubly *temp;
      if(First ==NULL)
        printf("list is empty");
    else{
        temp = First;
        while(temp!=NULL){
            printf("%d \n", temp->data);
            temp = temp->next;
        }
    }
}
void displayfromLast (){
    struct doubly *temp;
      if(Last ==NULL)
        printf("list is empty");
    else{
        temp = Last;
        while(temp!=NULL){
            printf("%d \n", temp->data);
            temp = temp->pre;
        }
    }
}
int main(){
    displayfromfirst();
    displayfromLast();
    insert(10);
    insert(20);
    insert(30);
    insert(40);
    printf("\n list traversal from last\n");
    displayfromLast();
    printf("\n list traversal from first\n");
    displayfromfirst();
    return 0;
}


—---------------------------------------------------------------------------------------------------
#include<stdio.h>
#include<stdlib.h>

// creation a data structure named struct
struct node {
    int data; 
    struct node *link;
} *start = NULL;

//INSERTING A VALUE IN LIST IN BEGINNING 
void insert (int x){
    struct node *ptr ;
    ptr = (struct node *) malloc(sizeof(struct node)); // ptr holds the memory address of new allocated memory of size a struct node
    ptr->data = x ;
    ptr->link = start;
    start = ptr;
}

// PRINT THE DATA OF LIST 
void display (){
    struct node *ptr ;
    if(start == NULL)
        printf("list is empty ! \n");
    else {
        ptr = start;
        while (ptr != NULL){
            printf("%d ", ptr->data);
            ptr = ptr->link;
        }
    }
}

// INSERT VALUE IN LIST AT LAST INDEX
void insert1 (int x){
    struct node *ptr1 , *ptr2 ;
    if(start == NULL){
    ptr1 = (struct node *) malloc(sizeof(struct node)); // ptr holds the memory address of new allocated memory of size a struct node
    ptr1->data = x;
    ptr1->link = NULL;
    start = ptr1;
    }
    else{
        ptr1 = start;
        while(ptr1->link != NULL){
            ptr1 = ptr1->link;
        }
        ptr2 = (struct node *)malloc(sizeof(struct node));
        ptr2->data = x ;
        ptr2->link = NULL;
        ptr1->link = ptr2;
    }
}

// COUNT THE NUMBER OF NODE 
int countNode(){
    int count =0;
    struct node *temp;
    temp = start;
    while (temp != NULL){
        count++;
        temp = temp ->link;
    }
    return count;
}

// INSERT THE ELEMENT AT GIVEN LOCATION 
void insertLoc(int x , int Loc){
    int i =1;
    struct node *new_node , *temp;
    new_node = (struct node *)malloc(sizeof(struct node));
    new_node->data = x;

    if(Loc==1){
    new_node->link = start;
    start = new_node;
    }
    else{
        temp = start;
        while(i <Loc-1){
            temp = temp->link;
            i++;
        }
        new_node->link =temp->link;
        temp->link = new_node;
     
    }
    }
 


void main(){
    insert(5);
    insert(6);
    insert(7);
    // display();
    insert1(12);
    insert1(13);
    insert1(14);
    insertLoc(10 , 1);
    // insertLoc(19 , 3);
    display();
    printf("\n The total number of nodes is = %d ", countNode());

    return ;
}  linked list

