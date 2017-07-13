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

```
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

+ 
  

## 条款27：要求 (或禁止) 对象产生于 heap 之中

## 条款28：Smart Pointer (智能指针)

## 条款29：Reference counting (引用计数)

## 条款30：Proxy class (替身类、代理类)

## 条款31：让函数根据一个以上的对象类型来决定如何虚化
