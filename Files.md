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
```c
#include<stdio.h>
int main()
{
        char line[50];
        FILE *fptr,*dptr;
        if((dptr=fopen("dest.txt","w"))==NULL)
        {
                printf("Error in opening a file\n");
                return 1;
        }
        if((fptr=fopen("source.txt","r+"))==NULL)
        {
                printf("Error in opening a file\n");
                return 1;
        }
        int lineNo=1;
        while((fgets(line,50,fptr))!=NULL)
        {
                fprintf(dptr,"%d %s",lineNo,line);
                lineNo++;
        }
        fclose(fptr);
        fclose(dptr);
}
```
# output
```
source.txt:
Hi
Hello
How are you
where are you from
dest.txt:
1 Hi
2 Hello
3 How are you
4 where are you from
```
 # 7.Program to remove a specified line in a file using a temp file
 ```c
#include<stdio.h>
int main()
{
FILE *fptr,*tptr;
int lineNo=1;
int n;
char line[50];
if((fptr=fopen("src.txt","r"))==NULL)
{
        printf("Error in opening a file\n");
        return 1;
}
if((tptr=fopen("dest.txt","w"))==NULL)
{
        printf("Error in opening a file\n");
        return 1;
}
printf("Enter line number:");
scanf("%d",&n);
while((fgets(line,50,fptr))!=NULL)
{
        if(lineNo!=n)
        {
                fprintf(tptr,"%s",line);

        }
        lineNo++;
}
fclose(fptr);
fclose(tptr);
remove("src.txt");
rename("dest.txt","src.txt");
}
```
# output
```
Enter line number:2
src.txt:
Hi
Hello
How are you
where are you from
src.txt:
Hi
How are you
where are you from
```
# 8.Moving the file pointer to the end of the file and determining the file size
```c
#include<stdio.h>
int main()
{
        FILE *fptr;
        int c=0;
        char ch;
        if((fptr=fopen("file.txt","r"))==NULL)
        {
                printf("Error in opening a file\n");
                return 1;
        }
        fseek(fptr,0,2);
        printf("%ld\n",ftell(fptr));
}
```
# output
```
abcdefg
8
```
# 9.Printing last n lines of a file
```
include<stdio.h>
#include<stdlib.h>
#include<string.h>
int main()
{
        FILE *fptr=fopen("file.txt","r");
        char *lines[100];
        int count=0,n;
        while(!feof(fptr))
        {
                lines[count]=malloc(200);
                if(fgets(lines[count],200,fptr))
                {
                        count++;
                }
        }
        printf("Enter n value:");
        scanf("%d",&n);
        for(int i=count-n;i<count;i++)
        {
                printf("%s",lines[i]);
        }
        fclose(fptr);
}
```
# output
```
file.txt:
tirumala
engineering
college
narasaraopet
programming
this
is
an
umberella
Enter n value:3
is 
an
umberella
```
# 10.Searching a string in a file
```c
#include<stdio.h>
#include<string.h>
int main()
{
        FILE *fptr=fopen("file.txt","r");
        if(fptr==NULL)
        {
                printf("Error in opening a file\n");
                return 1;
        }
        char word[100];
        printf("Enter a word:");
        scanf("%s",word);
        char line[100];
        int count=1;
        while(fgets(line,sizeof(line),fptr))
        {

                if(strstr(line,word))
                {
                        printf("word found at line:%d\n",count);
                }
                count++;
        }
        fclose(fptr);
}
```
# output
```
Enter a word:this
word found at line:6
```
# 11.Appending data in a file
```
#include<stdio.h>
int main()
{
        FILE *fptr=fopen("file.txt","a");
        char data[50];
        printf("Enter data:");
        scanf("%s",data);
        fprintf(fptr,"%s",data);
        fclose(fptr);
}
```
# output
```
tirumala
engineering
college
narasaraopet
programming
this
is
an
umberella
rainbow
```
# 12.Append date and time in a file
```c
#include<stdio.h>
#include<time.h>
int main()
{
        FILE *fptr=fopen("file.txt","a");
        time_t t = time(NULL);
        fprintf(fptr,"Run at:%s",ctime(&t));
        fclose(fptr);
}
```
# output
```
tirumala
engineering
college
narasaraopet
programming
this
is
an
umberella
rainbowRun at:Mon Sep  8 15:38:55 2025
```
# 13.To input text and append it to a file until they enter "exit"
```c
#include<stdio.h>
#include<string.h>
int main()
{
        FILE *fptr=fopen("file.txt","a");
        if(!fptr)
        {
                printf("Error in opening a file");
                return 1;
        }
        char line[100];
        while(1)
        {
                fgets(line,sizeof(line),stdin);
                if(!strstr(line,"exit"))
                {                       
                      fprintf(fptr,"%s",line);
                }
                else if(strstr(line,"exit"))
                {
                        break;
                }
        }
        fclose(fptr);
}
```
# output
```
true
false
boolean
exit
file.txt:
narasaraopet
programming
umberella
rainbow
true
false
boolean
```
# 14.Compressing a string in a file 
```c
include<stdio.h>
int main()
{
        FILE *in=fopen("input.txt","r");
        FILE *out=fopen("compressed.txt","w");
        char c,prev;
        int count=1;
        prev=fgetc(in);
        while((c=fgetc(in))!=EOF)
        {
                if(c==prev) count++;
                else
                {
                        fprintf(out,"%d%c",count,prev);
                        prev=c;
                        count=1;
                }
        }
        fprintf(out,"%d%c",count,prev);
        fclose(in);
        fclose(out);
}
```
# output
```
file1.txt
aaabbbbccdee
file2.txt:
3a4b2c1d2e1
```









