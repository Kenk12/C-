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


