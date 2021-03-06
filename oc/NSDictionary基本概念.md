# NSDictionary基本概念
##本小节知识点:
1. 【理解】NSDictionar基本概念
2. 【理解】NSDictionary的创建
3. 【理解】NSDictionary的遍历
4. 【理解】NSDictionary文件操作

---

##1.NSDictionar基本概念
- 什么是NSDictionary
    + NSDictionary翻译过来叫做”字典”
    + 日常生活中,“字典”的作用:通过一个拼音或者汉字,就能找到对应的详细解释
    + NSDictionary的作用类似:通过一个key,就能找到对应的value
    + NSDictionary是不可变的, 一旦初始化完毕, 里面的内容就无法修改

---
##2.NSDictionary的创建
```
+ (instancetype)dictionary;
+ (instancetype)dictionaryWithObject:(id)object forKey:(id <NSCopying>)key;
+ (instancetype)dictionaryWithObjectsAndKeys:(id)firstObject, ...;
+ (id)dictionaryWithContentsOfFile:(NSString *)path;
+ (id)dictionaryWithContentsOfURL:(NSURL *)url;
```

- NSDictionary创建简写
    + 以前
```objc
NSDictionary *dict = [NSDictionary dictionaryWithObjectsAndKeys:@"lnj", @"name", @"12345678", @"phone", @"天朝", @"address", nil];
```
    + 现在
```objc
NSDictionary *dict = @{@"name":@"lnj", @"phone":@"12345678", @"address":@"天朝"};
```

- NSDictionary获取元素简写
    + 以前
```objc
[dict objectForKey:@"name”];
```
    + 现在
```objc
dict[@"name”];
```


- 键值对集合的特点
    + 字典存储的时候,必须是"键值对"的方式来存储(同时键不要重复)
    + 键值对中存储的数据是"无序的".
    + 键值对集合可以根据键, 快速获取数据.

##3.NSDictionary的遍历
- \- (NSUInteger)count;
    + 返回字典的键值对数目

- \- (id)objectForKey:(id)aKey;
    + 根据key取出value


- 快速遍历

```objc
    NSDictionary *dict = @{@"name":@"lnj", @"phone":@"12345678", @"address":@"天朝"};
    for (NSString *key in dict) {
        NSLog(@"key = %@, value = %@", key, dict[key]);
    }
```
- Block遍历

```objc
    [dict enumerateKeysAndObjectsUsingBlock:^(NSString *key, NSString *obj, BOOL *stop) {
        NSLog(@"key = %@, value = %@", key, obj);
    }];

```
---
##4.NSDictionary文件操作
- 将字典写入文件中
    + \- (BOOL)writeToFile:(NSString *)path atomically:(BOOL)useAuxiliaryFile;
    + \- (BOOL)writeToURL:(NSURL *)url atomically:(BOOL)atomically;
    + 存结果是xml文件格式,但苹果官方推荐为plist后缀。

- 示例

```objc
    NSDictionary *dict = @{@"name":@"lnj", @"phone":@"12345678", @"address":@"天朝"};
    BOOL flag = [dict writeToFile:@"/Users/LNJ/Desktop/dict.plist" atomically:YES];
    NSLog(@"flag = %i", flag);
```

- 从文件中读取字典

```objc
NSDictionary *newDict = [NSDictionary dictionaryWithContentsOfFile:@"/Users/LNJ/Desktop/dict.plist"];
    NSLog(@"newDict = %@", newDict);
```
