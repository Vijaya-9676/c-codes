## Code Snippets
# 1.
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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
```
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






             




