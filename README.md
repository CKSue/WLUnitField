# WLUnitField

https://github.com/zhwayne/WLUnitField

`WLUnitField`是一个密码/验证码输入框，它提供了一个优雅简洁的输入框🙂，你可以像使用`UITextField`一样去使用`WLUnitField`。

![](./demo.gif)


## 使用

`WLUnitField`的使用非常简单。它继承自`UIControl`，这意味着你可以给它添加各种`UIControlEvent`。然而事实上，WLUnitField 只支持 3 种 event：
* UIControlEventEditingDidBegin
* UIControlEventEditingChanged
* UIControlEventEditingDidEnd

其他一些非必须的 event 已被忽略。

使用示例:

``` Objective-C
- (void)viewDidLoad {
    [super viewDidLoad];
    // Do any additional setup after loading the view, typically from a nib.
    
    WLUnitField *uniField = [[WLUnitField alloc] initWithInputUnitCount:4];
    uniField.frame = CGRectMake(40, 40, 240, 1);
    uniField.delegate = self;
    uniField.unitSpace = 12;
    uniField.borderRadius = 4;
    [uniField sizeToFit];
    [uniField addTarget:self action:@selector(unitFieldEditingChanged:) forControlEvents:UIControlEventEditingChanged];
    
    [self.view addSubview:uniField];
}

- (IBAction)unitFieldEditingChanged:(WLUnitField *)sender {
     NSLog(@"%s, %@", __FUNCTION__, sender.text);
}
```


## 存在的问题
1. 不支持系统输入法**点击选择候选词**功能，不支持系统输入法下**中文输入**。
