---
layout: post
title: Constructing Block Objects
---

a. Example block object defined as function：

```Objective-C
NSString* (^intToString)(NSUInteger) = ^(NSUInteger paramInteger){
    NSString *result = [NSString stringWithFormat:@"%lu",
                        (unsigned long)paramInteger];
    return result; 
};
```

b. `typedef` the signature of block object:

```Objective-C
typedef NSString* (^IntToStringConverter)(NSUInteger paramInteger);
```

c. define a Objective-C method that accepts both an integer and a block object of type:

```Objective-C
- (NSString *) convertIntToString:(NSUInteger)paramInteger usingBlockObject:(IntToStringConverter)paramBlockObject{

    return paramBlockObject(paramInteger); }
```

d. Calling the block object in another method:

```Objective-C
- (void) doTheConversion{
    NSString *result = [self convertIntToString:123
                               usingBlockObject:intToString];
    NSLog(@"result = %@", result);
}
```

e. Example block object defined as a function:

```Objective-C
- (void) doTheConversion{
    IntToStringConverter inlineConverter = ^(NSUInteger paramInteger){
        NSString *result = [NSString stringWithFormat:@"%lu",
                            (unsigned long)paramInteger];
    return result; };
    NSString *result = [self convertIntToString:123
                               usingBlockObject:inlineConverter];
    NSLog(@"result = %@", result);
}
```

f. construct a block object while passing it as a parameter:

```Objective-C
- (void) doTheConversion{
        NSString *result =
        [self convertIntToString:123
                usingBlockObject:^NSString *(NSUInteger paramInteger) {
                    NSString *result = [NSString stringWithFormat:@"%lu",
                                        (unsigned long)paramInteger];
                    return result; 
                }];

    NSLog(@"result = %@", result);
}
```