# 1.Finding the day of thr week using the date
```c
#include<stdio.h>
int main()
{
        int d,m,y;
        int j;
        printf("Enter date:");
        scanf("%d %d %d",&d,&m,&y);
        j=d;
        switch(m-1)
        {
                case 11:j+=30;
                case 10:j+=31;
                case 9:j+=30;
                case 8:j+=31;
                case 7:j+=31;
                case 6:j+=30;
                case 5:j+=31;
                case 4:j+=30;
                case 3:j+=31;
                case 2:j+=28;
                case 1:j+=31;
        }
        if((y%100 != 0 && y%4==0)||(y%400==0))
        {
                j+=1;
        }
        int f=(y-1)/4;
        int h=(y-1)/100;
        int fh=(y-1)/400;
        int day=(y+j+f-h+fh)%7;
        switch(day)
        {
                case 0:printf("saturday");break;
                case 1:printf("sunday");break;
                case 2:printf("Monday");break;
                case 3:printf("Tuesday");break;
                case 4:printf("wednesday");break;
                case 5:printf("thursday");break;
                case 6:printf("friday");
        }
}
```
# output
```
friday
```
# 2.Printing no.of days in a given month
```c
#include<stdio.h>
int main()
{
        int m=5;
        if(m==2)
        {
                printf("28 or 29 days\n");
        }
        else
        {
        switch(m)
        {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
                printf("31");
                break;
        case 4:
        case 6:
        case 9:
        case 11:
              printf("30");
        }
        }
}
```
# output
```
31
```
# 3.Given number is prime or not
```
#include<stdio.h>
int main()
{
        int n;
        printf("enter n value:");
        scanf("%d",&n);
        int i=2;
        int count=0;
        while(i<=n/2)
        {
         if(n%i==0)
         {
                count++;
         }
         i++;
        }
        if(count>0)
        {
                printf("not a prime\n");
        }
        else
        {
                printf("prime\n");
        }
}
```
# output
```
enter n value:5
prime
```
# 4.Counting no.of words in a string using while loop
```c
#include<stdio.h>
int main()
{
        char s[]="C programming language";
        int count=0,i=0;
        while(s[i]!='\0')
        {
                if((s[i]!=' '&&s[i+1]==' ')||(s[i]!=' '&&s[i+1]=='\0'))
                {
                                 count++;
                }
                i++;
        }
        printf("%d\n",count);
}
```
# output
```
3
```
# 5.String palindrome
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char s[10];
        printf("enter a string:");
        gets(s);
        char s1[10];
        int i,j;
        int flag=0;
        for(i=strlen(s)-1,j=0;i>0,j<strlen(s);i--,j++)
        {
                s1[j]=s[i];
        }
        s1[j]='\0';
        printf("%s\n",s);
        printf("%s\n",s1);
        while(s[i]==s1[i])
        {
                if(s[i]=='\0')
                {
                        flag=1;
                }
                i++;

        }
        if(flag==1)
        {
                printf("palindrome\n");
        }
        else
        {
                printf("not a palindrome\n");
        }
}
```
# output
```
enter a string:aabbaa
aabbaa
aabbaa
palindrome
```
# 6.Concatenation of two strings using a while loop
```c
#include<stdio.h>
int main()
{
        char s1[]="sri";
        char s2[]="rupa";
        int i=0,j=0;
        while(s1[i]!='\0')
        {
                i++;
        }
        while((s1[i++]=s2[j++])!='\0')
        {
                ;
        }
        printf("%s\n",s1);
}
```
# output
```
srirupa
```
# 7.Sum of digits until a single digit
```c
#include<stdio.h>
int main()
{
        int n=12345,dig=0,sum=0;
        do
        {
                sum=0;
                while(n>0)
                {
                 dig=n%10;
                 n=n/10;
                 sum=sum+dig;
                }
                n=sum;
        }while(n/10!=0);

printf("%d\n",sum);
}
```
# output
```
6
```
# 8.LCM
```c
#include<stdio.h>
int main()
{
        int num1=15,num2=10;
        int max=0;
        int lcm;
        if(num1>num2)
        {
                max=num1;
        }
        else
        {
                max=num2;
        }
        while(1)
        {
                if(max%num1==0 && max%num2==0)
                {
                        lcm=max;
                        break;
                }
                 max++;
        }
        printf("%d\n",lcm);
}
```
# output
```
30
```
# 9.Armstrong numbers between 1 and 1000
```c
#include<stdio.h>
int main()
{
        int i,j,p=1,k,count=0,sum=0,s=1,e=1000;
        for(i=s;i<=e;i++)
        {
                int num=i;
                int temp=num;
                sum=0;
                while(num>0)
                {
                        num=num/10;
                        count++;
                }
                num=temp;
                int t=count;
                while(num>0)
                {
                        int d=num%10;
                        num/=10;
                        count=t;
                        p=1;
                        while(count>0)
                        {
                                p*=d;
                                count--;
                        }
                        sum+=p;
                }
                 if(sum==temp)
                {
                        printf("%d\n",i);
                }
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
6
7
8
9
153
370
371
407
```
# 10.Removing duplicate elements in an array
```c
#include<stdio.h>
int main()
{
        int arr[10]={1,2,3,4,3,2,5,6,1,7};
        int i,j,k,n=10;
        for(i=0;i<n;i++)
        {
                for(j=i+1;j<n;j++)
                {
                     if(arr[i]==arr[j])
                      {
                             for(k=j;k<n-1;k++)
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
        printf("\n");
}
```
# output
```
1 2 3 4 5 6 7 
```
# 11.Second lagest element in an array
```c
#include<stdio.h>
int main()
{
        int arr[10]={1,5,2,3,6,3,7,8,0,9};
        int i,j,n=10,second=arr[0],first=arr[0];
        for(i=1;i<n;i++)
        {
            if(arr[i]>first)
            {
                    second=first;
                    first=arr[i];
            }
            else if(arr[i]>second  && arr[i]!=first)
            {
                    second=arr[i];
            }
        }
        printf("%d\n",second);

}
```
# output
```
8
```
# 12.Identity matrix or not
```c
#include<stdio.h>
int main()
{
        int arr[5][5]={{1,5,0,0,0},{0,1,0,0,0},{0,0,1,0,0},{0,0,0,1,0},{0,0,0,0,1}};
        int i,j,isidentity=1;
        for(i=0;i<5;i++)
        {
                for(j=0;j<5;j++)
                {
                        if(i==j && arr[i][j]!=1)
                        {
                                isidentity=0;
                        }
                        else
                        {
                                if(i!=j && arr[i][j]!=0)
                                {
                                        isidentity=0;
                                }
                        }
                }
                if(!isidentity)
                {
                        break;
                }
        }
        if(isidentity==1)
        {
                printf("identical\n");
        }
       else
        {
                printf("not identical\n");
        }
}
```
# output
```
not identical
```
# 13.Missing element in an array
```c
#include<stdio.h>
int main()
{
        int arr[]={1,2,3,4,6,7,9,10};
        int i;
        int n=10;
        int present[n+1];
        for(i=0;i<n;i++)
        {
        present[i]=0;
        }
        for(i=0;i<n;i++)
        {
                present[arr[i]]=1;
        }
        for(i=1;i<=n;i++)
        {
                if(present[i]==0)
                {
                        printf("%d\n",i);
                }
        }
}
```
# output
```
5
8
```
# 14.Ascii value of a character using loops
```c
#include<stdio.h>
int main()
{
        char ch='v';
        for(int ascii=0;ascii<=127;ascii++)
        {
                if(ch==ascii)
                {
                        printf("%d\n",ascii);
                        break;
                }
        }
}
```
# output
```
118
```
# 15.Hallow square
```c
#include<stdio.h>
int main()
{
        int n=5;
        int i,j;
        for(i=0;i<n;i++)
        {
                for(j=0;j<n;j++)
                {
                        if(i==0 || j==0 || i==n-1 || j==n-1)
                        {
                                printf("* ");
                        }
                        else
                        {
                                printf("  ");
                        }
                }
                printf("\n");
        }
}
```
# output
```
* * * * * 
*       * 
*       * 
*       * 
* * * * * 
```
# 16.Right triangle
```c
#include<stdio.h>
int main()
{
        int n=5;
        int i,j;
        for(i=0;i<n;i++)
        {
                for(j=0;j<=i;j++)
                {
                        printf("* ");
                }
                printf("\n");
        }
}
```
# output
```
* 
* * 
* * * 
* * * * 
* * * * * 
```
# 17.Mirrored right triangle
```c
#include<stdio.h>
int main()
{
        int n=5,i,j;
        for(i=1;i<=n;i++)
        {
                for(j=1;j<=n-i;j++)
                {
                  printf(" ");
                }
                for(j=1;j<=i;j++)
                {
                        printf("*");
                }
                printf("\n");
        }
}
```
# 18.Printing pyramid using starts
```c
#include<stdio.h>
int main()
{
        int n=5;
        int i,j;
        for(i=1;i<=n;i++)
        {
                for(j=1;j<=n-i;j++)
                {
                        printf(" ");
                }
                for(j=1;j<=2*i-1;j++)
                {
                        printf("*");
                }
                printf("\n");
        }
}
```
# output
```
    *
   ***
  *****
 *******
*********
```
# 19.Reverse pyramid using stars
```c
#include<stdio.h>
int main()
{
        int n=5;
        int i,j;
        for(i=1;i<=n;i++)
        {
                for(j=1;j<=i;j++)
                {
                        printf(" ");
                }
                for(j=1;j<=2*(n-i+1)-1;j++)
                {
                        printf("*");
                }
                printf("\n");
        }
}
```
# output
```
*********
 *******
  *****
   ***
    *
```
 










        

