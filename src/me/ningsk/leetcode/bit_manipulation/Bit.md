## & 与运算  
运算规则：
```java
class Bit {
    public static void main(String[] args) {
        int a = 10; // 00001010
        int b = 38; // 00100110
        // & 与  两位数都为1的时候，结果才为1
        // 0 & 0 = 0
        // 0 & 1 = 0
        // 1 & 0 = 0
        // 1 & 1 = 1
        // a & b = 00000010 = 2
         System.out.println(a & b);
    }
}
```
总结：两位同时为1，结果才为1，否则结果都为0 

### 与运算的用途
1. 清零
如果想将一个单元清0，即使其全部二进制位为0， 只要与一个各位都为0的数值相与，结果为0
```java
class Test {
    public static void main(String[] args) {
        System.out.println(784844 & 0);
    }
}
``` 
2. 取一个数的指定位
比如取数x = 1010 1110 的低四位，只需要找一个数y，令y的低四位为1，其余位为0 即 y = 0000 1111，然后
将x与y进行按位与运算（x&y = 0000 1110） 即可得到x的指定位
3. 判断奇数偶数
主要根据最末位是0还是1来决定 为0就是偶数，为1就是奇数，因此可以用if((a & 1) == 0) 代替 if (a % 2 == 0) 来判断a是不是偶数
### | 或运算
运算规则：
```java
class Bit {
    public static void main(String[] args) {
        int a = 10; // 00001010
        int b = 38; // 00100110
        // | 或 两个位都为0的时候，结果才是0
        // 1 |1 = 1
        // 1 | 0 = 0
        // 0 | 1 = 0
        // 0 | 0 = 0
        // a | b = 00101110 = 46
        System.out.println(a | b);
    }
}
```
总结：两个位都为0的时候，结果才是0
#### 或运算的用途
1. 常用来对一个数据的某些位设置为1
比如将数x=1010 1110 的低四位设置为1，只需要另找一个数y，令y的低四位为1，其他位为0，
即y = 0000 1111,x,y执行或运算（x|y = 1010 1111）即可得到   
   
### 异或运算
运算规则：
```
0^0 = 0
0^1 = 1
1^0 = 1
1^1 = 0
```
总结：参与位运算的两个对象，如果相应位相同为0，相异为1  
#### 异或的几条性质：  
- 交换律
- 结合率（a^b）^c = a^(b^c)
- 对于任何数x，都有x^x = 0, x ^ 0 = x
- 自反性: a^b^b = a^0 = a
#### 异或运算的用途

- 翻转指定位 比如将x=1010 1110 的低四位进行翻转，只需要找一个数y 令y的低四位为1，其他位0补足，即Y=0000 1111，然后将X与Y进行异或运算（X^Y=1010 0001）即可得到。
- 与0异或，值不变 例如：1010 1110 ^ 0000 0000 = 1010 1110
- 交换两个数 (自反性 a ^b ^b = a ^ 0 = a)
```java
class Test {
    public static void main(String[] args) {
        int a = 34;
        int b = 66;
        if (a != b) {
            a ^= b;
            b ^= a;
            a ^= b;
        }
    }
}
```
### 取反~
运算规则
```text
~1 = 0
~0 = 1
```
总结：对一个二进制数按位取反，即将0变1，1变0
#### 取反运算的用途
- 使一个数的最低位为0 可以表示为 a & ~ 1。~1的值为1111 1111 1111 1110 再与“与”运算结合，最低位一定是0