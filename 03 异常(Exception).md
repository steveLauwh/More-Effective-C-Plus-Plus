## 条款9：利用 destructor 避免泄漏资源

* C++ 标准程序库提供一个名为 auto_ptr 的 class template，auto_ptr destructor 采用 “单一对象” 形式的 delete，所以不适合取代数组对象的指针。
```cpp
template <class T>
class auto_ptr {
public:
  auto_ptr(T *p = 0) : ptr(p) {}
  ~auto_ptr() { delete ptr; }
private:
  T *ptr;
};
```
```cpp
void processAdoptions(istream& dataSource)
{
  while (dataSource) {
    auto_ptr<ALA> pa(readALA(dataSource));
    pa->processAdoption();
  }
}
```
* 把资源封装在对象内，通常便可以在 exception 出现时避免泄漏资源。

## 条款10：在 constructor 内阻止资源泄漏 (resource leak)

* 由于 C++ 不自动清理那些 “构造期间抛出 exception” 的对象，所以必须自己设计 constructor。
* 用 auto_ptr 对象来取代 pointer class member，便可以对 constructor 做了强化保护，免除 “execption 出现时发生资源泄漏” 的危机，
  不需要在 destructor 内亲自动手释放资源。

## 条款11：禁止异常 (exception) 流出 destructor 之外

* 全力阻止 exception 传出 destructor 之外。

## 条款12：了解 “抛出一个 exception” 与 “传递一个参数” 或 “调用一个虚函数” 之间的差异

* 函数参数和 exception 的传递方式有 3 种：by value，by reference，by pointer。
* throw;  // 重新抛出此 exception
* `catch(const void*)`  // 可以捕捉任何指针类型的 exception

## 条款13：以 by reference 方式捕捉 exception

* throw by pointer 在搬移 “异常相关信息” 时不需要复制对象。
* throw by value   每当 exception object 被抛出，就得复制两次。
* throw by reference 最好选择。

## 条款14：明智运用 exception specification

* throw()。

## 条款15：了解异常处理 (exception handling) 的成本

* 对 try 语句块和 exception specification 的使用限制于非用不可的地点，并且在真正异常的情况下才抛出 exception。
