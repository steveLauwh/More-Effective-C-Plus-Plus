## 条款16：谨记 80-20 法则

* 软件的整体性能几乎总是其构成要素(代码)的一小部分决定。

## 条款17：考虑使用 lazy evaluation (缓式评估)

* Reference Counting (引用计数)：在真正需要之前，不必着急为某物做一个副本。
* 区分读和写
* Lazy Fetching (缓式取出)
* Lazy Expression Evaluation (表达式缓评估)
* 节省空间方式

## 条款18：分期摊还预期的计算成本

* over-eager evaluation 超急评估：在被要求之前就先把事情做下去。
* 将 “已经计算好而有可能再被需要” 的数值保留下来，所谓的 caching。
* Prefetching 预先取出，需要一些空间来放置被预先取出的东西。
* 节省时间方式

## 条款19：了解临时对象的来源

* C++ 真正的临时对象是不可见的，不会在源代码中出现。
* 任何时候只要看到一个 reference-to-const 参数，就极可能会有一个临时对象被产生出来绑定至该参数上。
* 任何时候只要看到函数返回一个对象，就会产生临时对象。

## 条款20：协助完成 “返回值优化 (RVO)”

* 返回所谓的 “constructor argument” 以取代对象；
```cpp
inline const Rational operator*(const Rational& lhs, const Rational& rhs)
{
  return Rational(lhs.numerator() * rhs.numerator(), lhs.denominator() * rhs.denominator());
}
```

## 条款21：利用重载技术 (overload) 避免隐式类型转换

* 希望获得隐式类型转换，却不希望承受临时对象所带来的任何成本。
* 任何函数如果接受类型为 string，`char*`，complex 等自变量，都可以借由重载技术，合理消除类型转换。

## 条款22：考虑以操作符复合形式 (op=) 取代其独身形式 (op)

* 操作符的 “复合版本”(例如：operator+=) 比其对应的 “独身版本(例如：operator+)” 有更高效率的倾向。

## 条款23：考虑使用其他程序库

* 不同的程序库即使提供相似的机能，也往往表现出不同的性能取舍策略。

## 条款24：了解 virtual function、multiple inheritance、virtual base class、runtime type identification 的成本 (*)

* virtual table (vtbl) 和 virtual table pointer (vptr)
* vtbl 通常是一个由 “函数指针” 架构而成的数组。某些编译器会以链表取代数组，但其基本策略相同。
* 避免将虚函数声明为 inline。
* class vbtl 被产生于 “内含其第一个 non-line，non-pure 虚函数定义式” 的目标文件中。
* RTTI 让我们得以在运行时期获得 object 和 class 的相关信息。
