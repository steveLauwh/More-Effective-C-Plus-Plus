## 条款1：仔细区别 pointer 和 reference 

* 没有所谓的 null reference，一个 reference 必须总代表某个对象。
* 如果你有一个变量，其目的是用来指向另一个对象，但是也有可能它不指向任何对象，那么使用 pointer。
* 如果这个变量总是必须代表一个对象，不允许这个变量为 null，那么使用 reference。
* pointer 可以被重新赋值，指向另一个对象；reference 却总是指向它最初获得的那个对象。
* 当实现一个操作符而其语法需求无法由 pointer 达成，就选择 reference。 例如 operator[]

## 条款2：最好使用 C++ 转型操作符

* static_cast<type>(expression)         基本转型
* const_cast<type>(expression)          将某个对象的常量性去除掉
* dynamic_cast<type>(expression)        用来执行继承体系中“安全的向下转型或跨系转型动作”
* reinterpret_cast<type>(expression)    与编译平台息息相关，不具移植性，最常用用途是转换“函数指针”类型

```cpp
typedef void (*FuncPtr)();
FuncPtr funcPtrArray[10];

int doSomething();
funcPtrArray[0] = reinterpret_cast<FuncPtr>(&doSomething);
```

## 条款3：绝对不要以多态方式处理数组

* 多态和指针算术不能混用。
* 数组对象几乎总是会涉及指针的算术运算，所以数组和多态不要混用。

## 条款4：非必要不提供 default constructor

* 添加无意义的 default constructor，会影响 class 的效率。
* 如果 class constructor 可以确保对象的所有字段都会被正确地初始化，付出时间代价和空间代价成本便可以免除。
