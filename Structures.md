# 1.
```c
#include<stdio.h>
#include<string.h>
struct person
{
        char name[50];
        int age;
};
int main()
{
        struct person p1;
        strcpy(p1.name,"John Doe");
        p1.age=30;
        printf("Name:%s,Age:%d\n",p1.name,p1.age);
}
```
# output
```
Name:John Doe,Age:30
```
# 2.
```c
#include<stdio.h>
union data
{
        int i;
        float f;
};
int main()
{
        union data value;
        value.i=10;
        printf("Float value:%f\n",value.f);
}
```
# output
```
Float value:0.000000
```
# 3.
```c
#include<stdio.h>
#include<string.h>
struct data
{
        int i;
        char str[20];
};
void print_data(struct data *d)
{
        printf("Integer:%d\n",d->i);
        printf("string:%s\n",d->str);
}
int main()
{
        struct data d1;
        d1.i=10;
        strcpy(d1.str,"Hello world");
        print_data(&d1);
}
```
# output
```
Integer:10
string:Hello world
```
# 4.
```c
#include<stdio.h>
union data
{
        int i;
        float f;
};
int main()
{
        union data value;
        value.i=10;
        printf("Float value(before modification):%f\n",value.f);
        value.f=3.14;
        printf("Float value(after modification):%f\n",value.f);
}
```
# output
```
Float value(before modification):0.000000
Float value(after modification):3.140000
```
# 5.
```c
#include<stdio.h>
typedef struct
{
        char A;
        int B;
        char C;
}InfoData;
int main(int argc,char *argv[])
{
        printf("\n size of structure=%ld\n\n",sizeof(InfoData));
}
```
# output
```
size of structure=12
```
# 6.
```c
#include<stdio.h>
typedef struct
{
        double A;
        char B;
        char C;
}InfoData;
int main(int argc,char *argv[])
{
        printf("\n size of structure=%ld\n\n",sizeof(InfoData));
}
```
# output
```
 size of structure=16
```
# 7.
```c
#include<stdio.h>
typedef struct
{
        int A;
        int B;
        char C;
        char D;
        float E;
}InfoData;
int main(int argc,char *argv[])
{
        printf("\n size of structure =%ld\n\n",sizeof(InfoData));
}
```
# output
```
size of structure=16
```
# 8.
```c
#include<stdio.h>
typedef struct
{
        char A;
        char B;
}InfoData;
int main(int argc,char *argv[])
{
        printf("\n size of structure=%ld\n\n",sizeof(InfoData));
}
```
# output
```
2
```
# 9.
```c
#include<stdio.h>
typedef struct
{
        char A;
        short B;
        int C;
        char D;
}InfoData;
int main(int argc,char *argv[])
{
        printf("\n size of structure=%d\n\n",sizeof(InfoData));
}
```
# output
```
12
```
# 10.
```c
#include<stdio.h>
typedef struct
{
        char A;
        double B;
        char C;
}InfoData;
int main()
{
        printf("\n sizeof structure=%d\n\n",sizeof(InfoData));
}
```
# output
```
24
```
# 11.
```c
#include<stdio.h>
typedef struct
{
        char A;
        char B;
        short C;
        int D;
}InfoData;
int main()
{
        printf("\n size of structure = %d\n\n",sizeof(InfoData));
}
```
# output
```
8
```
# 12.
```c
#include<stdio.h>
#pragma pack(push,1)
typedef struct
{
        double A;
        char B;
}InfoData;
#pragma pack(pop)
int main(int argc,char *argv[])
{
        printf("\n size of structure = %ld\n\n\n",sizeof(InfoData));
}
```
# output
```
9
```
# 13.
```c
#include<stdio.h>
#pragma pack(push,4)
typedef struct
{
        double A;
        char B;
}InfoData;
#pragma pack(pop)
int main()
{
        printf("\n size of structure = %d\n\n\n\n",sizeof(InfoData));
}
```
# output
```
12
```









