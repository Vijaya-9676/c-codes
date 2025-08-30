# 1.Bit is set or not
```c
#include<stdio.h>
int main()
{
        int  num=10;
        int p=1;
        if(num&(1<<p))
        {
                printf("the bit is set\n");
        }
        else
        {
                printf("The bit is not a set\n");
        }
}
```
# output
```
the bit is set
```
# 2.Swapping nibbles in a 8 bit integer
```c
#include<stdio.h>
int main()
{
        unsigned char n=0X12;
        unsigned char swapped;
        swapped=(((n&0X0F)<<4) | ((n&0XF0)>>4));
        printf("0X%02X\n",swapped);
}
```
# output
```
0x21
```
# 3.swapping bytes in a 16 bit integer
```c
#include<stdio.h>
int main()
{
        unsigned short num=0X1234;
        unsigned short swap=(((num&0X00FF)<<8)|((num&0XFF00)>>8));
        printf("0X%04X\n",swap);
}
```
# output
```c
0x3412
```
# 4.Swapping bytes in a 32 bit integer
```c
#include<stdio.h>
int main()
{
        unsigned int num=0X12345678;
        unsigned int swap;
        swap = (((num&0X000000FF)<<24)|((num&0X0000FF00)<<8)|((num&0X00FF0000)>>8)|((num&0XFF000000)>>24));
        printf("0X%08X\n",swap);
}
```
# output
```
0X78563412
```
# 5.Given number is odd or even
```c
#include<stdio.h>
int main()
{
        int n=20;
        if(n&1)
        {
        printf("0dd\n");
        }
        else
        {
                printf("even\n");
        }
}
```
# output
```
even
```
# 6 clearing right most bit of a number
```c
#include<stdio.h>
int main()
{
        int n=7;
        int mask=n&~(1);
        printf("%d\n",mask);
}
```
# output
```c
6
```
# 7.Power of 2
```c
#include<stdio.h>
int main()
{
        int n=16;
        if((n>0)&&((n&(n-1))==0))
        {
        printf("%d is a power of 2\n",n);
        }
        else
        {
        printf("%d is not  power of 2\n",n);
        }
}
```
# output
```
16 is a power of 2
```
# 8.counting the no.of set bits in a number
```c
#include<stdio.h>
int main()
{
        int n=32;
        int count=0;
        while(n>0)
        {
                if(n&1)
                {
                        count++;
                }
                n=n>>1;
        }
printf("%d\n",count);
}
                                or
#include<stdio.h>
int main()
{
        int num,count=0;
        printf("Enter a number:");
        scanf("%d",&num);
        while(num)
        {
                num=num&(num-1);
                count++;
        }
        printf("%d\n",count);
}
```
# output
```
1
```
# 9.Swapping the given 2 bits in a number */
```c
#include<stdio.h>
int main()
{
        int n=9;
        int i=1,j=3;
        if(((n>>i)&1)!=((n>>j)&1))
        {
                n^=(1<<i);
                n^=(1<<j);
        }
printf("%d\n",n);
}
```
# output
```
3
```
# 10.Swapping adjacent bits of a number
```c
#include<stdio.h>
int main()
{
        unsigned int n=10;
        unsigned int even=(n&0XAAAAAAAA);
        unsigned int odd=(n&0X55555555);
        unsigned int res=((even>>1)|(odd<<1));
        printf("%u\n",res);
}
```
# output
```
5
```
# 11.Given number is less than 50 or not
```c
#include<stdio.h>
int main()
{
        int n=30;
        if((n-50)>>31)
        {
                printf("%d is less than 50\n",n);
        }
        else
        {
                printf("%d is greater than 50\n",n);
        }
}
```
# output
```
30 is less than 50
```
# 12.Given number is binary palindrome or not
```c
#include<stdio.h>
int main()
{
        int rev=0;
        int n=5;
        int temp=n;
        while(n>0)
        {
                rev=(rev<<1)|(n&1);
                n>>=1;
        }
        if(rev==temp)
        {
                printf("%d is a binary palindrome\n",temp);
        }
        else
        {
                printf("%d is not a binary palindrome\n",temp);
        }
}
```
# output
```
5 is a binary palindrome
```
# 13.Program to shift n bits to left
```c
include<stdio.h>
int main()
{
int n=1;
int d=2;
int b_width=32;
d=d%b_width;
int result=(n<<d)|(n>>(b_width-d));
printf("%d\n",result);
}
```
# output 
```
4
```
# 14.Given number has alternative set bits or not
```c
#include<stdio.h>
int main()
{
        int n=10;
        int x=n^(n>>1);
        if((x&(x+1))==0)
        {
                printf("%d has alternate set bits\n",n);
        }
        else
        {
                printf("%d does not have alternate set bits\n",n);
        }
}
```
# output
```
10 has alternative set bits
```
# 15.No.of bits to change from a to b 
```c
#include<stdio.h>
int main()
{
        int a=8;
        int b=7;
        int count=0;
        int n=a^b;
        while(n>0)
        {
                if(n&1)
                {
                        count++;
                }
                n=n>>1;
        }
        printf("%d\n",count);
}
```
# output
```
4
```
# 16.Power of 4 or not
```c
#include<stdio.h>
int main()
{
        int n=16;
        if((n>0)&&((n&(n-1))==0)&&(n&0X55555555))
        {
                printf("%d is a power of 4\n",n);
        }
        else
        {
                printf("%d is not a power of 4\n",n);
        }
}
```
# output
```
16 is power of 4
```
# 17.Perfect square or not
```c
#include<stdio.h>
int isperfectsquare(unsigned int num);
int main()
{
        int n;
        printf("enter n value:\n");
        scanf("%d",&n);
        if(isperfectsquare(n))
        {
                printf("Perfect square\n");
        }
        else
        {
                printf("Not a perfect square\n");
        }
}
int isperfectsquare(unsigned int num)
{
        if(num<0)
        {
                return 0;
        }
        int res=0;
        int bit=1<<15;
        while(bit>0)
        {
                res |= bit;
                if(res*res>num)
                {
                        res^=bit;
                }
                bit>>=1;
        }
        return (res*res==num);
}
```
# output
```
enter n value:
20
Not a perfect square
```
# 18.Swapping first and last bits of a number
```c
#include<stdio.h>
int msbpos(int n);
int swap(int n);
int main()
{
        int n=10;
        printf("%d\n",swap(n));
}
int msbpos(int n)
{
        int pos=-1;
        while(n>0)
        {
                n=n>>1;
                pos++;
        }
        return pos;
}
int swap(int n)
{
        int mpos=msbpos(n);
        if(mpos==0)
        {
                return n;
        }
        int msb=(n>>mpos)&1;
        int lsb=n&1;
        if(msb!=lsb)
        {
                n=n^(1<<mpos);
                n=n^1;
        }
        return n;
}
```
# output
```
3
```
# 19.Power of 8
```c
#include<stdio.h>
int pow8(int n);
int main()
{
int n=64;
if(pow8(n))
{
        printf("%d is power of 8\n",n);
}
else
{
        printf("%d is not power of 8\n",n);
}
}
int pow8(int n)
{
        if(n==0||(n&(n-1)!=0))
        {
        return 0;
        }
        int pos=0;
        while((n&1)==0)
        {
        n=n>>1;
        pos++;
        }
        return (pos%3==0);
}
```
# output
```
64 is power of 8
```
# 20.Power of 16 or not
```c
#include<stdio.h>
int pow16(int n);
int main()
{
int n=10;
if(pow16(n))
{
        printf("%d is power of 16\n",n);
}
else
{
        printf("%d is not a power of 16\n",n);
}
}
int pow16(int n)
{
        if(n==0 || ((n&(n-1))!=0))
        {
                return 0;
        }
        int pos=0;
        while((n&1)==0)
        {
                n=n>>1;
                pos++;
        }
        return (pos%4==0);
}
```
# output
```
10 is not a power of 16
```
# 21.To set odd bits of a number
```c
#include<stdio.h>
int main()
{
        int n=5;
        int odd=(n|0XA);
        printf("%d\n",odd);
}
```
# output
```
15
```
# 22.To toggle odd bits of a number
```c
#include<stdio.h>
int main()
{
        int n=10;
        printf("%u\n",n^0XA);
}
```
# output
```
0
```
# 23.Adding without using + operator
```c
#include<stdio.h>
int main()
{
        int a=5;
        int b=4;
        while(b!=0)
        {
                int carry=(a&b)<<1;
                a=a^b;
                b=carry;
        }
        printf("%d\n",a);
}
```
# output
```
9
```
# 24.Subtracting without - operator
```c
#include<stdio.h>
int main()
{
        int x,y;
        printf("Enter x and y values:");
        scanf("%d %d",&x,&y);
        while(y!=0)
        {
                int borrow = (-x) & y;
                x = x^y;
                y = borrow<<1;
        }
        printf("%d\n",x);
}
```
# output
```
Enter x and y values:5 2
3
```
# 25.Multiplication without using * operator
```c
#include<stdio.h>
int main()
{
        int a,b,result=0;
        printf("Enter a and b values:");
        scanf("%d %d",&a,&b);
        while(b)
        {
                if(b&1)
                {
                        result+=a;
                }
                a<<=1;
                b>>=1;
        }
        printf("%d\n",result);
}
```
# output
```
Enter a and b values:5 3
15
```
# 26.Sparse or not




        











