#include <cstdio>
#include <string.h>
#define M 100
int fi[M];
int Fabonacci(int n){            //递归实现
    if(n==1 || n==2) return 1;
    else{
        return Fabonacci(n-1)+Fabonacci(n-2);
    }
}
int _Fabonacci(int n){         //非递归
    if(n==1 || n==2) return 1;
    else{
        int temp=1,temp1=1;
        int result=0;
        for(int i=3;i<=n;i++){
            result=temp+temp1;
            temp=temp1;
            temp1=result;
        }
        return result;
    }
}
int __Fabonacci(int n){         //记忆化搜索优化
    if(n==1||n==2)
        return 1;
    if(fi[n]!=-1)
        return fi[n];
    return fi[n]=__Fabonacci(n-1)+__Fabonacci(n-2);
    /**************************************************/
    /*
       if(n > 2) return fi[n] == -1 ? fi[n]=__Fabonacci(n-1)+__Fabonacci(n-2):fi[n];
12     else return 1;
     */
}
int main(){
    memset(fi, -1, sizeof(fi));
    fi[0]=0,fi[1],fi[2]=1;
    //                       递归        非递归        记忆化搜索
    printf("%d %d %d",Fabonacci(20),_Fabonacci(20),__Fabonacci(20));
    return 0;
}
