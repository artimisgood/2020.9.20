# 2020.9.20———整数反转
## 题目
给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。
```
示例 1:
输入: 123
输出: 321

 示例 2:
输入: -123
输出: -321

示例 3:
输入: 120
输出: 21
```
## 解题
### 语言
c++
### 思路
用数学方法弹出或者推入数字：
```
//pop operation://弹出数字
pop = x % 10;
x /= 10;

//push operation://推入数字
temp = rev * 10 + pop;
rev = temp;
```

这种方法很危险，因为当 temp= rev⋅10+pop 时会导致溢出。

幸运的是，事先检查这个语句是否会导致溢出很容易。

为了便于解释，我们假设rev是正数。

当 rev负时可以应用类似的逻辑。
```
### 代码
```c++
class Solution {
public:
    int reverse(int x) {
        int rev = 0;
        while(x!=0){
            int pop=x%10;
            x/=10;//取x的最末位
            if(rev>INT_MAX/10||(rev==INT_MAX/10 && pop>7)) return 0;
            if(rev<INT_MIN/10||(rev==INT_MIN/10&& pop<-8)) return 0;//排除溢出的情况
            rev = rev*10+pop;
        }
        return rev;
    }
};
```
