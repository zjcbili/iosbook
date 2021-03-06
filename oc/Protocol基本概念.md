# Protocol基本概念
##本小节知识点:
1. 【理解】protocol 基本概念
2. 【掌握】protocol 语法格式
3. 【理解】protocol和继承区别

---

##1.protocol 基本概念
- Protocol翻译过来, 叫做”协议”
    + 在写java的时候都会有接口interface这个概念,接口就是一堆方法的声明没有实现,而在OC里面Interface是一个类的头文件的声明,并不是真正意义上的接口的意思,在OC中接口是由一个叫做协议的protocol来实现的
    + protocol它可以声明一些必须实现的方法和选择实现 的方法。这个和java是完全不同的

- Protocol的作用
    + 用来声明一些方法
    + 也就说, 一个Protocol是由一系列的方法声明组成的

---

##2.protocol 语法格式
- Protocol的定义

```objc
@protocol 协议名称
// 方法声明列表
@end
```

- 类遵守协议
    + 一个类可以遵守1个或多个协议
    + 任何类只要遵守了Protocol,就相当于拥有了Protocol的所有方法声明


```objc
@interface 类名 : 父类 <协议名称1, 协议名称2,…>
@end
```

- 示例

```objc
@protocol SportProtocol <NSObject>
- (void)playFootball;
- (void)playBasketball;
@end

#import "SportProtocol.h" // 导入协议
@interface Studnet : NSObject<SportProtocol> // 遵守协议
@end

@implementation Student
// 实现协议方法
- (void)playBasketball
{
    NSLog(@"%s", __func__);
}
// 实现协议方法
- (void)playFootball
{
    NSLog(@"%s", __func__);
}
@end
```
---

##3.protocol和继承区别
- 继承之后默认就有实现, 而protocol只有声明没有实现
- 相同类型的类可以使用继承, 但是不同类型的类只能使用protocol
- protocol可以用于存储方法的声明, 可以将多个类中共同的方法抽取出来, 以后让这些类遵守协议即可

---
