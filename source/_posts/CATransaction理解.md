---
title:  CATransaction理解
tags: IOS
date: 2019-05-21 17:31:29
---

> 官方文档:
> CATransaction is the Core Animation mechanism for batching multiple layer-tree operations into atomic updates to the render tree. Every modification to a layer tree must be part of a transaction. Nested transactions are supported.
> CATransaction是事务，用于批量提交多个对layer-tree的操作，并且是原子性的。所有对layer-tree的修改都必须包含在事务内。事务是可以嵌套的。

1. ##### 嵌套事务
- 事务允许嵌套， 但是嵌套在内层的事务不能被立即commit，会在最外层的事务结束后统一commit。
```Objective-C
    [CATransaction beigin];
    // 设置变化动画过程是否显示，默认为YES不显示
    [CATransaction setDisableActions:YES];

    layer.cornerRadius = (layer.cornerRadius == 0.0f) ? 30.0f : 0.0f;

    [CATransaction commit];

    //上面的动画并不会立即执行，需要等最外层的commit

    [NSThread sleepForTimeInterval:10];

    //显式事务默认开启动画效果,kCFBooleanTrue关闭

    [CATransaction setValue:(id)kCFBooleanFalse

                     forKey:kCATransactionDisableActions];

    //动画执行时间

    [CATransaction setValue:[NSNumber numberWithFloat:10.0f] forKey:kCATransactionAnimationDuration];

    //[CATransaction setAnimationDuration:[NSNumber numberWithFloat:5.0f]];

    anotherLayer.cornerRadius = (anotherLayer.cornerRadius == 0.0f) ? 30.0f : 0.0f;

    [CATransaction commit];
```

2. ##### 隐私CATransaction
 - 所有对layer-tree的操作都必须处于事务。修改UIView的属性最终也是修改到了layer-tree。当我们改动layer-tree时，如果当前没有显示创建CATransaction，系统会创建一个隐式的CATransaction，这个隐式CATransaction会在RunLoop结束时commit。
 
3. ##### 显示CATransaction
- 手动创建CATransaction, 设置一些列参数

#### 引用
- [理解CATransaction](http://jefferyfan.github.io/2016/06/27/programing/iOS/CATransaction/)
- [iOS-CATransaction](https://www.jianshu.com/p/a04abd33c28f)

