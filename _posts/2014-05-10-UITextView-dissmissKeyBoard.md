---
layout: post
title: UITextView 隐藏键盘
---

在 `viewDidLoad` 方法中：

```Objective-C
    // 在输入框加一个 Done 按钮退出键盘
    UIToolbar *topView = [[UIToolbar alloc] initWithFrame:CGRectMake(0, 0, 320, 30)];

    
    // 这里缺少 Button1，Button2 的话，doneButton 按钮会被放到 toolbar 的左边
    UIBarButtonItem *Button1 = [[UIBarButtonItem alloc]initWithTitle:@"" style:UIBarButtonItemStyleBordered target:self action:nil];

    UIBarButtonItem *Button2 = [[UIBarButtonItem alloc]initWithBarButtonSystemItem:UIBarButtonSystemItemFlexibleSpace target:self action:nil];

    UIBarButtonItem *doneButton = [[UIBarButtonItem alloc] initWithTitle:@"Done" style:UIBarButtonItemStyleDone target:self action:@selector(dismissKeyBoard)];

    [topView setItems:@[Button1,Button2,doneButton]];

    [self.textView setInputAccessoryView:topView];
```

`dismissKeyBoard` 方法：

```Objective-C
-(void)dismissKeyBoard{
    [self.textView resignFirstResponder];
}
```

效果图：
![](https://github.com/JeOam/jeoam.github.io/blob/9483f32c6b660e86028da07b0dc06cc10efda52b/images/2014-05-10.png)