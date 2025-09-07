# 1.count of given element in a linked list 
```c
#include<stdio.h>
#include<stdlib.h>
struct node
{
        int info;
        struct node *next;
};
struct node *create(int data);
void display(struct node *start);
int countele(struct node *start,int ele);
int main()
{
    struct node *start;
    start=create(1);
    start->next=create(3);
    start->next->next=create(3);
    start->next->next->next=create(4);
    start->next->next->next->next=create(3);
    start->next->next->next->next->next=create(5);
    display(start);
    int count=countele(start,3);
    printf("%d\n",count);
}
struct node *create(int data)
{
        struct node *newnode;
        newnode=(struct node *)malloc(sizeof(struct node));
        newnode->info=data;
        newnode->next=NULL;
        return newnode;
}
void display(struct node *start)
{
        struct node *ptr=start;
        int sum=0;
        while(ptr!=NULL)
        {
                printf("%d -> ",ptr->info);
                sum+=ptr->info;
                ptr=ptr->next;
        }
        printf("NULL\n");
        printf("sum:%d\n",sum);
}
int countele(struct node *start,int ele)
{
  struct node *temp=start;
  int count=0;
  while(temp!=NULL)
  {
          if(ele==temp->info)
         {
                 count++;
         }
         temp=temp->next;
  }
  return count;
}
```

## output 
```
1 -> 3 -> 3 -> 4 -> 3 -> 5 -> NULL
sum:19
3
```
# 2.Merging two linked lists
```
#include<stdio.h>
#include<stdlib.h>
struct node
{
        int info;
        struct node *next;
};
struct node *create(int data);
void display(struct node *start);
struct node *merge(struct node *start1,struct node *start2);
int main()
{
        struct node *start1=create(1);
        start1->next=create(3);
        start1->next->next=create(5);
        start1->next->next->next=create(7);
        start1->next->next->next->next=create(9);

        struct node *start2=create(2);
        start2->next=create(4);
        start2->next->next=create(6);
        start2->next->next->next=create(8);
        start2->next->next->next->next=create(10);

        display(start1);
        display(start2);

        start1=merge(start1,start2);
        display(start1);

}
struct node *create(int data)
{
        struct node *newnode;
        newnode=(struct node *)malloc(sizeof(struct node));
        newnode->info=data;
        newnode->next=NULL;
        return newnode;
}
void display(struct node *start)
{
        struct node *temp=start;
        while(temp)
        {
                printf("%d->",temp->info);
                temp=temp->next;
        }
        printf("NULL\n");
}

struct node *merge(struct node *start1,struct node *start2)
{
        struct node dummy;
        struct node *tail=&dummy;
        dummy.next=NULL;
        while(start1 && start2)
        {
                if(start1->info < start2->info)
                {
                        tail->next=start1;
                        start1=start1->next;
                }
                 else
                {
                        tail->next=start2;
                        start2=start2->next;
                }
                tail=tail->next;
        }
        tail->next=(start1)?start1:start2;
        return dummy.next;
}
```
# output
```
1->3->5->7->9->NULL
2->4->6->8->10->NULL
1->2->3->4->5->6->7->8->9->10->NULL
```
# 3.Reversing a linked list
```c
#include<stdio.h>
#include<stdlib.h>
struct node 
{
        int info;
        struct node *next;
};
struct node *create(int data);
void display(struct node *start);
struct node *reverse(struct node *start);
int main()
{
        struct node *start=create(1);
        start->next=create(2);
        start->next->next=create(3);
        start->next->next->next=create(4);
        start->next->next->next->next=create(5);
        display(start);
        start=reverse(start);
        display(start);
}
struct node *create(int data)
{
        struct node *newnode;
        newnode=(struct node *)malloc(sizeof(struct node));
        newnode->info=data;
        newnode->next=NULL;
        return newnode;
}
void display(struct node *start)
{
        struct node *temp=start;
        while(temp)
        {
                printf("%d->",temp->info);
                temp=temp->next;
        }
        printf("NULL\n");
}
struct node *reverse(struct node *start)
{
        struct node *prev,*ptr,*next=NULL;
        prev=NULL;
        ptr=start;
        while(ptr!=NULL)
        {
                next=ptr->next;
                ptr->next=prev;
                prev=ptr;
                ptr=next;
        }
        return prev;
}
```
# output
```
1->2->3->4->5->NULL
5->4->3->2->1->NULL
```
# 4.Loop creation, detection and removing */
```c
#include<stdio.h>
#include<stdlib.h>
struct node
{       
        int info;
        struct node *next;
};
struct node *create(int data);
void display(struct node *start);
int detectloop(struct node *start);
struct node removeloop(struct node *start);
int main()
{
        struct node *start=create(1);
        start->next=create(2);
        start->next->next=create(3);
        start->next->next->next=create(4);
        start->next->next->next->next=create(5);
        start->next->next->next->next->next=create(6);
        display(start);
        start->next->next->next->next->next=start->next->next;
        if(detectloop(start))
        {
                printf("Loop detected\n");
        }
        else
        {
                printf("No loop detected\n");
        }
        removeloop(start);
        display(start);
}
struct node *create(int data)
{
        struct node *newnode=(struct node *)malloc(sizeof(struct node));
        newnode->info=data;
        newnode->next=NULL;
        return newnode;
}
void display(struct node *start)
{
        struct node *temp=start;
        while(temp)
        {
                printf("%d->",temp->info);
                temp=temp->next;
        }
        printf("NULL\n");
}
int detectloop(struct node *start)
{
        struct node *slow=start,*fast=start;
        while(slow && fast && fast->next)
        {
                slow=slow->next;
                fast=fast->next->next;
                if(slow==fast)
                {
                        return 1;
                }
        }
        return 0;
}
struct node removeloop(struct node *start)
{
        struct node *slow=start,*fast=start;
        while(slow && fast && fast->next)
        {
                slow=slow->next;
                fast=fast->next->next;
                if(slow==fast)
                {
                        printf("Loop detected at node %d\n",slow->info);
                        slow=start;
                        while(slow != fast)
                        {
                                slow=slow->next;
                                fast=fast->next;
                        }
                        printf("start of the loop is at node %d\n",slow->info);
                        struct node *ptr=slow;
                        while(ptr->next != slow)
                        {
                                ptr=ptr->next;
                        }
                        ptr->next=NULL;
                        printf("Loop removed\n");
                        return;
                }
        }
        printf("No loop detected\n");
}
```
# output
```
1->2->3->4->5->6->NULL
Loop detected
Loop detected at node 4
start of the loop is at node 3
Loop removed
1->2->3->4->5->NULL
```
# 5.Printing large and small elements in a linked list
```c
#include<stdio.h>
#include<stdlib.h>
struct node
{
        int info;
        struct node *next;
};
struct node *create(int data);
void display(struct node *start);
void minmax(struct node *start,int *large,int *small);
int main()
{
        struct node *start;
        start=create(40);
        start->next=create(30);
        start->next->next=create(60);
        start->next->next->next=create(20);
        start->next->next->next->next=create(70);
        start->next->next->next->next->next=create(10);
        display(start);
        int large,small;
        minmax(start,&large,&small);
        printf("Large:%d\tsmall:%d\n",large,small);
}
struct node *create(int data)
{
        struct node *newnode;
        newnode=(struct node *)malloc(sizeof(struct node));
        newnode->info=data;
        newnode->next=NULL;
        return newnode;
}
void display(struct node *start)
{
        int count=0;
        struct node *ptr=start; 
        while(ptr!=NULL)
        {
                printf("%d->",ptr->info);
                ptr=ptr->next;
                count++;
        }
        printf("NULL\n");
        printf("length of list is:%d\n",count);
}
void minmax(struct node *start,int *large,int *small)
{
        *large=start->info;
        *small=start->info;
         struct node *temp=start->next;
         while(temp!=NULL)
         {
                 if(temp->info > *large)
                 {
                         *large=temp->info;
                 }
                 else if(temp->info < *small)
                 {
                         *small=temp->info;
                 }
                 temp=temp->next;
         }
}
```
# output
```
40->30->60->20->70->10->NULL
length of list is:6
Large:70	small:10
```
# 6.Creating a copy of a linked list or clone of a single linked list
```c
#include<stdio.h>
#include<stdlib.h>
struct node
{
        int info;
        struct node *next;
};
struct node *create(int data);
void display(struct node *start);
struct node *copylist(struct node *start);
int main()
{
        struct node *start;
        start=create(10);
        start->next=create(20);
        start->next->next=create(30);
        start->next->next->next=create(40);
        printf("Original list:");
        display(start);
        printf("Copied list:");
        display(copylist(start));
}
struct node *create(int data)
{
        struct node *newnode;
        newnode=(struct node*)malloc(sizeof(struct node));
        newnode->info=data;
        newnode->next=NULL;
        return newnode;
}
void display(struct node *start)
{
        struct node *temp=start;
        while(temp!=NULL)
        {
                printf("%d->",temp->info);
                temp=temp->next;
        }
        printf("NULL\n");
}
struct node *copylist(struct node *start)
{
        struct node *newstart=create(start->info);
        struct node *original=start->next;
        struct node * copy=newstart;
        while(original != NULL)
        {
                copy->next=create(original->info);
                copy=copy->next;
                original=original->next;
        }
        return newstart;
}
```
# output
```
Original list:10->20->30->40->NULL
Copied list:10->20->30->40->NULL
```
# 7.Moving the largest element to the end of the linked list
```
#include<stdio.h>
#include<stdlib.h>
struct node
{
        int info;
        struct node *next;
};
struct node *create(int data);
void display(struct node *start);
struct node *maxend(struct node * start);
int main()
{
        struct node * start=create(10);
        start->next=create(40);
        start->next->next=create(51);
        start->next->next->next=create(20);
        display(start);
        start=maxend(start);
        display(start);
}
struct node *create(int data)
{
        struct node *newnode=(struct node *)malloc(sizeof(struct node));
        newnode->info=data;
        newnode->next=NULL;
        return newnode;
}
void display(struct node *start)
{
        struct node *temp=start;
        while(temp != NULL)
        {
             printf("%d->",temp->info);
                temp=temp->next;
        }
        printf("NULL\n");
}
struct node *maxend(struct node *start)
{
        struct node *curr=start;
        struct node *later=curr->next;
        while(later != NULL)
        {
                if(curr->info > later -> info)
                {
                        int temp=curr->info;
                        curr->info=later->info;
                        later->info=temp;
                }
                later=later->next;
                curr=curr->next;
        }
        return start;
}
```
# output
```
10->40->51->20->NULL
10->40->20->51->NULL
```

                




