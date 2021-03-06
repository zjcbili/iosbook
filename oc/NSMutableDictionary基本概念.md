# NSMutableDictionary基本概念
##本小节知识点:
1. 【理解】NSMutableDictionary 基本概念
2. 【理解】NSMutableDictionary 常用方法
3. 【理解】NSMutableDictionary 简写
4. 【理解】NSDictionary和NSArray对比

---

##1.NSMutableDictionary 基本概念
- 什么是NSMutableDictionary
    + NSMutableDictionary是NSDictionary的子类
    + NSDictionary是不可变的,一旦初始化完毕后,它里面的内容就永远是固定的,不能删除里面的元素, 也不能再往里面添加元素
    + NSMutableDictionary是可变的,随时可以往里面添加\更改\删除元素

---


##2.NSMutableDictionary的常见操作
- \- (void)setObject:(id)anObject forKey:(id <NSCopying>)aKey;
    + 添加一个键值对(会把aKey之前对应的值给替换掉)

- \- (void)removeObjectForKey:(id)aKey;
    + 通过aKey删除对应的value

- \- (void)removeAllObjects;
    + 删除所有的键值对

##3.NSMutableDictionary的简写
- 设置键值对
    + 以前
```objc
[dict setObject:@"Jack" forKey:@"name”];
```
    + 现在
```objc
dict[@"name"] = @"Jack";
```

---
##4.NSDictionary和NSArray对比
- NSArray和NSDictionary的区别
    + NSArray是有序的,NSDictionary是无序的
    + NSArray是通过下标访问元素,NSDictionary是通过key访问元素

- NSArray的用法
    + 创建
```objc
@[@"Jack", @"Rose"] (返回是不可变数组)
```
    + 访问
```objc
id d = array[1];
```
    + 赋值
```objc
array[1] = @"jack";
```

- NSDictionary的用法
    +创建
```objc
@{ @"name" : @"Jack", @"phone" : @"10086" } (返回是不可变字典)
```
    + 访问
```objc
id d = dict[@"name"];
```
    + 赋值
```objc
dict[@"name"] = @"jack";
```
