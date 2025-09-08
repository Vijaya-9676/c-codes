# 1.Printing sum of integers of a file in another file
```c
#include<stdio.h>
int main()
{
        FILE *fptr,*sptr;
        if((fptr=fopen("source.txt","r"))==NULL)
        {
                printf("Error in opening the file\n");
                return 1;
        }
        if((sptr=fopen("dest.txt","w"))==NULL)
        {
                printf("Error in opening a file\n");
                return 1;
        }
        char ch;
        int sum=0;
        while((ch=fgetc(fptr))!=EOF)
        {
                if(ch>=48 && ch<=57)
                {
                   sum+=ch-'0';
                }
        }
        fprintf(sptr,"%d",sum);
        fclose(fptr);
        fclose(sptr);
}
```
# output
```
source.txt: 1 2 3 4 5
dest.txt: 15
```
# 2.Counting no.of words in a file
```c
#include<stdio.h>
int end(char ch);
int main()
{
        char line[81];
        FILE *fptr;
        int count=0;
        if((fptr=fopen("source.txt","r"))==NULL)
        {
                printf("Error in opening file\n");
        }
        while((fgets(line,81,fptr))!=NULL)
        {
          for(int i=0;line[i]!='\0';i++)
          {
           if(end(line[i]))
           {
             count++;
           }
          }
        }
        printf("%d\n",count);
        fclose(fptr);
}
int end(char ch)
{
        if(ch==' ' || ch=='.' || ch==',' || ch==';' || ch==':' || ch=='\n' || ch== '\t')
        {       
                return 1;
        }
return 0;
}
```
# output
```
5
```
# 3.Checking if the file exists or not
```c
#include<stdio.h>
int main()
{
        FILE *fptr;
        if((fopen("source.txt","r"))==NULL)
        {
                printf("File does not exist\n");
                return 1;
        }
        printf("File exists\n");
}
```
# output
```
File exists
```
# 4.Renaming a file
```c
#include<stdio.h>
int main()
{
        if(rename("source.txt","src.txt")==0)
        {
            printf("File renamed\n");
        }
        else
        {
            printf("Error in renaming a file\n");
        } 
}
```
# output
```
File renamed
```
# 5.Handling file errors
```c
#include<stdio.h>
#include<errno.h>
#include<string.h>
int main()
{
        FILE *f=fopen("files.txt","r");
        if(!f)
        {
                printf("Error:%s\n",strerror(errno));
                return 1;
        }
        fclose(f);
}
```
# output
```
Error:No such file or directory
```
# 6.Adding line numbers in a file
```
::x



