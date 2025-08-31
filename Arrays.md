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
int arr[3][3]={{3,2,4},{6,3,2},{7,4,5}};
int m=3,n=3;
int temp,k,min,i,j;
for(i=0;i<m;i++)
{
for(j=0;j<n-1;j++)
{
min=j;
for(k=j+1;k<n;k++)
{
if(arr[i][min]>arr[i][k])
{
min=k;
}
}
if(min!=j)
{
temp=arr[i][j];
arr[i][j]=arr[i][min];
arr[i][min]=temp;
}
}
}
for(i=0;i<n;i++)
{
for(j=0;j<m;j++)
{
printf("5%d",arr[i][j]);
}
printf("\n");
}
}
```
# output
```
52 53 54 
52 53 56 
54 55 57 
```
# 13.Sorting an array column wise
```c
:




