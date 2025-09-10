# 1.
```c
#include<stdio.h>
int func(void);
int main()
{
int x=10;
x=func();
printf("%d\n",x);
return 0;
}
int func(void)
{
printf("Function\n");
}
```
# output
```
Function
9
```
# 2.
```c
#include<stdio.h>
int main(void)
{
int s;
s=func(1,2);
printf("%d\n",s);
s=func(1,2,3,4);
printf("%d\n",s);
return 0;
}
int func(int a , int b,int c)
{
return a+b+c;
}
```
# output
```
-1670223877
6
```
# 3.
```c
#include<stdio.h>
int func1(int n);
int sum(int m);
int main()
{
   int num;
   printf("Enter a number:");
   scanf("%d",&num);
   if(func1(num==1))
   {
         printf("Happy number");
   }
   else
   {
         printf("Not a happy number");
   }
}
int sum(int m)
{
   int s=0;
   int r;
   while(m>0)
   {
         r=m%10;
         s+=r*r;
         m=m/10;
   }
   return s;
}
int func1(int n)
{
   int p;
   while(n>=1)
   {
        p=sum(n);
        n=p;
        if(p==1)
        {
           return 1;
        }
   }
}

```
# output
```
Enter a number:10
Not a happy number
```
# 4.
```c
#include<stdio.h>
int sumdiv(int num);
int main()
{
int n;
int n1,n2;
printf("Enter 1st number:");
scanf("%d",&n1);
printf("Enter 2nd number:");
scanf("%d",&n2);
if(sumdiv(n1)==n2 && sumdiv(n2)==n1){
printf("Amicable");
}
else{
printf("Not amicable");
}
}
int sumdiv(int num)
{
int s=0;
int i=1;
while(i<num){
if(num%i==0)
{
s+=i;
}
i+=1;
}
return s;
}
```
# output
```
Enter 1st number:20
Enter 2nd number:30
Not amicable
```
# 5.
```c
#include<stdio.h>
int proddigits(int num);
int mdr(int s);
int main()
{
int n;
printf("Enter a number:");
scanf("%d",&n);
mdr(n);
}
int proddigits(int num)
{
int p=1;
while(num>0)
{
p*=num%10;
num/=10;
}
return p;
}
int mdr(int s)
{
int c=0;
while(s>9)
{
 int r;
r=proddigits(s);
c+=1;
s=r;
}
printf("Multiplicative persistence:%d\n",c);
printf("Multiplicative digital root:%d\n",s);
}
```
# output
```
39 3 4
```
# 6.
```c
#include<stdio.h>
int main()
{
int n;
printf("Enter a number:");
scanf("%d",&n);
for(int i=1;i<=10;i++)
{
printf("%d * %d = %d\n",n,i,n*i);
}
return 0;
}
```
# output
```
Enter a number:5
5 * 1 = 5
5 * 2 = 10
5 * 3 = 15
5 * 4 = 20
5 * 5 = 25
5 * 6 = 30
5 * 7 = 35
5 * 8 = 40
5 * 9 = 45
5 * 10 = 50
```
# 7.
```c
#include<stdio.h>
int func(int n);
int main(void)
{
printf("%d ",func(2));
printf("%d ",func(5));
printf("%d ",func(2));
}
int func(int n)
{
static int s=0;
int i;
for(i=1;i<=n;i++)
   s+=i;
return s;
}
```
# output
```
3 18 21
```
# 8.
```c
#include<stdio.h>
int func(void);
int main()
{
int i;
for(i=1;i<6;i++)
   printf("%d ",func());
return 0;
}
int func(void)
{
 int k=1;
k*=2;
return k;
} 
```
# output
```
2 2 2 2 2
```
# 9.
```c
#include<stdio.h>
void func(int a, static int b);
int main(void)
{
func(1,2);
func(3,4);
}
void func(int a, static int b)
{
a++;
b++;
printf("%d %d\n",a,b);
}
```
# output
```
Error due to static as parameter
```
# 10.
```
#include<stdio.h>
int main()
{
int i = 9;
if(i==9)
{
int i = 25;
}
printf("i=%d\n",i);
}
```
# output
```
9
```
# 11.
```c
#include<stdio.h>
int func(int k);
int main()
{
int i=0,k=3;
i+=func(k);
i+=func(k);
i+=func(k);
printf("%d\n",i);
}
int func(int k)
{
static int m=2;
m=m+k;
return m;
}
```
# output
```
24
```
# 12.
```c
#include<stdio.h>
int func(int x,int y);
int main(void)
{
int a = 2,b=5;
a=func(a+b,a-b);
printf("%d\n",a);
}
int func(int x, int y)
{
return x+y,x-y;
}
```
# output
```
10
```
# 13.
```c
#include<stdio.h>
int a = 5;
void func(void);
int main()
{
func();
printf("%d\n",a);
}
void func(void)
{
int a = 2;
printf("%d\t",a);
}
```
# output
```
2 5
```
# 14.
```c
#include<stdio.h>
void func(int a, int b);
int main(void)
{
int i=5, j =10;
func(i/2,j%3);
return 0;
}
void func(int a, int b)
{
a/=2;
b--;
printf("%d\t",a+b);
}
```
# output
```
1
```
# 15.
```c
#include<stdio.h>
int func(int a, int b, int c);
int main(void)
{
int x;
x=func(2,3,4);
printf("%d\n",x);
return 0;
}
int func(int a,int b,int c)
{
return a,b,c;
}
```
# output
```
4
```
# 16.
```c
#include<stdio.h>
int func(int a, int b);
int main(void)
{
int i=2,j=3;
printf("%d\n",func(i,j));
return 0;
}
int func(int a, int b)
{
int p;
a=a-5;
b=b+5;
p= (!a + --b);
return p;
}
```
# output
```
7
```
# 17.
```c
#include<stdio.h>
void func(void);
int main(void)
{
int i = 5;
for(i=i+1; i<8; i++)
func();
return 0;
}
void func(void)
{
int j;
for(j=1; j<3; j++)
printf("%d\t",++j);
}
```
# 18.
```c
#include<stdio.h>
void func(void);
int main(void)
{
int i = 5;
for(i=i+1; i<8; i++)
func();
return 0;
}
void func(void)
{
int j;
for(j=1; j<3; j++)
printf("%d\t",++j);
}
```
# output
```
2 2
```
# 19.
```c
#include<stdio.h>
void display(int,int);
int main()
{
int x=15;
float y=290.5;
display(x,y);
return 0;
}
void display(int a,int b)
{
printf("%d %d\n",a,b);
}
```
# output
```
15 290
```
# 20.
```c
#include<stdio.h>
int main(void)
{
int func(int a,int b)
{
return (a+b);
}
int c;
c=func(3,5);
printf("%d",c);
return 0;
}
```
# output
```
8
```
# 21.
```c
#include<stdio.h>
int square1(int a);
int square2(double a);
double square3(int a);
double square4(double a);
int main()
{
double x=2.5,y;
y=square1(x);
printf("%lf\t",y);
y=square2(x);
printf("%lf\t",y);
y=square3(x);
printf("%lf\t",y);
y=square4(x);
printf("%lf\t",y);
return 0;
}
int square1(int a)
{
return a*a;
}
int square2(double a){
return a*a;}
double square3(int a)
{
return a*a;
}
double square4(double a)
{
return a*a;
}
```
# output
```
4.000000	6.000000	4.000000	6.250000
```
# 22.
```c
#include<stdio.h>
int sum(int a,int b);
int main()
{
(void)sum(1,2);
return 0;
}
int sum(int a,int b)
{
printf("Sum is %d\n",a+b);
}
```
# output
```
Sum is 3
```
# 23.
```c
#include<stdio.h>
int func(int a,int b,int c);
int main(void)
{
int x=1,y=2,z=3,result;
result=func(x,y,(z=5,z+10));
printf("x=%d,y=%d,z=%d",x,y,z);
printf("result=%d\n",result);
return ;
}
func(int a,int b,int c)
{
return 2*(a+b+c);
}
```
# output
```
x=1,y=2,z=5 result=36
```
# 24.
```c
#include<stdio.h>
int sqr(int x);
int cube(int x);
int func(int n);
int main(void)
{
int n=5;
printf("%d\n",func(n));
return 0;
}
int sqr(int x)
{
  return x*x;
}
int cube(int x)
{
  return x*x*x;
}
int func(int n)
{
  return n+sqr(n-2)+cube(n-3);
}
```
# output
```
22
```
# 25.
```
#include<stdio.h>
int diff(int x,int y)
{ return x-y; }
int sum (int x, int y)
{ return x+y; }
int main(void)
{
int a = 20,b=5,c=2,d=6;
printf("%d\t",a+diff(d,c));
printf("%d\n",diff(a,sum(diff(b,c),d)));
return 0;
}
```
# output
```
24	11
```










