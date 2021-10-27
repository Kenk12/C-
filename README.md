# C
王仕儒C语言
#include <stdio.h>
/* 当fahr= 0,20,...,300时，分别打印华氏温度与摄氏温度对照表 */
main()
{
    int fahr,celsius;
    int lower,upper,step;

        lower = 0;       /* 温度表的下限 */
        upper = 300;     /* 温度表的上限 */
        step = 20;         /*     不长     */

        fahr = lower;
        while(fahr <= upper)
        {
            celsius = 5* (fahr-32)/9;
            printf("%d\t%d\n",fahr,celsius);
            fahr=fahr+step;
        }

}

摄氏度表转化为华氏度表
#include <stdio.h>
#include <stdio.h>
/* 当fahr= 0,20,...,300时，分别打印华氏温度与摄氏温度对照表 */
main()
{
    int fahr,celsius;
    int lower,upper,step;

        lower = 0;       /* 温度表的下限 */
        upper = 148;     /* 温度表的上限 */
        step = 9;
            /*     不长     */

        fahr = lower;
        printf("温度表的标题\n");
        while(celsius<= upper)
        {
            fahr=celsius*9/5 + 32;
            printf("%d\t%d\n",fahr,celsius);
            celsius=celsius+step;
        }

}




逆向输出温度表
#include <stdio.h>
main()
{
    int fahr;
    for(fahr=300;fahr>=0;fahr-=20)
        {
            printf("%3d %6.1f\n",fahr,(5.0/9.0)*(fahr-32));
        }
}






define应用

#define 名字，替换文本

#include<stdio.h>
#define LOWER 0  /* 打印温度表的下限 */
#define UPPER 300   /* 打印温度表的上限 */
#define STEP 20   /* 步长 */

/* 打印华氏温度—摄氏温度对照表 */
main ()
{
    int fahr;
    for(fahr=LOWER;fahr<=UPPER;fahr=fahr+STEP)
        printf("%3d %6.1f\n",fahr,(5.0/9.0)*(fahr-32));
}







文件复制
#include<stdio.h>
main()
{
    int c;
    c=getchar();
    while(c!=EOF){
        putchar(c);
        c=getchar();
    }
}
#include<stdio.h>
main()
{
    int c;
    c=getchar();
    while(c!=EOF){
        putchar(c);
        c=getchar();
    }
}






统计空格，制表符，和换行符的个数


#include <stdio.h>
/* count blanks, tabs, and newlines */
main()
{
 int c,blanks,tabs,newlines;
     blanks=0;
     tabs=0;
     newlines=0;
 while(c=getchar()!=EOF){
    if(c==' ')
    ++blanks;
    else if (c=='\t')
    ++tabs;
    else if (c=='\n')
    ++newlines;
 }
    printf("%3d %3d %3d\n",blanks,tabs,newlines);

}











统计各个数字、空白符及其他字符出现的次数
#include<stdio.h>
/* 统计各个数字、空白符及其他字符出现的次数 */
main()
{
    int c,i,nwhite,nother;
    int ndigit[10];
    nwhite = nother=0;
    for(i=0;i<10;++i)
        ndigit[i]=0;
        while((c=getchar())!=EOF){
            if(c>='0' && c<='9')
            ++ndigit[c-'0'];
        else if(c==' '||c=='\t'||c=='\n')
            ++nwhite;
        else
            ++nother;
        printf("digits=");
        for(i=0;i<10;++i)
            printf("%d",ndigit[i]);
        printf(", white space =%d,other=%d\n",nwhite,nother);}
}



测试power函数
#include <stdio.h>

/* 测试power函数 */

main()
{
    int i;

    for(i=0;i<10;++i)
        printf("%d %d %d\n",i,power(2,i),power(-3,i));
        return 0;

}

int power(int base,int n)
{
    int i,p;
    p=1;
    for(i=1;i<=n;++i)
        p=p*base;
    return p;
}







1.9字符数组


#include<stdio.h>
int MAXLINE =1000;/* 允许输入行的最大长度 */

int getline(char line[],int MAXLINE);
void copy(char to[],char from[]);

/* 打印最长的输入行 */
main()
{
    int len;                             /* 当前行长度 */
    int max;                             /* 目前为止发现的最长行的长度 */
    char line[MAXLINE];                  /* 当前的输入行 */
    char longest[MAXLINE];              /* 用于保存最长的行 */

    max =0;
    while(( len= getline(line,MAXLINE))>0){
    if(len>max){
        max = len;
        copy(longest,line);
    }
    if(max>0)                          /* 存在这样的行 */
        printf("%s",longest);}
    return 0;
}

/* getline函数:将一行读入s中并返回其长度 */
int getline(char s[],int lim)
{
    int c,i;

    for(i=0;i<lim-1 &&(c=getchar())!=EOF && c!='\n';++i)
        s[i]=c;
    if(c=='\n'){
        s[i] = c;
        ++i;
    }
    s[i] ='\0';
    return i;
    }

    /* copye函数：将from复制到to；这里假定to足够大 */
    void copy(char to[],char from[])
    {
        int i;

        i=0;
        while((to[i] = from[i])!='\0')
            ++i;
    }



#include <stdio.h>
int MAXLINE=1000;                                 /* maximum input line size */

int getline(char line[],int maxline);
void copy(char to[],char from[]);

/* print longest input line */
main()
{
    int len;                                      /* current line length     */
    int max;                                      /* maximum length seen so far(目前为止) */
    char line[MAXLINE];                           /* current input line */
    char longest[MAXLINE];                        /* longest line saved here */
    max = 0;
    while((len = getline(line,MAXLINE))>0){
        printf("%d, %s",len, line);
        if(len > max){                            /* 当前长度大于历史长度 */
            max = line;
            copy(longest,line);
        }
    }
    if(max > 0)                                    /* There was a line       */
        printf("%s",longest);
    return 0;
}

/* getline: read a line into s,return length   */
int getline(char s[],int lim)
{
    int c,i,j;

    j = 0;
    for (i = 0;(c = getchar())!=EOF && c != '\n';++i)
    if(i < lim-2){
        s[j] = c;                                  /* line still in boudaries */
        ++j;
    }
    if(c =='\n'){
        s[j] = c;
        ++i;
        ++j;
    }
    s[j] = '\0';
    return i;
}
/* copy:copy 'from' into 'to';assume(假设) to is big enough */
void copy(char to[], char from[])
{
    int i;

    i = 0;
    while((to[i] = from[i])!= '\n')
        ++i;
}
