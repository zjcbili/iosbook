# @class
##本小节知识点:
1. 【掌握】@class基本概念
2. 【掌握】@class其它应用场景
3. 【掌握】@class和#import

---

##1.@class基本概念
- 作用
    + 可以简单地引用一个类

- 简单使用
    + @class Dog;
    + 仅仅是告诉编译器:Dog是一个类;并不会包含Dog这个类的所有内容

- 具体使用
    + 在.h文件中使用@class引用一个类
    + 在.m文件中使用#import包含这个类的.h文件

---

##2.@class其它应用场景
- 对于循环依赖关系来说，比方A类引用B类，同时B类也引用A类
- 这种嵌套包含的代码编译会报错

```objc
#import "B.h"
@interface A : NSObject
{
    B *_b;
}
@end

#import “A.h"
@interface B : NSObject
{
    A *_a;
}
@end

```

- 当使用@class在两个类相互声明，就不会出现编译报错

```objc
@class B;
@interface A : NSObject
{
    B *_b;
}
@end

@class A;
@interface B : NSObject
{
    A *_a;
}
@end
```
---


##3.@class和#import
- 作用上的区别
    + \#import会包含引用类的所有信息(内容),包括引用类的变量和方法
    + @class仅仅是告诉编译器有这么一个类, 具体这个类里有什么信息, 完全不知

- 效率上的区别
    + 如果有上百个头文件都#import了同一个文件，或者这些文件依次被#import,那么一旦最开始的头文件稍有改动，后面引用到这个文件的所有类都需要重新编译一遍 , 编译效率非常低
    + 相对来讲，使用@class方式就不会出现这种问题了

---


