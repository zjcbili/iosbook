# NSMutableString练习
##本小节知识点:
1. 【理解】NSMutableString练习

---

##1.NSMutableString练习
- 从要求讲3个520it拼接在一起

- 会生成很多新的字符串

```objc
    NSString *res = @"";
    NSString *subStr = @"520";
    // 1.拼接字符串

//    res = [res stringByAppendingString:subStr];
//    res = [res stringByAppendingString:@" "];
//
//    res = [res stringByAppendingString:subStr];
//    res = [res stringByAppendingString:@" "];
//
//    res = [res stringByAppendingString:subStr];
//    res = [res stringByAppendingString:@" "];

    for (int i = 0; i < 3; ++i) {
        res = [res stringByAppendingString:subStr];
        res = [res stringByAppendingString:@" "];
    }

    // 2.删除末尾的空格
//    res = [res stringByTrimmingCharactersInSet:[NSCharacterSet whitespaceCharacterSet]];
    res = [res substringToIndex:res.length - 1];

    NSLog(@"res = |%@|", res);
```

- 不会生成新的字符串

```objc
    NSString *subStr = @"520it";
    NSMutableString *res = [NSMutableString string];
    // 1.拼接字符串
    for (int i = 0; i < 3; ++i) {
        [res appendString:subStr];
        [res appendString:@" "];
    }
    // 2.删除空格
//    [res replaceCharactersInRange:NSMakeRange(res.length - 1, 1) withString:@""];
    [res deleteCharactersInRange:NSMakeRange(res.length - 1, 1)];
    NSLog(@"res = |%@|", res);
```
---
