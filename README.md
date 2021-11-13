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


#include<stdio.h>
int month;
int main(){

scanf("%d", &month);
switch ( month )
{
    case 1: printf("January\n");
    break;
    case 2: printf("February\n");
    break;
    case 3: printf("March\n");
    break;
    case 4: printf("April\n");
    break;
    case 5: printf("May\n");
    break;
    case 6: printf("June\n");
    break;
    case 7: printf("July\n");
    break;
    case 8: printf("August\n");
    break;
    case 9: printf("September\n");
    break;
    case 10: printf("October\n");
    break;
    case 11: printf("November\n");
    break;
    case 12: printf("December\n");
    break;
    return 0;

}

}


//算平均数
#include <stdio.h>

int main()
{
    int number;
    int sum = 0;
    int count = 0;
    scanf("%d",&number);
    while ( number != -1)
        {
        sum += number;
        count ++;
        scanf("%d",&number);
        }

        printf("%f\n", 1.0*sum/count);

        return 0;
}

//猜数
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    srand(time(0));
    int number = rand()%100 + 1;
    int count = 0;
    int a = 0;
    printf("我已经想好了一个1到100之间的数。\n");
    do{
        printf("猜猜这个1到100之间数：");
        scanf("%d",&a);
        count ++;
        if( a > number){
            printf("你猜的数大了。");
        }else if ( a < number ){
        printf("你猜的数小了。");
        }
        }while(a != number);
        printf("太好了,你用了%d次就猜到了答案。\n",count);
}
#include<stdio.h>
int main()
{
    int x;
    scanf("%d",x);
    //x = 12345;
    int digit;
    int ret = 0;

    while (x>0){
        digit = x%10;
        ret = ret*10 + digit;
        printf("x=%d,digit=%d,ret=%d\n",x,digit,ret);
        x /= 10;

    }
    printf("%d",ret);
    printf("helloworld");
    return 1;
}

//F(n) = 1 + 1/2 + 1/3 +.......++1/n  前n项求和

#include <stdio.h>

int main()
{
    int n;
    int i;
    double sum = 0.0;
    
    scanf("%d",&n);
    for( i = 1; i <=n; i++)
        {
            sum += 1.0/i;
        }
    
    return 0;
}
//F(n) = 1 + 1/2 + 1/3 +.......++1/n  前n项求和

#include <stdio.h>

int main()
{
    int n;
    int i;
    double sum = 0.0;
    double sign = 1.0;
    
    scanf("%d",&n);
    for( i = 1; i <=n; i++ )
        {
            sum += sign/i;
            sign = -sign;
        }
        printf("f(%d)=%f\n",n,sum);
    
    return 0;
}

//从嵌套的循环中和跳出
#include <stdio.h>

int main()
{
    int x;
    int one , two, five;

    scanf("%d", &x);
    for ( one = 1; one < x*10; one++)
        {
            for( two = 1; two <x*10/2; two++)
                {
                    for( five =1; five <x*10/5; five++)
                        {
                            if( one + two*2 + five*5)
                                {
                                    printf("可以用%d个1加%d个2角加%d个5角得到%d元\n",one,two,five,x);
                                }
                        }
                }
        }
        return 0;
}


//从嵌套的循环中和跳出
#include <stdio.h>

int main()
{
    int x;
    int one , two, five;
    int exit = 0;

    scanf("%d", &x);
    for ( one = 1; one < x*10; one++)
        {
            for( two = 1; two <x*10/2; two++)
                {
                    for( five =1; five <x*10/5; five++)
                        {
                            if( one + two*2 + five*5)
                                {
                                    printf("可以用%d个1加%d个2角加%d个5角得到%d元\n",one,two,five,x);
                                    exit = 1;
                                    break;
                                }
                        }if( exit == 1 ) break;
                }if( exit == 1 ) break;
        }
        return 0;
}

//从嵌套的循环中和跳出
#include <stdio.h>

int main()
{
    int x;
    int one , two, five;
    int exit = 0;

    scanf("%d", &x);
    for ( one = 1; one < x*10; one++)
        {
            for( two = 1; two <x*10/2; two++)
                {
                    for( five =1; five <x*10/5; five++)
                        {
                            if( one + two*2 + five*5)
                                {
                                    printf("可以用%d个1加%d个2角加%d个5角得到%d元\n",one,two,five,x);
                                    exit = 1;
                                    break;
                                }
                        }if( exit == 1 ) break;
                }if( exit == 1 ) break;
        }
        return 0;
}

#include <stdio.h>                     /* 整数逆序 */
int main()
{
    int x ;
    scanf("%d",&x);
    int mask = 1;
    int t = x;

    while( t>9 )
        {
            t /= 10;
            mask *=10;
        }

#include<stdio.h>

int main()
{
    scanf("%d", &x);
    int cnt = 0;
    do{
        x /= 10;
        cnt++;
        
    } while( x > 0 );
    printf("cnt = %d\n", cnt);
    int mask = pow(10, cnt-1);
    int mask = 10000;
    do{
        int d = x / mask;
        printf("%d", 9);
        if( mask > 9 ){
            printf(" ");
        }
        x %= mask;
        mask /= 10;
    }while ( mask > 0);
}
        printf("x=%d，mask=%d\n",x,mask);
        do{
            int d = x / mask;
            printf("%d", d);
            if ( mask > 9 ){
                printf(" ");
            }
            x %= mask;
            mask /= 10;
          } while ( mask > 0);
          printf("\n");
}
#include <stdio.h>                     /* 整数逆序 */
int main()
{
    int x ;
    scanf("%d",&x);
    int mask = 1;
    int t = x;

    while( t>9 )
        {
            t /= 10;
            mask *=10;
        }

#include<stdio.h>

int main()
{
    scanf("%d", &x);
    int cnt = 0;
    do{
        x /= 10;
        cnt++;
        
    } while( x > 0 );
    printf("cnt = %d\n", cnt);
    int mask = pow(10, cnt-1);
    int mask = 10000;
    do{
        int d = x / mask;
        printf("%d", 9);
        if( mask > 9 ){
            printf(" ");
        }
        x %= mask;
        mask /= 10;
    }while ( mask > 0);
}
        printf("x=%d，mask=%d\n",x,mask);
        do{
            int d = x / mask;
            printf("%d", d);
            if ( mask > 9 ){
                printf(" ");
            }
            x %= mask;
            mask /= 10;
          } while ( mask > 0);
          printf("\n");
}

/* 求最大公约数 */
#include<stdio.h>                                       /* 枚举 */
int main()                                              
{
    int a,b;                                            /* 1.设t为2 */
    int min;                                            /* 如果u和v都被t整除，则记下这个t */
    scanf("%d %d",&a, &b);                              /* t加1后重复第2步，直到t等于u或v */
    if ( a < b ){                                       /* 那么，曾经记下的最大的可以同时整除u和v的t就是gcd */
        min = a;
    }
    else
        {
            min = b;
        }
    int ret = 0;
    int i;
    for ( i = 1; i <= min; i++ ){
        if ( a%i == 0 ){
            if( b%i == 0 ){
                ret = i;
            }
        }
    }
    printf("%d和%d的最大公约数是%d.\n", a , b , ret);
}

