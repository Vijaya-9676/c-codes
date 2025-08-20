```
## 1 count of given element in a linked list 
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
```
