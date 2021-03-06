# NSFileManager
##本小节知识点:
1. 【理解】NSFileManager介绍
2. 【理解】NSFileManager用法(常见的判断)
3. 【理解】NSFileManager的文件访问
4. 【理解】NSFileManager的文件操作

---

##1.NSFileManager介绍
- 什么是NSFileManager
    + 顾名思义, NSFileManager是用来管理文件系统的
    + 它可以用来进行常见的文件\文件夹操作

- NSFileManager使用了单例模式
    + 使用defaultManager方法可以获得那个单例对象
```objc
[NSFileManager defaultManager]
```

---

##2.NSFileManager用法
- \- (BOOL)fileExistsAtPath:(NSString *)path;
    + path这个文件\文件夹是否存在

```objc
    NSFileManager *manager = [NSFileManager defaultManager];
    // 可以判断文件
    BOOL flag = [manager fileExistsAtPath:@"/Users/LNJ/Desktop/lnj.txt"];
    NSLog(@"flag = %i", flag);
    // 可以判断文件夹
    flag = [manager fileExistsAtPath:@"/Users/LNJ/Desktop/未命名文件夹"];
    NSLog(@"flag = %i", flag);
```
- \- (BOOL)fileExistsAtPath:(NSString *)path isDirectory:(BOOL *)isDirectory;
    + path这个文件\文件夹是否存在, isDirectory代表是否为文件夹

```objc
    NSFileManager *manager = [NSFileManager defaultManager];
    BOOL directory = NO;
    BOOL flag = [manager fileExistsAtPath:@"/Users/LNJ/Desktop/未命名文件夹" isDirectory:&directory];
    NSLog(@"flag = %i, directory = %i", flag, directory);
```
- \- (BOOL)isReadableFileAtPath:(NSString *)path;
    + path这个文件\文件夹是否可读

- \- (BOOL)isWritableFileAtPath:(NSString *)path;
    + path这个文件\文件夹是否可写
    + 系统目录不允许写入

- \- (BOOL)isDeletableFileAtPath:(NSString *)path;
    + path这个文件\文件夹是否可删除
    + 系统目录不允许删除


---

##3.NSFileManager的文件访问
- \- (NSDictionary *)attributesOfItemAtPath:(NSString *)path error:(NSError **)error;
    + 获得path这个文件\文件夹的属性

```objc
    NSFileManager *manager = [NSFileManager defaultManager];
    NSDictionary *dict = [manager attributesOfItemAtPath:@"/Users/LNJ/Desktop/lnj.txt" error:nil];
    NSLog(@"dit = %@", dict);
```

- \- (NSArray *)contentsOfDirectoryAtPath:(NSString *)path error:(NSError **)error;
    + 获得path的当前子路径

- \- (NSData *)contentsAtPath:(NSString *)path;
    + 获得文件内容

```objc
    NSFileManager *manager = [NSFileManager defaultManager];
    NSArray *paths = [manager contentsOfDirectoryAtPath:@"/Users/LNJ/Desktop/" error:nil];
    NSLog(@"paths = %@", paths);
```

- \- (NSArray *)subpathsAtPath:(NSString *)path;
- \- (NSArray *)subpathsOfDirectoryAtPath:(NSString *)path error:(NSError **)error;
    + 获得path的所有子路径

```objc
    NSFileManager *manager = [NSFileManager defaultManager];
    NSArray *paths = [manager subpathsAtPath:@"/Users/LNJ/Desktop/"];
    NSLog(@"paths = %@", paths);
```
---


##4.NSFileManager的文件操作
- \- (BOOL)copyItemAtPath:(NSString *)srcPath toPath:(NSString *)dstPath error:(NSError **)error;
    + 拷贝

- \- (BOOL)moveItemAtPath:(NSString *)srcPath toPath:(NSString *)dstPath error:(NSError **)error;
    + 移动(剪切)

- \- (BOOL)removeItemAtPath:(NSString *)path error:(NSError **)error;
    + 删除

- \- (BOOL)createDirectoryAtPath:(NSString *)path withIntermediateDirectories:(BOOL)createIntermediates attributes:(NSDictionary *)attributes error:(NSError **)error;
    + 创建文件夹(createIntermediates为YES代表自动创建中间的文件夹)

```objc
    NSFileManager *manager = [NSFileManager defaultManager];
    BOOL flag = [manager createDirectoryAtPath:@"/Users/LNJ/Desktop/test" withIntermediateDirectories:YES attributes:nil error:nil];
    NSLog(@"flag = %i", flag);
```
- \- (BOOL)createFileAtPath:(NSString *)path contents:(NSData *)data attributes:(NSDictionary *)attr;
    + 创建文件(NSData是用来存储二进制字节数据的)

```objc
    NSString *str = @"lnj";
    NSData  *data = [str dataUsingEncoding:NSUTF8StringEncoding];
    NSFileManager *manager = [NSFileManager defaultManager];
    BOOL flag = [manager createFileAtPath:@"/Users/LNJ/Desktop/abc.txt" contents:data attributes:nil];
    NSLog(@"flag = %i", flag);
```
