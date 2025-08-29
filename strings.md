# 1.length of largest substring without repeating characters 
```c
#include<stdio.h>
#include<string.h>
int lengthoflargestsubstring(char *s);
int main()
{
        char str[]="hihelloworld";
        int l=lengthoflargestsubstring(str);
        printf("%d\n",l);
}
int lengthoflargestsubstring(char *s)
{
        int maxlength=0,length=0,start=0;
        int index[256]={0};
        int i=0;
        for(i=0;s[i];i++)
        {
                if(index[(unsigned char)s[i]]>start)
                {
                        start=index[(unsigned char)s[i]];
                }
                length=i-start+1;
                if(length>maxlength)
                {
                   maxlength=length;
                }
                index[(unsigned char)s[i]]=i+1;
        }
        return maxlength;
}
```
# output
```
5
```
# 2.length of longest coomon subsequence  
```c
#include<stdio.h>
#include<string.h>
int lcslength(char *str1,char *str2);
int max(int a,int b);
int main()
{
        char str1[]="babbab";
        char str2[]="abaaba";
        int len=lcslength(str1,str2);
        printf("%d\n",len);
}
int lcslength(char *str1,char *str2)
{
        int m=strlen(str1);
        int n=strlen(str2);
        int dp[m+1][n+1];
        int i,j;
        for(i=0;i<=m;i++)
        {
                for(j=0;j<=n;j++)
                {
                        if(i==0 || j==0)
                        {
                                dp[i][j]=0;
                        }
                        else if(str1[i-1]==str2[j-1])
                        {
                                dp[i][j]=dp[i-1][j-1]+1;
                        }
                        else
                        {
                                dp[i][j]=max(dp[i-1][j],dp[i][j-1]);
                        }
                }
        }
        return dp[m][n];
}
int max(int a,int b)
{
        return (a>b?a:b);
}
```
# output
```
4
```
# 3.longest palindromic substring 
```c
#include<stdio.h>
#include<string.h>
void palsubstring(char *str,char *result);
int main()
{
        char str[100],result[100];
        fgets(str,sizeof(str),stdin);
        str[strcspn(str,"\n")]='\0';
        palsubstring(str,result);
        printf("%s\n",result);
}
void palsubstring(char *str,char *result)
{
        int start=0;
        int len=strlen(str);
        int maxlen=1;
        int i;
        for(i=0;i<len;i++)
        {
                int low=i-1;
                int high=i+1;
                while(low>=0 && high<len && str[low]==str[high])
                {
                        if(high-low+1>maxlen)
                        {
                                start=low;
                                maxlen=high-low+1;
                        }
                        low--;
                        high++;
                }
                low=i;
                high=i+1;
                while(low>=0 && high<len && str[low]==str[high])
                {
                        if(high-low+1>maxlen)
                        {
                                start=low;
                                maxlen=high-low+1;
                        }
                        low--;
                        high++;
                }
        }
        strncpy(result,str+start,maxlen);
        result[maxlen]='\0';
}
```
# output
```c
Enter string:abcdabcbadefgh
dabcbad
```
# 4.Bracket validation in a given string
```c
#include<stdio.h>
#include<string.h>
#define MAX 100
int validate(char *str);
int ismatch(char open,char close);
void push(char ch);
char pop();
int top=-1;
char stack[100];
int main()
{
        char str[100];
        printf("Enter a string:");
        fgets(str,sizeof(str),stdin);
        str[strcspn(str,"\n")]='\0';
        if(validate(str))
        {
                printf("Valid String\n");
        }
        else
        {
                printf("Not a valid string\n");
        }
}
int validate(char *str)
{
        for(int i=0;str[i]!='\0';i++)
        {
                char ch=str[i];
                if(ch=='{' || ch=='[' || ch=='(' || ch=='<')
                {
                        push(ch);
                }
                else if(ch=='}' || ch==']' || ch==')' || ch=='>')
                {
                        char open=pop();
                        if(!ismatch(open,ch))
                        {
                           return 0;
                        }
                }
        }
        return (top==-1);
}
void push(char ch)
{
   if(top<MAX-1)
   {
    stack[++top]=ch;
   }
}
char pop()
{
   if(top>=0)
   {
      return stack[top--];
   }
 return '\0';
}
int ismatch(char open,char close)
{
        return ((open=='{' && close=='}')||
                (open=='(' && close==')')||
                (open=='[' && close==']')||
                (open=='<' && close=='>'));
}
```                
# output
```c
Enter a string:{([<>])}
Valid String
```

                               


