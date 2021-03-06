# 类初始化

> Swift中类、结构体、枚举都可以定义初始化器,但是由于类存在继承关系，初始化器较为复杂，一般通过初始化器来初始化类

## 类初始化器

> 类有2种初始化器：指定初始化器（designated initializer）、便捷初始化器（convenience initializer）;

- **指定初始化器**：通过init(参数...)初始化，`目的是安全，保证每个值都被初始化`
- **便捷初始化器**：通过`convenience init 初始化`，目的是快捷初始化，在不需要传入那么多参数的情况下可以完成初始化

**结论**：如上所述，一个类`理应只有一个指定初始化器做为主初始化器`,可以有`若干个便捷初始化器，便捷初始化器都要调用自己类的主初始化器完成所有值的初始化`。这样设计，不管走主分支，还是子分支，都可以确保所有值被初始化。

![image-20210124153948587](/Users/shy/Library/Application Support/typora-user-images/image-20210124153948587.png)

## 初始化器的相互调用

![image-20210124154038135](/Users/shy/Library/Application Support/typora-user-images/image-20210124154038135.png)

- `指定初始化器调用是纵向的`,遵循子类调父类，目的是一条线初始化完整一个对象。
- `便捷初始化器调用是横向的`,有且只能调用自己的指定初始化器或便捷初始化器，但不管如何调用，都要走回指定初始化器初始化一切的分支，保证所有属性被初始化。