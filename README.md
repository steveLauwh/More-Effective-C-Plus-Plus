# More-Effective-C-Plus-Plus

* [01 基础议题(Basics)](https://github.com/steveLauwh/More-Effective-C-Plus-Plus/blob/master/01%20%E5%9F%BA%E7%A1%80%E8%AE%AE%E9%A2%98(Basics).md)

  + 条款 1：仔细区别 pointer 和 reference
  
  + 条款 2：最好使用 C++ 转型操作符
  
  + 条款 3：绝对不要以多态方式处理数组
  
  + 条款 4：非必要不提供 default constructor

* [02 操作符(Operator)](https://github.com/steveLauwh/More-Effective-C-Plus-Plus/blob/master/02%20%E6%93%8D%E4%BD%9C%E7%AC%A6(Operator).md)
  
  + 条款 5：对定制的 “类型转换函数” 保存警觉
  
  + 条款 6：区别 increment/decrement 操作符的前置(prefix)和后置(postfix)形式
  
  + 条款 7：千万不要重载 &&，|| 和 ，操作符
  
  + 条款 8：了解各种不同意义的 new 和 delete

* [03 异常(Exception)](https://github.com/steveLauwh/More-Effective-C-Plus-Plus/blob/master/03%20%E5%BC%82%E5%B8%B8(Exception).md)

  + 条款 9：利用 destructor 避免泄漏资源

  + 条款 10：在 constructor 内阻止资源泄漏 (resource leak)
  
  + 条款 11：禁止异常 (exception) 流出 destructor 之外
  
  + 条款 12：了解 “抛出一个 exception” 与 “传递一个参数” 或 “调用一个虚函数” 之间的差异
  
  + 条款 13：以 by reference 方式捕捉 exception
  
  + 条款 14：明智运用 exception specification
  
  + 条款 15：了解异常处理 (exception handling) 的成本

* [04 效率(Efficiency)](https://github.com/steveLauwh/More-Effective-C-Plus-Plus/blob/master/04%20%E6%95%88%E7%8E%87(Efficiency).md)

  + 条款 16：谨记 80-20 法则
  
  + 条款 17：考虑使用 lazy evaluation (缓式评估)
  
  + 条款 18：分期摊还预期的计算成本
  
  + 条款 19：了解临时对象的来源
  
  + 条款 20：协助完成 “返回值优化 (RVO)”
  
  + 条款 21：利用重载技术 (overload) 避免隐式类型转换
  
  + 条款 22：考虑以操作符复合形式 (op=) 取代其独身形式 (op)
  
  + 条款 23：考虑使用其他程序库
  
  + 条款 24：了解 virtual function、multiple inheritance、virtual base class、runtime type identification 的成本 

* [05 技术(Technique, Idiom, Pattern)](https://github.com/steveLauwh/More-Effective-C-Plus-Plus/blob/master/05%20%E6%8A%80%E6%9C%AF(Technique%2C%20Idiom%2C%20Pattern).md)

  + 条款 25：将 constructor 和 non-member function 虚化
  
  + 条款 26：限制某个 class 所能产生的对象数量
  
  + 条款 27：要求 (或禁止) 对象产生于 heap 之中
  
  + 条款 28：Smart Pointer (智能指针)
  
  + 条款 29：Reference counting (引用计数)
  
  + 条款 30：Proxy class (替身类、代理类)
  
  + 条款 31：让函数根据一个以上的对象类型来决定如何虚化

* [06 杂项讨论(Miscellany)](https://github.com/steveLauwh/More-Effective-C-Plus-Plus/blob/master/06%20%E6%9D%82%E9%A1%B9%E8%AE%A8%E8%AE%BA(Miscellany).md)

  + 条款 32：在未来时态下发展程序
  
  + 条款 33：将非尾端类 (non-leaf classess) 设计为抽象类
  
  + 条款 34：如何在同一程序中结合 C++ 和 C
  
  + 条款 35：让自己习惯于标准 C++ 语言
