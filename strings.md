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
```
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
```
Enter a string:{([<>])}
Valid String
```
# 5.sorting the words in a string 
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char str[10][100],temp[100];
        int n;
        printf("enter no.of strings:");
        scanf("%d",&n);
        getchar();
        int i;
        for(i=0;i<n;i++)
        {
                printf("Enter string :");
                gets(str[i]);
        }
        int j;
        for(i=0;i<n-1;i++)
        {
                for(j=i+1;j<n;j++)
                {
                        if(strcmp(str[i],str[j])>0)
                        {
                                strcpy(temp,str[i]);
                                strcpy(str[i],str[j]);
                                strcpy(str[j],temp);
                        }
                }
        }
        for(i=0;i<n;i++)
        {
                printf("%s ",str[i]);
        }
}
```
# output
```
Enter no.of strings:4
Enter string :Telugu
Enter string :Hindi
Enter string :English
Enter string :Maths
English Hindi Maths Telugu
```
# 6.string comparision using pointers using pointers
```c
#include<stdio.h>
int pstrcmp(char *s1,char *s2);
int main()
{
char *s1="anu";
char *s2="anu";
printf("%d\n",pstrcmp(s1,s2));
}
int pstrcmp(char *s1,char *s2)
{
while(*s1==*s2)
{
if(*s1=='\0')
{
return 0;
}
s1++;
s2++;
}
```
# output
```
0
```
# 7.copying a string into another using pointers 
```c
#include<stdio.h>
char *pstrcpy(char *s1,char *s2);
int main()
{
char *s2="abcd";
char *s1;
pstrcpy(s1,s2);
printf("%s\n",s1);
}
char *pstrcpy(char *s1,char *s2)
{
while((*s1=*s2)!='\0')
{
s1++;
s2++;
}
return s1;
}
```
# output
```
abcd
```
# 8.string concatenation using pointers 
```c
#include<stdio.h>
char *pstrcat(char *str1,char *str2);
int main()
{
char str1[]="Data";
char str2[]="Base";
printf("%s\n",pstrcat(str1,str2));
}
char *pstrcat(char *str1,char *str2)
{
char *p=str1;
while(*p!='\0')
{
p++;
}
while(*p++=*str2++)
{
;
}
return str1;
}
```
# output
```
DataBase
```
# 9.first non repeating character in a string 
```c
#include<stdio.h>
#include<string.h>
int firstNR(char str[]);
int main()
{
char str[30]="Suresh Kumar Srivastava";
printf("%d\n",firstNR(str));
}
int firstNR(char str[])
{
int i,flag=0,j;
int end=strlen(str)-1;
for(i=0;i<end;i++)
{
for(j=i+1;j<=end;j++)
{
flag=0;
if(str[i]==str[j])
{
flag=1;
break;
}
}
if(flag==0)
{
return i;
}
}
return -1;
}
```
# output
```
3
```
# 10.Frequency of each character in a string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char str[100];
        int freq[256]={0};
        printf("Enter a string:");
        fgets(str,sizeof(str),stdin);
        str[strcspn(str,"\n")]='\0';
        int i;
        for(i=0;str[i]!='\0';i++)
        {
                freq[(unsigned char)str[i]]++;
        }
        for(i=0;i<256;i++)
        {
                if(freq[i]>0)
                {
                        printf("count of %c is %d\n",i,freq[i]);
                }
        }
}
```
# output
```
Enter a string:Embedded
count of E is 1
count of b is 1
count of d is 3
count of e is 2
count of m is 1
```
# 11.count of words in a given string
```c
#include<stdio.h>
int main()
{
        char str[100];
        printf("Enter a string:");
        fgets(str,sizeof(str),stdin);
        int inword=0,count=0,i=0;
        while(str[i])
        {
                if(str[i]==' ')
                {
                        inword=0;
                }
                else if(inword==0)
                {
                        inword=1;
                        count++;
                }
                i++;
        }
        printf("count of words in the string:%d\n",count);
}
                            OR
#include<stdio.h>
#include<string.h>
int main()
{
char s[]="good food";
int len=strlen(s),count=0;
for(int i=0;i<len;i++)
{
        if((s[i]!=' '&&s[i+1]==' ')||(s[i]!=' '&&s[i+1]=='\0'))
        {
           count++;
        }
}
printf("%d\n",count);
}
```
# output
```
Enter a string:Vijaya Lakshmi
count of words in the string:2
```
# 12.Removing particular word from a string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char str[100],word[50],temp[100],result[100]="";
        printf("Enter a string:");
        fgets(str,sizeof(str),stdin);
        str[strcspn(str,"\n")]='\0';
        printf("Enter the word to be removed:");
        fgets(word,sizeof(word),stdin);
        word[strcspn(word,"\n")]='\0';
        int i=0,j=0,k=0;
        while(str[i])
        {

                while(str[i]==' ')
                {
                        result[j++]=str[i++];
                }
                k=0;
                while(str[i]!=' ' && str[i]!='\0')
                {
                        temp[k++]=str[i++];
                }
                temp[k]='\0';
                if((strcmp(temp,word))!=0)
                {
                        strcat(result,temp);
                        j=strlen(result);
                }
        }
        strcpy(str,result);
         printf("%s\n",str);
}
```
# output
```
Enter a string:This is c programming
Enter the word to be removed:is
This  c programming
```
# 13.High frequency character in a string 
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char str[100]="latha likes cooking oo";
        char maxchar;
        int freq[256]={0};
        int i,maxfreq=0;
        for(i=0;str[i]!='\0';i++)
        {
                freq[(unsigned char)str[i]]++;
        }
        for(i=0;i<256;i++)
        {
                if(freq[i]>maxfreq)
                {
                        maxfreq=freq[i];
                        maxchar=i;
                }
        }
        printf("maximum frequency char:%c\n",maxchar);
}       
```                               
# output
```
maximum frequency char:o
```
# 14.Removing a particular character from a string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char str[100]="programming";
        int i,j=0;
        char s[50];
        char ch='a';
        for(i=0;str[i]!='\0';i++)
        {
                if(str[i]!=ch)
                {
                        s[j++]=str[i];
                }
        }
        printf("%s\n",s);
}
```
# output
```
progrmming
```
# 15.Sorting a string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char s[]="AppLe";
        int len=strlen(s);
        for(int i=0;i<len-1;i++)
        {
          for(int j=0;j<len-i-1;j++)
          {
                  if(s[j]>s[j+1])
                  {
                          char temp=s[j];
                          s[j]=s[j+1];
                          s[j+1]=temp;
                  }
          }
        }
        printf("%s\n",s);
}
```
# output
```
ALepp
```
# 16.Length of a string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char s[50];
        fgets(s,sizeof(s),stdin);
        s[strcspn(s,"\n")]='\0';
        printf("%s",s);
        int i=0;
        while(s[i]!='\0')
        {
                i++;
        }
        printf("%d\n",i);
}
```
# output
```
vijaya
6
```
# 17.Reversing a string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char s[]="preethi";
        int len=strlen(s);
        for(int i=len-1;i>=0;i--)
        {
                printf("%c\n",s[i]);
        }
}
```
# output 
```
code
edoc
```
# 18.Extracting a substring from the given string
```c
#include<stdio.h>
#include<string.h>
void extract(char *str,int start,int length,char *res);
int main()
{
        char str[]="Hello, World!";
        int start=7;
        int length=5;
        char substr[100];
        extract(str,start,length,substr);
        printf("Extrcted substring: %s\n",substr);
}
void extract(char *str,int start,int length,char *res)
{
        int i;
        for(i=0;i<length,str[start+i]!='\0';i++)
        {
         res[i]=str[start+i];
        }
        res[i]='\0';
}
```
# output
```
Extrcted substring: World!
```
# 19.Finding if the given substring is present in the string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char str[100]="world war peace";
        char substr[100]="pea";
        if(strstr(str,substr)!=NULL)
        {
                printf("%s found\n",substr);
        }
        else
        {
                printf("string not found");
        }
}
```
# 20.Finding the presence of substring in a string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char str[100]="world war peace";
        char substr[100]="pea";
        if(strstr(str,substr)!=NULL)
        {
                printf("%s found\n",substr);
        }
        else
        {
                printf("string not found");
        }
}
```
# output
```
pea found
```
# 21.Reversing the positions of words in a string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char str[]="viven embedded academy";
        int i=0,j=0;
        int end=strlen(str)-1;
        for(i=end;i>=0;i--)
        {
                if(str[i]==' ')
                {
                        for(j=i+1;j<=end;j++)
                        {
                                printf("%c",str[j]);
                        }
                        printf(" ");
                        end=i-1;
                }
        

        }
        for(j=0;j<=end;j++)
        {
                printf("%c",str[j]);
        }
        printf("\n");
}
```
# output
```
Language Programming C
```
# 22.Reversing each word in a string
```c
#include<stdio.h>
#include<string.h>
int main()
{
        char str[]="viven embedded academy";
        int i=0,j=0;
        int len=strlen(str);
        int end=len-1;
        int start=0;
        while(str[i]!='\0')
        {
                if(str[i]!=' ')
                {
                   i++;
                }
                else
                {
                for(j=i-1;j>=start;j--)
                {
                        printf("%c",str[j]);
                }
                printf(" ");
                i++;
                start=i;
                }
        }
        printf("\n");
}
```
# output
```
neviv deddebme
```



