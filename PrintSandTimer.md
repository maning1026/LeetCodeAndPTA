# 打印沙漏
## 题目
所谓“沙漏形状”，是指每行输出奇数个符号；各行符号中心对齐；相邻两行符号数差2；符号数先从大到小顺序递减到1，再从小到大顺序递增；首尾符号数相等。

给定任意N个符号，不一定能正好组成一个沙漏。要求打印出的沙漏能用掉尽可能多的符号。 
输入格式:

输入在一行给出1个正整数N（≤\le≤1000）和一个符号，中间以空格分隔。 
输出格式:

首先打印出由给定符号组成的最大的沙漏形状，最后在一行中输出剩下没用掉的符号数。 
输入样例:

19 *

输出样例:
```
*****
 ***
  *
 ***
*****
2
```

## 解答

```
#include<stdio.h>
#include<math.h>
//(N+1)/2=n^2 max=square((N+1)/2)
int main(){
    int N;
    char c;
    scanf("%d %c",&N,&c);
    if(N == 1){
        printf("%c",c);
        printf("\n");
        printf("%d\n",0);
    }
    else{
        int temp = (N+1)/2;
        int n = sqrt(temp);
        int num = 0;
        for(int temp  = n-1; temp >= 0; temp--){
            int blank = n - temp -1;
            for(int i = 0; i<blank;i++){
                printf(" ");
            }
            for( int i = 0; i < 2*temp + 1; i++){
                num++;
                printf("%c",c);
            }
            printf("\n");
        }
        for(int temp = 1; temp < n ;temp++){
            int blank = n - temp -1;
            for(int i = 0; i<blank;i++){
                printf(" ");
            }
            for( int i = 0; i< 2 * temp + 1; i++){
                num++;
                printf("%c",c);
            }
            printf("\n");
        }
        printf("%d\n",(N - num));
    }
    return 0;
}
```