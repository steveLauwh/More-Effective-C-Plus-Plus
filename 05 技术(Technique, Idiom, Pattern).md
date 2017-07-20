## 条款25：将 constructor 和 non-member function 虚化

* technique 技术，idiom 惯用手法，pattern 模式。
* virtual constructor 是某种函数，视其获得的输入，可产生不同类型的对象。
* virtual copy constructor 会返回一个指针，指向其调用者(某对象)的一个新副本。
* non-member functions 的行为虚化：写一个虚函数做实际工作，再写一个什么都不做的非虚函数，只负责调用虚函数。

## 条款26：限制某个 class 所能产生的对象数量

+ 允许零个或一个对象
  - 将 class 的 constructor 声明为 private。
  - 全局函数被声明为此 class 的一个 friend，致使 全局函数 不受 private constructor 的约束。
  - 全局函数内含一个 static 对象，意思是只有一个对象会被产生出来。

```cpp
class PrintJob;
class Printer {
public:
  void submitJob(const PrintJob& job);
  void reset();
  void preformSelfTest();
  ...
  friend Printer& thePrinter();

private:
  Printer();
  Printer(const Printer& rhs);
  ...
};

Printer& thePrinter()
{
  static Printer p;
  return p;
}
```

+ 不同的对象构造状态

+ 允许对象生生灭灭

+ 一个用来计算对象个数的 Base Class

## 条款27：要求 (或禁止) 对象产生于 heap 之中

* 要求对象产生于 heap 之中，让 destructor 成为 private，而 constructor 仍为 public。
* 判断某个对象是否位于 heap 内。
* 栈 stack 高地址往低地址成长，堆 heap 由低地址往高地址成长。
* static 对象在程序执行期间只初始化一次。
* 禁止对象产生于 heap 之中
```cpp
class UPNumber {
private:
  static void *operator new(size_t size);
  static void operator delete(void *ptr);
};
```
## 条款28：Smart Pointer (智能指针) (*)

* smart pointer 取代 C++ 的 dumb pointer(内建指针) ：构造和析构；复制和赋值；解引。
* smart pointer 的构造、赋值、析构。
* 考虑 C++ 标准程序库提供的 auto_ptr template。
* 实现 Dereferencing Operator (解引操作符)：`operator*` 和 `operator->`
* 测试 smart pointer 是否为 null。
  `operator void*()`
* 将 smart pointer 转换为 dumb pointer。
* 不要提供对 dumb pointer 的隐式转换操作符。
* smart pointer 和 “与继承有关的” 类型转换。
* smart pointer 与 const。

## 条款29：Reference counting (引用计数)

* reference counting 允许多个等值对象共享同一实值。
* copy-on-write (写时才复制)。
* 一个 reference counting 基类。
* 自动操作 reference count 引用次数。
* 将 reference counting 加到既有的 class 身上。
* 相对多数的对象共享相对少量的实值。
* 对象实值的产生或销毁成很高，或是它们使用许多内存。

## 条款30：Proxy class (替身类、代理类) (*)

* 区分 operator[] 的读写操作
* proxies 难以完全取代真正对象的最后一个原因在于隐式类型转换。

## 条款31：让函数根据一个以上的对象类型来决定如何虚化 (*)

* 虚函数 + RTTI (运行时期类型辨识)
* 使用 “非成员函数” 的碰撞处理函数
