'''c
##length of largest substring without repeating characters 
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
