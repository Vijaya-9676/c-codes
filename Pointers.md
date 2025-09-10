## Code Snippets
# 1.
```c
#include<stdio.h>
int main()
{
        int arr[5]={1,2,3,4,5};
        int *p=arr;
        int (*ptr)[10]=&arr;
        printf("%p\t%p\n",p,ptr);
        ptr++;
        p++;
        printf("%p\t%p\n",p,ptr);
}
```
# output
```
0x7ffe77056b30	0x7ffe77056b30
0x7ffe77056b34	0x7ffe77056b58
```
# 2.
```c
#include<stdio.h>
int main()
{
        int arr[5]={1,2,3,4,5};
        int (*ptr)[5]=&arr;
        for(int i=0;i<5;i++)
        {
          printf("%d\n",*(*ptr+i));
        }
}
```
# output
```
1
2
3
4
5
```
# 3.
```c
#include<stdio.h>
int main()
{
        int arr[3][4]={{1,2,3,4},{5,6,7,8},{9,10,11,12}};
        int i,j;
        int (*ptr)[4]=arr;
        for(i=0;i<3;i++)
        {
                for(j=0;j<4;j++)
                {
                        printf("%d\t%p\n",ptr[i][j],&ptr[i][j]);
                }
        }
        printf("\n");
        for(i=0;i<3;i++)
        {
                for(j=0;j<4;j++)
                {
                        printf("%d\t%p\n",*(*(ptr+i)+j),*(ptr+i)+j);
                 }
        }
}
```
# output
```
1	0x7fffceefe270
2	0x7fffceefe274
3	0x7fffceefe278
4	0x7fffceefe27c
5	0x7fffceefe280
6	0x7fffceefe284
7	0x7fffceefe288
8	0x7fffceefe28c
9	0x7fffceefe290
10	0x7fffceefe294
11	0x7fffceefe298
12	0x7fffceefe29c

1	0x7fffceefe270
2	0x7fffceefe274
3	0x7fffceefe278
4	0x7fffceefe27c
5	0x7fffceefe280
6	0x7fffceefe284
7	0x7fffceefe288
8	0x7fffceefe28c
9	0x7fffceefe290
10	0x7fffceefe294
11	0x7fffceefe298
12	0x7fffceefe29c
```
# 4.
```c
include<stdio.h>
int main()
{
        int arr[2][3][3]={{{1,2,3},{4,5,6},{7,8,9}},
                {{10,11,12},{13,14,15},{16,17,18}}};
        int i,j,k;
        for(i=0;i<2;i++)
        {
             for(j=0;j<3;j++)
             {
                for(k=0;k<3;k++)
                 {
                    printf("%d\t%p\n",*(*(*(arr+i)+j)+k),*(*(arr+i)+j)+k);
                 }
             }
        }
}

```
# output
```
1	0x7fff58e633f0
2	0x7fff58e633f4
3	0x7fff58e633f8
4	0x7fff58e633fc
5	0x7fff58e63400
6	0x7fff58e63404
7	0x7fff58e63408
8	0x7fff58e6340c
9	0x7fff58e63410
10	0x7fff58e63414
11	0x7fff58e63418
12	0x7fff58e6341c
13	0x7fff58e63420
14	0x7fff58e63424
15	0x7fff58e63428
16	0x7fff58e6342c
17	0x7fff58e63430
18	0x7fff58e63434
```
# 5.
```c
#include<stdio.h>
#include<string.h>
void rev(char *str);
int main()
{
        char s[]="zentree";
        rev(s);
        printf("%s\n",s);
}
void rev(char *str)
{
        char *start=str;
        char *end=str+strlen(str)-1;
while(start<=end)
{
        char temp=*start;
        *start=*end;
        *end=temp;
        start++;
        end--;
}
}
```
# output
```
eertnez
```
# 6.
```c
#include<stdio.h>
void sort(int arr[],int *n);
int main()
{
        int arr[]={2,4,3,6,7,5,10,0};
        int n=8,min=arr[0];
        sort(arr,&n);
        for(int i=0;i<n;i++)
        {
                printf("%d ",arr[i]);
        }
        printf("\n");
}
void sort(int arr[],int *n)
{
        int *i,*j;
        for(i=arr;i<arr + (*n-1);i++)
        {
                for(j=i+1;j< arr + *n;j++)
                {
                        if(*i>*j)
                        {
                                int temp=*i;
                                *i=*j;
                                *j=temp;
                        }
                }
        }
}
```
# output
```
0 2 3 4 5 6 7 10 
```
# 7.
```c
#include<stdio.h>
int *fun(int a,int i);
int main()
{
        int a=5;
        int i=2;
        printf("%p\n",fun(a,i));
}
int *fun(int a,int i)
{
        int *p=&a;
        printf("%p\n",p);
        p=p+i;
        return p;
}
```
# output
```
0x7ffc419de00c
0x7ffc419de014
```
# 8.
```c
#include<stdio.h>
struct student
{
        char name[20];
        int rollno;
        int marks;
};
int main()
{
        struct student stuarr[3]={{"mary",12,98},
                                   {"john",11,97},
                                   {"tom",13,89}};

        struct student *arr[3];
        for(int i=0;i<3;i++)
        {
                arr[i]=&stuarr[i];
        }
        struct student **p=arr;
        for(int i=0;i<3;i++)
        {
                printf("Name:%s\n",p[i]->name);
        }

}
```
# 9.
```c
#include<stdio.h>
struct student
{
        char name[20];
        int rollno;
        int marks;
};
int main()
{
        struct student stuarr[3]={{"mary",12,98},
                                   {"john",11,97},
                                   {"tom",13,89}};

        struct student *arr[3];
        for(int i=0;i<3;i++)
        {
                arr[i]=&stuarr[i];
        }
        struct student **p=arr;
        for(int i=0;i<3;i++)
        {
                printf("Name:%s\n",p[i]->name);
        }

}
```
# output
```
Name:mary
Name:john
Name:tom
```
# 10.
```c
#include<stdio.h>
void search(int arr[],int n);
int main()
{
        int arr[]={1,2,3,4,5};
        int *ptr=arr;
        int ele=2;
        int flag=0;
        for(ptr=arr;ptr<arr+5;ptr++)
        {
                if(*ptr==ele)
                {
                        flag=1;
                        break;
                }
        }
        if(flag)
        {
                printf("element %d found at index %ld\n",ele,ptr-arr);
        }
}
```
# output
```
element 2 found at index 1
```
# 11.
```c
#include<stdio.h>
int main()
{
        int mat1[2][3]={{1,2,3},{4,5,6}};
        int mat2[2][3]={{1,2,3},{4,5,6}};
        int mat3[2][3];
        int *p1=&mat1[0][0];
        int *p2=&mat2[0][0];
        int *p3=&mat3[0][0];
        for(int i=0;i<6;i++)
        {
                *(p3+i)=*(p1+i) + *(p2+i);
        }
        for(int i=0;i<2;i++)
        {
                for(int j=0;j<3;j++)
        {
                printf("%d ",*(*(mat3+i)+j));
        }
        printf("\n");
        }
}
```
# output
```
2 4 6 
8 10 12
```
# 12.
```c
#include<stdio.h>
void concat(char *str1,char *str2);
int main()
{
        char str1[20]="viven";
        char str2[]="123";
        concat(str1,str2);
        printf("%s\n",str1);
}
void concat(char *str1,char *str2)
{
        while(*str1!='\0')
        {
                str1++;
        }
        while((*str1++=*str2++)!='\0')
        {
          ;
        }
        
}
```
# output
```
viven123
```
# 13.
```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
        int *arr=(int *)malloc(10*sizeof(int));
        if(arr==NULL)
        {
                printf("Memory allocation failed!\n");
        }
        for(int i=0;i<10;i++)
        {
                scanf("%d",arr+i);
        }
        for(int i=0;i<10;i++)
        {
                printf("%d ",*(arr+i));
        }
        printf("\n");
}
```
# output
```
1 2 3 4 5 6 7 8 9 10
1 2 3 4 5 6 7 8 9 10 
```
# 14.
```c
#include<stdio.h>
int main()
{
        int *p[5];
        int arr[]={1,2,3,4,5};
        for(int i=0;i<5;i++)
        {
                p[i]=&arr[i];
        }
        for(int i=0;i<5;i++)
        {
                printf("%d   %p\n",*p[i],p[i]);
        }
        printf("\n");
}
```
# output
```
1   0x7ffc2bb9f330
2   0x7ffc2bb9f334
3   0x7ffc2bb9f338
4   0x7ffc2bb9f33c
5   0x7ffc2bb9f340
```
# 15.
```c
#include<stdio.h>
int main()
{
        int arr[5]={1,2,3,4,5};
        int (*ptr)[5]=&arr;
        printf("%p\t%d\n",ptr,*(*ptr+1));
}
```
# output
```
0x7fff9a049450	2
```
# 16.
```c
#include<stdio.h>
int add(int a,int b);
int main()
{
        int (*fp)(int,int);
        fp=add;
        int res;
        res=add(2,3);
        printf("%d\t",res);
        res=(*fp)(2,3);
        printf("%d\t",res);
}
int add(int a,int b)
{
        return a+b;
}
```
# output
```
5	5
```
# 17.
```c
#include<stdio.h>
void func(char,void (*fp)(float));
void fun1(float);
int main()
{
        char ch='A';
        func(ch,fun1);
}
void func(char c,void (*fp)(float))
{
        printf("%c\n",c);
        (*fp)(8.5);
}
void fun1(float d)
{
        printf("%f\n",d);
}
```
# output
```
A
8.500000
```
# 18.
```c
#include<stdio.h>
void func(char,void (*fp)(int));
void fun1(int);
int main()
{
        void (*fp)(int);
        void *p=fun1;
        func('c',p);
}
void func(char c,void (*fp)(int))
{
        printf("%c\n",c);
        (*fp)(8.5);
}
void fun1(int d)
{
        printf("%d\n",d);
}
```
# output
```
A
8.500000
```
# 19.
```c
#include<stdio.h>
int main()
{
        int a,b=10;
        a=-b--;
        printf("a=%d,b=%d",a,b);
}
```
# output
```
a=-10,b=9
```
# 20.
```c
#include<stdio.h>
int main()
{
        int array[5][5];
        printf("%d",((array==*array)&&(*array==array[0])));
}
```
# output
```
1
```
# 20.
```c
#include<stdio.h>
int func()
{
int num=10;
return &num;
}
int main()
{
int *p=func();
printf("%d",*p);
}
```
# output
```
segmentatult(core dumped)
```
# 21.
```c
#include<stdio.h>
int main()
{
        char *s[]={"knowledge","is","power"};
        char **ptr[]={s+2,s+1,s};
        char ***pptr=ptr;
        printf("%s",**++pptr);
        printf("%s",*--*++pptr+3);
        printf("%s",**pptr+1);
}
```
# output
```
is�����
```
## PROGRAMS
# 22.Length of stringg using pointers
```c
#include<stdio.h>
int len(char *s);
int main()
{
char *s[20];
printf("Enter a string:");
gets(s);
printf("%d\n",len(s));
}
int len(char *s)
{
char *ptr=s;
while(*ptr != '\0')
{
ptr++;
}
return ptr-s;
}
```
# output
```
Enter a string:programming
11
```
# 23.Min and max elements using pointers
```c
#include<stdio.h>
int main()
{
int arr[5]={2,12,4,5,3};
int min,max;
minmax(arr,&min,&max);
printf("%d %d\n",min,max);
}
int minmax(int *arr,int *min,int *max)
{
*min=arr[0];
*max=arr[0];
int *ptr=arr;
for(int i=0;i<5;i++)
{
if(*(ptr+i)<*min)
{
*min=*(ptr+i);
}
if(*(ptr+i)>*max)
{
*max=*(ptr+i);
}
}
}
```
# output
```
2 12
```
# 24.Reversing a string using pointers
```c
#include<stdio.h>
#include<string.h>
void reverse(char *str);
int main()
{
char *s[20];
printf("Enter a string:");
gets(s);
reverse(s);
puts(s);
}
void reverse(char *str)
{
char *start=str;
char *end=str+strlen(str)-1;
char temp;
while(start<end)
{
temp=*start;
*start=*end;
*end=temp;
start++;
end--;
}
}
```
# output
```
Enter a string:program
margorp
```
# 25.Sum of elements of an array using pointer arithmetic
```c
#include<stdio.h>
int main()
{
int arr[5]={1,2,3,4,5};
int *ptr=arr;
int sum=0;
for(int i=0;i<5;i++)
{
sum+=*(ptr+i);
}
printf("%d\n",sum);
}
```
# output
```
15
```
# 26.Copying a string into another without using cpy and using pointers
```c
#include<stdio.h>
void strcopy(char *s,char *d);
int main()
{
char *str="viven";
char *des[10];
strcopy(str,des);
printf("%s",des);
}
void strcopy(char *s,char *d)
{
while(*s != '\0')
{
*d=*s;
s++;
d++;
}
}
```
# output
```
viven
```
# 27.Comparing two strings lixicographically using pointers
```c
#include<stdio.h>
int lex(char *s1,char *s2);
int main()
{
char *s1="Ramya";
char *s2="Ramya";
printf("%d\n",lex(s1,s2));
}
int lex(char *s1,char *s2)
{
while(*s1 && *s2)
{
if(*s1!=*s2)
{
return *s1-*s2;
}
s1++;
s2++;
}
return *s1-*s2;
}
```
# output
```
0
```
# 28.Reversing an array using pointers
```c
#include<stdio.h>
int rev(int *a,int n);
int main()
{
int a[5]={1,2,3,4,5};
rev(a,5);
for(int i=0;i<5;i++)
{
printf("%d ",a[i]);
}
}
int rev(int *a,int n)
{
int *ptr=a,temp;
for(int i=0;i<=n/2;i++)
{
temp=*(ptr+i);
*(ptr+i)=*(ptr+n-i-1);
*(ptr+n-i-1)=temp;
}
}
```
# output
```
5 4 3 2 1
```
# 29.Printing an array by dynamic memory allocation
```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
int *ptr=(int *)malloc(5*sizeof(int));
printf("Enter array elements:");
if(ptr==NULL)
{
printf("Memory not available ");
exit(1);
}
for(int i=0;i<5;i++)
{
scanf("%d",ptr+i);
}
for(int i=0;i<5;i++)
{
printf("%d ",*(ptr+i));
}
}
```
# output
```
Enter array elements:1 2 3 4 5
1 2 3 4 5
```
# 30.Factorial of a number using pointers
```c
#include<stdio.h>
int fact(int *n,int *factorial);
int main()
{
int num=5;
int factorial;
fact(&num,&factorial);
printf("%d\n",factorial);
}
int fact(int *n,int *factorial)
{
*factorial=1;
for(int i=1;i<=*n;i++)
{
*factorial *= i;
}
}
```
# output
```
120
```
# 31.Counting no.of vowels and consonants using pointers
```c
#include<stdio.h>
#include<ctype.h>
void consvow(char *str,int *vowel,int *consonant);
int main()
{
char *str="radha123";
int vowel,consonant;
consvow(str,&vowel,&consonant);
printf("%d  %d\n",vowel,consonant);
}
void consvow(char *str,int *vowel,int *consonant)
{
*vowel=0;
*consonant=0;
while(*str != '\0')
{
char ch = tolower(*str);
if(*str >= 'a' && *str <= 'z')
{
if(*str=='a'||*str=='e'||*str=='i'||*str=='o'||*str=='u')
{
(*vowel)++;
}
else
{
(*consonant)++;
}
}
str++;
}
}
```
# output
```
2  3
```
# 32.Sorting an array using pointers
```c
#include<stdio.h>
void sort(int *arr,int *n,int *min);
int main()
{
int arr[8]={2,53,21,12,6,4,76,75};
int n=8,min=arr[0];
sort(arr,&n,&min);
for(int i=0;i<n;i++)
{
printf("%d ",arr[i]);
}
}
void sort(int *arr,int *n,int *min)
{
int *i,*j;
for(i=arr;i<arr + *n -1;i++)
{
for(j=i+1;j < arr + *n;j++)
{
if(*i > *j)
{
int temp=*i;
*i=*j;
*j=temp;
}
}
}
}
```
# output
```
2 4 6 12 21 53 75 76
```
# 33.Function returning a pointer
```c
#include<stdio.h>
int *fun(int *p,int n);
int main()
{
int arr[5]={1,2,3,4,5};
int n=5;
int *ptr;
ptr=fun(arr,n);
printf("%p",ptr);
}
int *fun(int *p,int n)
{
p=p+n;
return p;
}
```
# output
```
0x7fff1a4ef794
```
# 34.Searching an element 
```c
#include<stdio.h>
void search(int *a,int n,int target);
int main()
{
int a[8]={1,2,3,4,5,6,7,8};
int target=12;
int n=8;
search(a,n,target);
}
void search(int *a,int n,int target)
{
int *ptr=a;
for(int i=0;i<n;i++)
{
if(*ptr==target)
{
printf("Element found at %d\n",i);
return;
}
ptr++;
}
printf("Element not found");
}
```
# output
```
Element not found
```
# 35.Addition of two integers using pointers
```c
#include<stdio.h>
int mat(int (*mat1)[3],int (*mat2)[3],int (*mat3)[3]);
int main()
{
int mat1[3][3]={{1,2,3},{4,5,6},{7,8,9}};
int mat2[3][3]={{1,2,3},{4,5,6},{7,8,9}};
int mat3[3][3];
mat(mat1,mat2,mat3);
for(int i=0;i<3;i++)
{
for(int j=0;j<3;j++)
{
printf("%d ",mat3[i][j]);
}
printf("\n");
}
}
int mat(int (*mat1)[3],int (*mat2)[3],int (*mat3)[3])
{
for(int i=0;i<3;i++)
{
for(int j=0;j<3;j++)
{
*(*(mat3+i)+j)=*(*(mat1+i)+j)+*(*(mat2+i)+j);
}
}
}
```
# output
```
2 4 6 
8 10 12 
14 16 18 
```
# 36.Multiplication of two matrices
```c
#include<stdio.h>
int mat(int (*mat1)[4],int (*mat2)[3],int (*mat3)[3]);
int main()
{
int mat1[3][4]={{1,2,3,4},{5,6,7,8},{9,10,11,12}};
int mat2[4][3]={{12,11,10},{8,7,6},{4,3,2},{9,5,1}};
int mat3[3][3];
mat(mat1,mat2,mat3);
for(int i=0;i<3;i++)
{
for(int j=0;j<3;j++)
{
printf("%d ",mat3[i][j]);
}
printf("\n");
}
}
int mat(int (*mat1)[4],int (*mat2)[3],int (*mat3)[3])
{
for(int i=0;i<3;i++)
{
for(int j=0;j<3;j++)
{
*(*(mat3+i)+j)=0;
for(int k=0;k<4;k++)
{
*(*(mat3+i)+j)+=*(*(mat1+i)+k) * *(*(mat2+k)+j);
}
}
}
}
```
# output
```
76 54 32 
208 158 108 
340 262 184 
```
# 37.Concatinating two strings using pointers
```c
#include<stdio.h>
void concat(char *s1,char *s2,char *ptr);
int main()
{
char *s1="Ramya";
char *s2="Rani";
char *str[15];
concat(s1,s2,&str);
printf("%s",str);
}
void concat(char *s1,char *s2,char *ptr)
{
while(*s1 != '\0')
{
*ptr=*s1;
ptr++;
s1++;
}
while(*s2 != '\0')
{
*ptr=*s2;
ptr++;
s2++;
}
}
```
# Output
```
RamyaRani
```
# 38.Dynamically allocate a 2d array using pointer to an array
```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
int r=3;
int (*ptr)[4];
ptr=(int (*)[4])malloc(r*4*sizeof(int));
printf("Enter array elements:\n");
for(int i=0;i<r;i++)
{
for(int j=0;j<4;j++)
{
scanf("%d",&ptr[i][j]);
}
}
for(int i=0;i<3;i++)
{
for(int j=0;j<4;j++)
{
printf("%d ",ptr[i][j]);
}
printf("\n");
}
}
```
# output
```
Enter array elements:
1 2 3 4 5 6 7 8 9 10 11 12
1 2 3 4 
5 6 7 8 
9 10 11 12 
```
# 39.Array of pointer
```c
#include<stdio.h>
int main()
{
int *a[5];
int arr[5]={1,2,3,4,5};
for(int i=0;i<5;i++)
{
a[i]=&arr[i];
}
for(int i=0;i<5;i++)
{
printf("%p ",a[i]);
}
}
```
# output
```
0x7ffcccf6ac70 0x7ffcccf6ac74 0x7ffcccf6ac78 0x7ffcccf6ac7c 0x7ffcccf6ac80
```
# 40.Pointer to an array
```c
#include<stdio.h>
int main()
{
int (*a)[5];
int arr[5]={1,2,3,4,5};
a=&arr;
printf("%d\n",*(*(a)));
printf("%p\n",a);
printf("%p\n",++a);
}
```
# output
```
1
0x7fffdbd723d0
0x7fffdbd723e4
```
# 41.Invoking a function using function pointer
```c
#include<stdio.h>
int fun(int a,int b);
int main()
{
int (*fp)(int a,int b);
int a=5,b=2;
fp=fun;
int r=(*fp)(a,b);
printf("%d\n",r);
}
int fun(int a,int b)
{
if(a>b)
{
return a;
}
else
{
return b;
}
}
```
# output
```
5
```
# 42.Sending functions address as an argument to another function
```c
#include<stdio.h>
void fun(char c,void (*f1)(int));
void function(int);
int main()
{
fun('a',function);
}
void fun(char c,void (*f1)(int))
{
printf("%c ",c);
(*f1)(5);
}
void function(int d)
{
printf("%d\n",d);
}
```
# output
```
a 5
```
# 43.Passing a pointer containing functions address as an argument
```c
#include<stdio.h>
void fun(char c,void (*fp)(int));
void f1(int a);
int main()
{
void (*p)(int);
p=f1;
fun('a',p);
}
void fun(char c,void (*fp)(int))
{
printf("%c\n",c);
(*fp)(5);
}
void f1(int a)
{
printf("%d\n",a);
}
```
# output
```
a
5
```
















             




