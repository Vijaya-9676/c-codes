# 1.Addition of n numbers using recursion 
```c
#include<stdio.h>
int add(int n);
int main()
{
int n;
printf("Enter a number:");
scanf("%d",&n);
printf("%d",add(n));
}
int add(int n)
{
if(n==0){
return 0;
}
return n+add(n-1);
}
```
# output
```
Enter a number:5
15
```
# 2.Recursive function to reverse a line of text without storing in array
```c
#include<stdio.h>
void rev(char *s);
int main()
{
char str[100];
printf("Enter a string:");
gets(str);
printf("Reversed line:");
rev(str);
}
void rev(char *s)
{
if(*s=='\0'){
return;
}
rev(s+1);
putchar(*s);
}
```
# output
```
Enter a string:programming
Reversed line:gnimmargorpVijayaLakshmi
```
 # 3.Sum of factors of a number using recursion
 ```c
#include<stdio.h>
int factor(int n,int i);
int main()
{
int n;
printf("Enter a number:");
scanf("%d",&n);
printf("sum of factors is:%d",factor(n,n-1));
}
int factor(int n,int i){
if(i==0){
return 0;
}
else if(n%i==0){
return i+factor(n,i-1);
}
factor(n,i-1);
}
```
# output
```
Enter a number:6
sum of factors is:6
```
# 4.Perfect number program using recursion
```c
#include<stdio.h>
int fact(int n,int div);
int main()
{
int n;
printf("Enter n value:");
scanf("%d",&n);
int temp=n;
if(fact(n,n-1)==temp){
printf("perfect number");
}
else{
printf("Not a perfect number");
}
}
int fact(int n,int div){
if(div==0){
return 0;
}
if(n%div==0){
return div+fact(n,div-1);
}
fact(n,div-1);
}
```
# output
```
Enter n value:20
Not a perfect number
```
# 5.Converting number to words
```c
#include<stdio.h>
void numtowords(int n);
int main()
{
int n;
printf("Enter a number:");
scanf("%d",&n);
numtowords(n);
}
void numtowords(int n){
char *words[]={"zero","one","two","three","four","five","six","seven","eight","nine"};
if(n==0){
return;
}
numtowords(n/10);
printf("%s ",words[n%10]);
}
```
# output
```
Enter a number:555
five five five V
```
# 6.Reversing a given integer
```c
#include<stdio.h>
void reverse(int n);
int main(){
int n;
printf("Enter a number:");
scanf("%d",&n);
reverse(n);
}
void reverse(int n){
if(n==0){
return;
}
printf("%d",n%10);
reverse(n/10);
}
```
# output
```
Enter a number:123
321
```
# 7.Finding remainder using recursion without using % operator
```c
#include<stdio.h>
int rem(int a,int b);
int main(){
printf("%d\n",rem(5,5));
}
int rem(int a,int b){
if(a<b){
return a;
}
rem(a-b,b);
}
```
# output
```
0
```
# 8.Finding quotient without / operator using recursion
```c
#include<stdio.h>
int quo(int a,int b);
int main(){
printf("%d\n",quo(25,5));
}
int quo(int a,int b){
static int q=0;
if(a<b){
return q;
}
quo(a-b,b);
q+=1;
}
```
# output
```
5
```
# 9.Finding the power without multiplying n times using recursion
```c
#include<stdio.h>
int power(int a,int n);
int main()
{
printf("%d\n",power(5,2));
}
int power(int a,int n)
{
if(n==0){
return 1;
}
if(n%2==0){
return power(a*a,n/2);
}
return a*power(a*a,n/2);
}
```
# output
```
25
```
# 10.Finding product of numbers by russian peasant method using recursion
```c
#include<stdio.h>
int pro(int a,int b);
int main()
{
printf("%d\n",pro(25,2));
}
int pro(int a,int b){
if(a==1){
return b;
}
if(a%2!=0){
return b+pro(a/2,b*2);
}
pro(a/2,b*2);
}
```
# output
```
50
```
# 11.Finding value of log n base 2 and log n base b
```c
#include<stdio.h>
int logbaseb(int n,int b);
int logbase2(int n);
int main()
{
printf("%d\n",logbaseb(16,3));
printf("%d\n",logbase2(16));
}
int logbaseb(int n,int b)
{
if(n<b){
return 0;
}
return 1+logbaseb(n/b,b);
}
int logbase2(int n)
{
if(n<=1){
return 0;
}
return 1+logbase2(n/2);
}
```
# output
```
2
4
```
# 12.Program to find the binomial coefficient of n,k\
```c
#include<stdio.h>
int bincof(int n,int k){
if(k==0||k==n){
return 1;
}
return bincof(n-1,k-1)+bincof(n-1,k);
}
int main()
{
int n=5,k=2;
printf("C(%d,%d) = %d\n",n,k,bincof(n,k));
}
```
# output
```
C(5,2) = 10
```
# 13.Sum of series using recursion
```c
#include<stdio.h>
#include<math.h>
double power(double x,int n) {
if(n==0){
return 1;
}
return x*power(x,n-1);
}
int factorial(int n){
if(n<=1){
return 1;
}
return n*factorial(n-1);
}
double series(double x,int n){
if(n==1){
return x;
}
int term_exp=2*n-1;
double term =power(x,term_exp)/factorial(term_exp);
if(n%2==0){
term=-term;
}
return series(x,n-1)+term;
}
int main(){
double x=2.0;
int n=5;
printf("series sum=%lf\n",series(x,n));
}
```
# output
```
series sum=0.909347
```
# 14.Pattern
```c
#include<stdio.h>
void printleft(int row,int col){
if(row==0){
return;
}
if(col<=row){
printf("%d ",col);
printleft(row,col+1);
}
else{
printf("\n");
printleft(row-1,1);
}
}
int main(){
int n=4;
printleft(n,1);
}
```
# output
```
1 2 3 4 
1 2 3 
1 2 
1 
```
# 15.Pattern
```c
#include<stdio.h>
void printright(int row,int col){
if(row==0){
return;
}
if(col<=row){
printf("%d ",row-col+1);
printright(row,col+1);
}
else{
printf("\n");
printright(row-1,1);
}
}
int main(){
int n=4;
printright(n,1);
}
```
# output
```
4 3 2 1 
3 2 1 
2 1 
1 
```
# 16.Printing 1 to n numbers using recursion
```c
#include<stdio.h>
void func(int n);
int main()
{
int num;
printf("Enter a number");
scanf("%d",&num);
func(num);
}
void func(int n)
{
if(n==0)
{
return;
}
func(n-1);
printf("%d ",n);
}
```
# output
```
Enter a number10
1 2 3 4 5 6 7 8 9 10
```
# 17.Printing sum of series of n numbers
```c
#include<stdio.h>
int series(int n);
int main()
{
int n;
printf("Enter number of terms:");
scanf("%d",&n);
printf("\b\b = %d",series(n));
}
int series(int n)
{
int s;
if(n==0)
{
return 0;
}
s=n+series(n-1);
printf("%d + ",n);
return s;
}
```
# output
```
Enter number of terms:5
1 + 2 + 3 + 4 + 5  = 15
```
# 18.Sum of digits of a number using recursion
```c
#include<stdio.h>
int sum(int n);
void digits(int m);
int main()
{
int num;
printf("Enter the number:");
scanf("%d",&num);
printf("Sum:%d\n",sum(num));
digits(num);
}
int sum(int n)
{
if(n==0){
return 0;
}
return n%10+sum(n/10);
}
void digits(int m)
{
if(m==0){
return;
}
digits(m/10);
printf("%d ",m%10);
}
```
# output
```
Enter the number:55
Sum:10
5 5
```
# 19.Printing a number in binary octal and hexadecimal
```c
#include<stdio.h>
void convert(int num,int base);
int main()
{
int n;
printf("Enter a number:");
scanf("%d",&n);
convert(n,2);
printf("\n");
convert(n,8);
printf("\n");
convert(n,16);
printf("\n");
}
void convert(int num,int base)
{
int r=num%base;
if(num==0)
{
return;
}
convert(num/base,base);
if(r<10){
printf("%d",r);
}
else{
printf("%c",r-10+'A');
}
}
```
# output
```
Enter a number:15
1111
17
F
```
# 20.Pow(a,n) using recursion
```c
#include<stdio.h>
float power(float a,int n);
int main()
{
float a,p;
int n;
printf("Enter a,n values:");
scanf("%f%d",&a,&n);
printf("%f\n",power(a,n));
}
float power(float a,int n)
{
if(n==0){
return 1;
}
return (a*power(a,n-1));
}
```
# output
```
Enter a,n values:5 3
125.000000
```
# 21.Printing factors of a number using recursion
```c
#include<stdio.h>
void pfactors(int n);
int main()
{
int n;
printf("Enter n value:");
scanf("%d",&n);
printf("The factors of n are:");
pfactors(n);
}
void pfactors(int n){
int i=2;
if(n==1){
return;
}
while(n%i!=0){
i++;
}
printf("%d ",i);
pfactors(n/i);
}
```
# output
```
Enter n value:10
The factors of n are:2 5
```
# 22.GCD of two numbers using recursion
```c
#include<stdio.h>
int gcd(int a,int b);
int main()
{
int a,b;
printf("Enter a,b values");
scanf("%i%i",&a,&b);
printf("%d",gcd(a,b));
}
int gcd(int a,int b)
{
if(b==0){
return a;
}
return gcd(b,a%b);
}
```
# output
```
Enter a,b values 10 5
5
```
# 23.Fibonacii series using recursion
```c
#include<stdio.h>
int fib(int n);
int main()
{
int n;
printf("Enter n value:");
scanf("%d",&n);
for(int i=0;i<n;i++){
printf("%d ",fib(i));
}
}
int fib(int n){
if(n==0||n==1){
return 1;
}
return (fib(n-1)+fib(n-2));
}
```
# output
```
Enter n value:5
1 1 2 3 5
```
# 24.Divisible by 9 or not
```c
#include<stdio.h>
void div(int n);
int main()
{
int n;
printf("Enter a number:");
scanf("%d",&n);
div(n);
}
void div(int n)
{
int s;
if(n==9){
printf("Divisible by 9\n");
return;
}
if(n<9){
printf("Not divisible by 9\n");
return;
}
s=0;
while(n>0)
{
s+=n%10;
/=10;
}
return (div(s));
}
```
# output
```
Enter a number:27
Divisible by 9
```
# 25.Divisible by 11 or not
```c
#include<stdio.h>
void div(int n);
int main()
{
int n;
printf("Enter n value:");
scanf("%d",&n);
div(n);
}
void div(int n){
int s1,s2,diff;
if(diff == 0 || diff == 11){
printf("divisible by 11\n");
return;
}
else{
printf("Not divisible by 11\n");
return;
}
s1=0;
s2=0;
diff=0;
while(n>0){
s1+=n%10;
n/=10;
s2+=n%10;
n/=10;
}
return (div(diff));
}
```
# output
```
Enter n value:121
divisible by 11
```
## Code Snippets
# 26.
```c
#include<stdio.h>
int main(void)
{
printf("%d %d\n",func1(3,8),func2(3,8));
}
func1(int a,int b){
if(a>b){
return 0;
}
return b+func1(a,b-1);
}
func2(int a,int b){
if(a>b)
{
return 0;
}
return a+func2(a+1,b);
}
```
# output
```
33 33
```
# 27.
```c
#include<stdio.h>
int func(int a,int b);
int main()
{
printf("%d \n",func(3,8));
}
int func(int a,int b)
{
if(a>b){
return 1000;
}
return a+func(a+1,b);
}
```
# output
```
1033
```
# 28.
```c
#include<stdio.h>
int func(int a);
int func1(int a);
int main()
{
printf("%d\n",func(6));
printf("%d\n",func1(6));
}
int func(int a)
{
if(a==10){
return a;
}
return a+func(a+1);
}
int func1(int a)
{
if(a==0){
return a;
}
return a+func1(a+1);
}
```
# output
```
40 segmentation fault
```
# 29.
```c
#include<stdio.h>
int func(int a,int b);
int main()
{
printf("%d\n",func(4,8));
printf("%d\n",func(3,8));
}
int func(int a,int b)
{
if(a==b){
return a;
}
return a+b+func(a+1,b-1);
}
```
# output
```
30 segmentation fault
```
# 30.
```c
#include<stdio.h>
void func1(int a,int b);
void func2(int a,int b);
int main()
{
func1(10,18);
printf("\n");
func2(10,18);
}
void func1(int a,int b){
if(a>b){
return;
}
printf("%d ",b);
func1(a,b-1);
}
void func2(int a,int b){
if(a>b){
return;
}
func2(a,b-1);
printf("%d ",b);
}
```
# output
```
18 17 16 15 14 13 12 11 10 
10 11 12 13 14 15 16 17 18
```
# 31.
```c
include<stdio.h>
void func1(int a,int b);
void func2(int a,int b);
int main()
{
func1(10,18);
printf("\n");
func2(10,18);
}
void func1(int a,int b){
if(a>b){
return;
}
printf("%d ",a);
func1(a+1,b);
}
void func2(int a,int b){
if(a>b){
return;
}
func2(a+1,b);
printf("%d ",a);
}
```
# output
```
10 11 12 13 14 15 16 17 18
18 17 16 15 14 13 12 11 10
```
# 32.
```c
#include<stdio.h>
int func(int a,int n);
int main()
{
printf("%d\n",func(3,8));
printf("%d\n",func(3,0));
printf("%d\n",func(0,3));
}
int func(int a,int n){
if(n==0){
return 0;
}
if(n==1){
return a;
}
return a+func(a,n-1);
}
```
# output
```
24 0 0
```
# 32.
```c
#include<stdio.h>
int count(int n);
int main()
{
printf("%d\n",count(17243));
}
int count(int n)
{
if(n==0){
return 0;
}
return 1+count(n/10);
}
```
# output
```
5
```
# 33.
```c
#include<stdio.h>
int func(int n);
int main()
{
printf("%d\n",func(14837));
}
int func(int n){
return (n)? n%10 + func(n/10) : 0;
}
```
# output
```
23
```
# 34.
```c
#include<stdio.h>
int count(long int n,int d);
int main()
{
printf("%d\n",count(123212,2));
}
int count(long int n,int d)
{
if(n==0){
return 0;
}
else if(n%10 == d){
return 1+count(n/10,d);
}
else{
return count(n/10,d);
}
}
```
# output
```
3
```
# 35.
```c
#include<stdio.h>
int f(char *s,char a);
int main(void)
{
char str[100],a;
printf("Enter a string:");
gets(str);
printf("Enter a character:");
scanf("%c",&a);
printf("%d\n",f(str,a));
return 0;
}
int f(char *s,char a)
{
if(*s=='\0')
{
return 0;
}
if(*s==a)
{
return 1+f(s+1,a);
}
return f(s+1,a);
}
```
# output
```
Enter a string:apple
Enter a character:p
2
```
# 36.
```c
#include<stdio.h>
void func1(int n);
void func2(int n);
int main()
{
func1(4);
func2(4);
}
void func1(int n)
{
int i;
if(n==0)
{
return;
}
for(i=1;i<=n;i++){
printf("*");
}
printf("\n");
func1(n-1);
}
void func2(int n){
int i;
if(n==0){
return;
}
func2(n-1);
for(i=1;i<=n;i++){
printf("*");
}
printf("\n");
}
```
# output
```
****
***
**
*
*
**
***
****
```







