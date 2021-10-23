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
