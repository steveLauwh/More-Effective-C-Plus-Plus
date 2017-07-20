## 条款5：对定制的 “类型转换函数” 保存警觉

* 隐式类型转换操作符，关键词 operator 之后加上一个类型名称。
```cpp
class Rational {
public:
  operator double() const;
  ...
};
```
* 只要将 constructor 声明为 explicit，编译器便不能因隐式类型转换的需要而调用它们。

## 条款6：区别 increment/decrement 操作符的前置(prefix)和后置(postfix)形式

* 后置式有一个 int 自变量，并且在它被调用时，编译器默默地为该 int 指定一个 0 值。
* 前置式返回一个 reference，后置式返回一个 const 对象。
```cpp
class UPInt {
public:
  UPInt& operator++();          // 前置式++
  const UPInt operator++(int);  // 后置式++
  
  UPInt& operator--();           // 前置式--
  const UPInt operator--(int);  // 后置式--
};
```

## 条款7：千万不要重载 &&，|| 和 ，操作符

* 重载 && 和 ||，没办法提供程序员预期的某种行为模式。
* C++ 语言规范并未明确定义函数调用动作中各参数的评估顺序。
* 重载 && ，|| 和 ，无法令其行为像它们应有的行为一样。

## 条款8：了解各种不同意义的 new 和 delete

* new 是所谓的 new operator。这个操作符是语言内建的，就像 sizeof 那样，不能被改变意义，总是做相同的事情。
* operator new 只负责分配内存。
* placement new 一个特殊版本的 operator new，在已分配(并拥有指针)的内存中构造对象。
* delete 是内建的 delete operator，如 delete ps；先析构 ps 所指对象，又能够释放被该对象占用的内存。
* 内存释放动作是函数 operator delete 执行。
* 分配对象数组，`string *ps = new string[10];`。
