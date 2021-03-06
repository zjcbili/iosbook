# typedef和Block
##本小节知识点:
1. 【了解】函数指针回顾
2. 【掌握】block和typedef

---

##1.函数指针回顾
- 函数指针使用

```objc
int sum(int value1, int value2)
{
    return value1 + value2;
}

int minus(int value1, int value2)
{
    return value1 - value2;
}

int main(int argc, const char * argv[]) {
    int (*sumP) (int, int) = sum;
    int res = sumP(10, 20);
    NSLog(@"res = %i", res);

    int (*minusP) (int , int) = minus;
    res = minusP(10, 20);
    NSLog(@"res = %i", res);
    return 0;
}
```
- 函数指针别名

```objc
typedef int (*calculate) (int, int);
int main(int argc, const char * argv[]) {
    calculate sumP = sum;
    int res = sumP(10, 20);
    NSLog(@"res = %i", res);
    calculate minusP = minus;
    res = minusP(10, 20);
    NSLog(@"res = %i", res);
    return 0;
}
```
---

##2.block和typedef

- block使用
```objc
int main(int argc, const char * argv[]) {
    int (^sumBlock) (int, int) = ^(int value1, int value2){
        return value1 + value2;
    };
    int res = sumBlock(10 , 20);
    NSLog(@"res = %i", res);

    int (^minusBlock) (int, int) = ^(int value1, int value2){
        return value1 - value2;
    };
    res = minusBlock(10 , 20);
    NSLog(@"res = %i", res);
    return 0;
}
```

- block别名

```objc
int main(int argc, const char * argv[]) {
    calculateBlock sumBlock = ^(int value1, int value2){
        return value1 + value2;
    };
    int res = sumBlock(10, 20);
    NSLog(@"res = %i", res);
    calculateBlock minusBlock = ^(int value1, int value2){
        return value1 - value2;
    };
    res = minusBlock(10, 20);
    NSLog(@"res = %i", res);

    return 0;
}
```
---

