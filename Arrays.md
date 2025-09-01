# 1.Swapping adjacent elements of an array
```c
#include<stdio.h>
int main()
{
int a[10]={1,2,3,4,5,6,7,8,9,0};
int temp;
int i,j;
for(i=0;i<10;i+=2)
{
temp=a[i];
a[i]=a[i+1];
a[i+1]=temp;
}
for(j=0;j<10;j++)
{
printf("%d ",a[j]);
}
printf("\n");
}
```
# output
```c
2 1 4 3 6 5 8 7 0 9
```
# 2.Finding large and second large
```c
#include<stdio.h>
int main()
{
int a[10]={1,52,3,4,5,46,7,8,19,100};
int i,large,secondlarge;
large=secondlarge=a[0];
for(i=1;i<10;i++)
{
if(a[i]>large)
{
secondlarge=large;
large=a[i];
}
else if(a[i]>secondlarge && a[i]<large){
secondlarge=a[i];
}
}
printf("%d %d\n",large,secondlarge);
}
```
# output
```c
100 52
```
# 3.Swap a part of an array
```c
#include<stdio.h>
int func(int arr[],int n);
int main()
{
int arr[10]={12,4,55,6,7,8,23,55,32,44};
int n=5;
func(arr,n);
}
int func(int arr[],int n)
{
int temp,j,k,i;
for(i=0,j=n-1;i<n,j>n/2;i++,j--)
{
temp=arr[i];
arr[i]=arr[j];
arr[j]=temp;
}
for(k=0;k<10;k++)
{
printf("%d ",arr[k]);
}
printf("\n");
}
```
# output
```
7 6 55 4 12 8 23 55 32 44 
```
# 4.Selection sort
```c
#include<stdio.h>
int main()
{
int arr[5]={12,23,54,4,3};
int temp,min,i,j;
for(i=0;i<4;i++)
{
min=i;
for(j=i+1;j<5;j++)
{
if(arr[min]>arr[j])
{
min=j;
}
}
if(i!=min)
{
temp=arr[i];
arr[i]=arr[min];
arr[min]=temp;
}
}
for(i=0;i<5;i++)
{
printf("%d ",arr[i]);
}
printf("\n");
}
```
# output
```
3 4 12 23 54
```
# 5.Insertion sort
```c
#include<stdio.h>
int main()
{
int arr[8]={3,6,2,5,9,24,45,67};
int i,n=8,j,k;
for(int i=1;i<n;i++)
{
k=arr[i];
for(j=i-1;j>=0 && arr[j]>k;j--) {
arr[j+1]=arr[j];
}
arr[j+1]=k;
}
for(i=0;i<n;i++)
{
printf("%d ",arr[i]);
}
printf("\n");
}
```
# output
```
2 3 5 6 9 24 45 67
```
# 6.Bubble sort
```c
#include<stdio.h>
int main()
{
int arr[10]={33,23,54,65,12,32,14,55,87,44};
int temp,n=10,i,j,flag;
for(i=0;i<n-1;i++)
{
flag=0;
for(j=i+1;j<n-i-1;j++)
{
if(arr[j]>arr[j+1])
{
temp=arr[j];
arr[j]=arr[j+1];
arr[j+1]=temp;
flag=1;
}
}
if(flag==0)
{
break;
}
}
for(i=0;i<n;i++)
{
printf("%d ",arr[i]);
}
printf("\n");
}
```
# output
```
12 14 23 32 33 44 54 55 65 87 
```
# 7.Removing duplicates from an unsorted array
```c
#include<stdio.h>
int main()
{
int n=10;
int arr[10]={12,34,56,73,12,11,34,67,89,23};
int k,i,j;
for(i=0;i<n-1;i++)
{
for(j=i+1;j<n;j++)
{
if(arr[i]==arr[j])
{
for(k=j;k<n;k++)
{
arr[k]=arr[k+1];
}
n--;
}
}
}
for(i=0;i<n;i++)
{
printf("%d ",arr[i]);
}
}
```
# output
```
12 34 56 73 11 67 89 23
```
# 8.Removing duplicates from a sorted array
```c
#include<stdio.h>
int main()
{
int arr[10]={1,2,33,33,34,55,66,78,86,90};
int n=10;
int k,i,j;
for(i=0;i<n;i++)
{
if(arr[i]==arr[i+1])
{
for(k=i;k<n;k++)
{
arr[k]=arr[k+1];
}
n--;
}
}
for(i=0;i<n;i++)
{
printf("%d ",arr[i]);
}
}
```
# output
```
1 2 33 34 55 66 78 86 90
```
# 9.No.of inversions in an array
```c
#include<stdio.h>
int main()
{
int arr[5]={4,9,2,8,7};
int n=5,count,i,j;
for(i=0;i<n-1;i++)
{
for(j=i+1;j<n;j++)
{
if(arr[i]>arr[j])
{
printf("(%d,%d)  ",arr[i],arr[j]);
count+=1;
}
}
}
printf("%d\n",count);
}
```
# output
```
(4,2)  (9,2)  (9,8)  (9,7)  (8,7)  5
```
# 10.Frequently repeated element in a sorted array
```c
#include<stdio.h>
int main()
{
int arr[8]={1,1,2,2,2,3,3,4};
int n=8;
int maxcount=0,count=1,mostfrequent=arr[0];
for(int i=1;i<n;i++)
{
if(arr[i]==arr[i-1])
{
count++;
}
else
{
count=1;
}
if(count>maxcount) {
maxcount=count;
mostfrequent=arr[i];
}
}
printf("%d \n",mostfrequent);
}
```
# output 
```
2
```
# 11.Finding all the leader elements in an array
```c
#include<stdio.h>
int lead(int arr[],int n);
int main()
{
int arr[7]={2,4,9,6,3,5,2};
int n=7;
lead(arr,7);
}
int lead(int arr[],int n)
{
int i,leader=arr[n-1];
printf("%d ",leader);
for(i=n-2;i>=0;i--)
{
if(arr[i]>leader)
{
leader=arr[i];
printf("%d ",leader);
}
}
}
```
# output
```
2 5 6 9
```
# 12.Sorting a matrix row wise
```c
#include<stdio.h>
int main()
{
        int rows=3,cols=4;
        int arr[3][4]={{11,1,5,7},{10,7,15,3},{11,12,8,6}};
        int i,j,temp,row;
        for(row=0;row<rows;row++)
        {
                for(i=0;i<cols-1;i++)
                {
                        for(j=0;j<cols-i-1;j++)
                        {
                                if(arr[row][j]>arr[row][j+1])
                                {
                                        temp=arr[row][j];
                                        arr[row][j]=arr[row][j+1];
                                        arr[row][j+1]=temp;
                                }
                        }
                }
        }
        for(i=0;i<rows;i++)
        {
                for(j=0;j<cols;j++)
                {
                        printf("%d ",arr[i][j]);
                }
                printf("\n");
        }
}
```
# output
```
1 5 7 11 
3 7 10 15 
6 8 11 12
```
# 13.Sorting an array column wise
```c
#include<stdio.h>
int main()
{
        int rows=4,cols=3;
        int arr[4][3]={{11,10,8},
                             {32,12,20},
                             {11,56,17},
                             {13,65,38}};
        int i=0,j=0,col=0,temp=0;
        for(col=0;col<cols;col++)
        {
                for(i=0;i<rows-1;i++)
                {
                        for(j=0;j<rows-i-1;j++)
                        {
                                if(arr[j][col]>arr[j+1][col])
                                {
                                        temp=arr[j][col];
                                        arr[j][col]=arr[j+1][col];
                                        arr[j+1][col]=temp;
                                }
                        }
                }
        }
        for(i=0;i<rows;i++)
        {
                for(j=0;j<cols;j++)
                {
                        printf("%d ",arr[i][j]);
                }
                printf("\n");
        }
}
```
# output
```
11 10 8 
11 12 17 
13 56 20 
32 65 38 
```
# 14.Matrix multiplication
```c
#include<stdio.h>
#define row1 3
#define col1 4
#define row2 col1
#define col2 2
int main()
{
     int mat1[row1][col1],mat2[row2][col2],mat3[row1][col2];
     int i,j,k;
     printf("Enter mat1 elements:");
     for(i=0;i<row1;i++)
     {
         for(j=0;j<col1;j++)
         {
            scanf("%d",&mat1[i][j]);
         }
     }
     printf("Enter mat2 elements:");
     for(i=0;i<row2;i++)
     {
        for(j=0;j<col2;j++)
        {
            scanf("%d",&mat2[i][j]);
        }
     }
     for(i=0;i<row1;i++)
     {
        for(j=0;j<col2;j++)
        {
           mat3[i][j]=0;
           for(k=0;k<col1;k++)
           {
              mat3[i][j]+=mat1[i][k]*mat2[k][j];
           }
        }
     }
     for(i=0;i<row1;i++)
     {
          for(j=0;j<col2;j++)
          {
             printf("%5d ",mat3[i][j]);
          }
          printf("\n");
     }
}
```
# output
```
Enter mat1 elements:1 2 3 4 5 6 7 8 9 10 11 12
Enter mat2 elements:1 2 3 4 5 6 7 8
   50    60 
  114   140 
  178   220 
```
# 15.Transpose of a matrix
```c
#include<stdio.h>
#define row 3
#define col 4
int main()
{
        int mat1[row][col],mat2[col][row],i,j;
        for(i=0;i<row;i++)
        {
              for(j=0;j<col;j++)
              {
                     scanf("%d",&mat1[i][j]);
              }
        }
        for(i=0;i<row;i++)
        {
              for(j=0;j<col;j++)
              {
                    printf("%3d",mat1[i][j]);
              } 
              printf("\n");
        }
        for(i=0;i<col;i++)
        {
              for(j=0;j<row;j++)
              {
                    mat2[i][j]=mat1[j][i];
              }
        }
        for(i=0;i<col;i++)
        {
              for(j=0;j<row;j++)
              {
                    printf("%3d",mat2[i][j]);
              }
              printf("\n");
        }
}
```
# output
```
Enter array elements:1 2 3 4 5 6 7 8 9 10 11 12
  1  2  3  4
  5  6  7  8
  9 10 11 12
  1  5  9
  2  6 10
  3  7 11
  4  8 12
```
# 16.Decimal to other forms based on choice
```c
#include<stdio.h>
void fun(int n,int b);
int main()
{
int n=30;
printf("1.Binary form\n2.octal form\n3.hexadecimalform\n");
printf("Enter your choice:");
int ch;
scanf("%d",&ch);
switch(ch)
{
case 1:
    printf("The binary form is:");
    fun(n,2);
    break;
case 2:
    printf("The octal form is:");
    fun(n,8);
    break;
case 3:
     printf("The hexadecimail form is:");
     fun(n,16);
     break;
}
printf("\n");
}
void fun(int n,int b)
{
    int i,rem;
    char arr[20];
    while(n>0)
    {
        rem=n%b;
        n/=b;
        if(rem>9 && rem<16)
        {
            arr[i++]=rem-10+'A';
        }
        else
        {
            arr[i++]=rem+'0';
        }
     }
     for(int j=i-1;j>=0;j--)
     {
           printf("%c",arr[j]);
     }
}
```
# output
```
1.Binary form
2.octal form
3.hexadecimalform
Enter your choice:1
The binary form is:11110
```
# 17.Linear search
```c
#include<stdio.h>
int linear(int arr[],int val);
int main()
{
      int arr[10]={1,2,3,4,5,6,7,8,9,0};
      int val=7;
      printf("%d\n",linear(arr,val));
}
int linear(int arr[],int val){
int i;
while(arr[i]!=val)
{
     i++;
}
if(i<10)
{
     return i;
}
else
{
     return -1;
}
}
```
# output
```
6
```
# 18.Binary search in sorted array
```c
#include<stdio.h>
int binary(int arr[],int n);
int main()
{
     int arr[10]={1,2,3,4,5,6,7,8,9,10};
     int n=5;
     if(binary(arr,n)==-1)
     {
               printf("Element not found");
     }
     else
     {
               printf("Element found at %d th index",binary(arr,n));
     }
}
int binary(int arr[],int n)
{
     int low=0,high=9,mid;
     while(low<high)
     {
               mid=low+high/2;
               if(arr[mid]<n)
               {
                   low=mid+1;
               }
               else if(arr[mid]>n)
               {
                   high=mid-1;
               }
               else
               {
                   return mid;
               }
      }
      return -1;
}
```
# output
```
Element found at 4 th index
```
# 19.Swapping index 0 with the smallest element in an array
```c
#include<stdio.h>
int main()
{
int arr[10]={5,6,3,2,1,8,9,4,6,0};
int temp,min=0;
for(int i=0;i<10;i++){
if(arr[min]>arr[i]){
min=i;
}
}
if(min!=0){
temp=arr[0];
arr[0]=arr[min];
arr[min]=temp;
}
for(int i=0;i<10;i++){
printf("%d",arr[i]);
}
}
```
# output
```
0 6 3 2 1 8 9 4 6 5
```
# 20.Selection sort
```c
#include<stdio.h>
int main()
{
      int arr[10]={1,2,3,4,12,4,16,33,21,23};
      int temp,n=10;
      int i,j,min;
      for(i=0;i<n-1;i++)
      {
         min=i;
         for(j=i+1;j<n;j++)
         {
               if(arr[min]>arr[j])
               {  
                   min=j;
               }  
         }
         if(i!=min)
         {
               temp=arr[i];
               arr[i]=arr[min];
               arr[min]=temp;
         }
      }
      for(i=0;i<n;i++)
      {
                printf("%d ",arr[i]);
      }
printf("\n");
}
```
# output
```
1 2 3 4 4 12 16 21 23 33
```
# 21.Largest element to the last
```c
#include<stdio.h>
int main()
{
      int arr[5]={5,46,7,0,50};
      int j,n=5;
      int exchanges=0;
      int temp;
      for(j=0;j<n-1;j++)
      {
            if(arr[j]>arr[j+1])
            {
                  temp=arr[j];
                  arr[j]=arr[j+1];
                  arr[j+1]=temp;
                  exchanges++;
            }
     }  
     for(j=0;j<n;j++)
     {
            printf("%d ",arr[j]);
     }
     printf("number of exchanges:%d\n",exchanges);
}
```
# output
```
5 7 0 46 50 number of exchanges:2
```
# 22.Bubble sort
```c
#include<stdio.h>
int main()
{
      int arr[8]={4,16,2,4,9,3,25,5};
      int i,j,exchange,n=8,temp;
      for(i=0;i<n;i++)
      {
           for(j=0;j<n-1-i;j++)
           {
               if(arr[j]>arr[j+1])
               {
                    temp=arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=temp;
               }
           }
       }
       for(i=0;i<n;i++)
       {
            printf("%d ",arr[i]);
       }
       printf("\n");
}
```
# output
```
2 3 4 4 5 9 16 25
```
# 23.Insering an element at a given position and moving elements to right
```c
#include<stdio.h>
int main()
{
      int n=10;
      int i,item=7;
      int index=5;
      int arr[10]={2,4,66,4,3,12,23,9,76};
      for(i=n-2;i>=index;i--)
      {
           arr[i+1]=arr[i];
      }
      arr[index]=item;
      for(i=0;i<n;i++)
      {
           printf("%d ",arr[i]);
      }
      printf("\n");
}
```
# output
```
2 4 66 4 3 7 12 23 9 76
```
# 24.Inserting an element in a sorted array
```c
#include<stdio.h>
int main()
{
         int arr[10]={1,2,3,4,5,6,12,13,15};
         int item=7;
         int i;
         int n=10;
         for(i=n-2;item<arr[i] && i>=0;i--)
         {
              arr[i+1]=arr[i];
         }
         arr[i+1]=item;
         for(i=0;i<n;i++)
         {
              printf("%d ",arr[i]);
         }
         printf("\n");
}
```
# output
```
1 2 3 4 5 6 7 12 13 15
```
# 25.Insertion sort
```c
#include<stdio.h>
int main()
{
      int arr[10]={2,33,55,12,16,23,46,7,10,1};
      int i,k,j,n=10;
      for(i=1;i<n;i++)
      {
         k=arr[i];
         for(j=i-1;j>=0 && arr[j]>k;j--)
         {
              arr[j+1]=arr[j];
         }
         arr[j+1]=k;
      }
      for(i=0;i<n;i++)
      {
         printf("%d ",arr[i]);
      }
      printf("\n");
}
```
# output
```
1 2 7 10 12 16 23 33 46 55
```
# 26.Merging two sorted arrays and getting another sorted array
```c
#include<stdio.h>
int main()
{
    int arr1[5]={1,3,6,7,8};
    int arr2[5]={2,9,10,12,15};
    int i=0,j=0,k=0;
    int n1=5,n2=5;
    int arr3[10];
    while(i<n1 && j<n2)
    {
         if(arr1[i]<arr2[j])
         {
              arr3[k++]=arr1[i++];
         }
         else
         {
              arr3[k++]=arr2[j++];
         }
   }
   while(i<n1)
   {
        arr3[k++]=arr1[i++];
   }
   while(j<n2)
   {
        arr3[k++]=arr2[j++];
   }
   for(i=0;i<n1+n2;i++)
   {
        printf("%d ",arr3[i]);
   }
}
```
# output
```
1 2 3 6 7 8 9 10 12 15
```
# 27.Pascals triangle
```c
#include<stdio.h>
int main()
{
    int i,j,n;
    n=7;
    int a[15][15];
    for(i=0;i<n;i++)
    {
         for(j=0;j<=i;j++)
         {
              if(j==0 || i==j)
              {
                    a[i][j]=1;
              }
              else
              {
                    a[i][j]=a[i-1][j-1]+a[i-1][j];
              }
         }
    }
    for(i=0;i<n;i++)
    {
         for(j=0;j<=i;j++)
         {
               printf("%3d",a[i][j]);
         }
         printf("\n");
    }
    printf("\n");
}
```
# output
```
  1
  1  1
  1  2  1
  1  3  3  1
  1  4  6  4  1
  1  5 10 10  5  1
  1  6 15 20 15  6  1
```




 







