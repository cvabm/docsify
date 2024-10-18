# c++标准库
C++ 标准库是 C++ 语言的一部分，提供了一系列的类、函数和模板，用于执行常见的编程任务。C++ 标准库非常庞大，包括了以下主要部分：

```
iostream.h
fstream.h
string.h 对 C 风格字符串的封装，更安全易用
容器（vector、list、map、set 等）

```
## sstream
- `istringstream` 字符串中读取数据
    ```cpp
    int main() {
    std::string input = "42 3.14 Hello";
    std::istringstream iss(input);

    int intValue;
    double doubleValue;
    std::string stringValue;

    // 从字符串流中提取数据
    iss >> intValue >> doubleValue >> stringValue;

    // 输出提取的数据
    std::cout << "Integer: " << intValue << std::endl;
    std::cout << "Double: " << doubleValue << std::endl;
    std::cout << "String: " << stringValue << std::endl;

    return 0;
}

- `ostringstream ` 写入数据
    ```cpp
    int main() {
    std::ostringstream name;
    std::string str("操的");
    name << str;
    std::cout<<name.str();
    return 0;
}
- `chrono`
    - 于处理时间和日期的库
    - 测试本机性能
```cpp
#include <iostream>
#include <chrono>

unsigned long long fibonacci(int n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    int N = 40; // 可以根据需要调整 N 的值
    std::cout << "Calculating Fibonacci(" << N << ")..." << std::endl;

    auto start = std::chrono::high_resolution_clock::now();

    // 进行多次计算以增加计算量
    unsigned long long result = 0;
    for (int i = 0; i < 30; ++i) { // 调整循环次数以增加计算量
        result += fibonacci(N);
    }

    auto end = std::chrono::high_resolution_clock::now();
    std::chrono::duration<double> duration = end - start;

    std::cout << "Fibonacci(" << N << ") = " << result << std::endl;
    std::cout << "Time taken: " << duration.count() << " seconds" << std::endl;

    return 0;
}


```

    

### 容器
- `array` 固定数组
- `vector` 动态数组，自动管理内存
- `queue`
    ```cpp
    std::queue<int> vec;
    vec.push(2);
    vec.push(3);
    vec.push(5);
   while(!vec.empty()){
    std::cout << vec.front() << std::endl;
    vec.pop();
   } 
- `deque` 双端队列
    ```c
    myDeque.push_back(20);
    myDeque.push_front(5);

    支持for循环遍历
- `stack` 
- 
1. **基础输入输出流（iostream）**：

   * 提供了 `cin`、`cout`、`cerr` 和 `clog` 等流对象，用于标准输入输出。

2. **字符串处理（string）**：

   * 提供了 `std::string` 类，用于处理字符串。

3. **容器（vector、list、map、set 等）**：

   * 提供了多种类型的容器，如动态数组、链表、哈希表、平衡树等。

4. **算法（algorithm）**：

   * 提供了一组算法，如排序、搜索、复制、替换、删除等。

5. **函数对象和绑定（functional）**：

   * 提供了函数适配器和绑定机制，用于创建自定义函数对象。

6. **智能指针（memory）**：

   * 提供了 `std::unique_ptr`、`std::shared_ptr` 和 `std::weak_ptr` 等智能指针，用于自动管理内存。

7. **线程（thread）**：

   * 提供了线程相关的支持，允许并发执行。

8. **随机数生成（random）**：

   * 提供了生成随机数的设施。

9. **时间日期（chrono）**：

   * 提供了时间日期处理的能力。

10. **正则表达式（regex）**：

    * 提供了正则表达式的支持。

11. **文件系统（filesystem）**：

    * 提供了文件系统操作的类和函数。

12. **原子操作（atomic）**：

    * 提供了原子类型和原子操作，用于无锁编程。

13. **动态内存管理（memory）**：

    * 提供了 `std::allocator` 和其他内存分配相关的工具。

14. **异常处理（exception）**：

    * 提供了异常处理的类和函数。

15. **类型特性（type\_traits）**：

    * 提供了编译时类型检查和特性测试。

16. **元组（tuple）**：

    * 提供了 `std::tuple` 类，用于存储不同类型的值。

17. **位操作（bitset）**：

    * 提供了 `std::bitset` 类，用于处理二进制数据。

18. **数学库（cmath）**：

    * 提供了数学函数，如三角函数、指数、对数等。

19. **复杂数学库（complex）**：

    * 提供了复数的支持。

20. **I/O 流操作（fstream、sstream、iostream）**：

    * 提供了文件流、字符串流等高级流操作。

21. **容器适配器（stack、queue、priority\_queue）**：

    * 提供了容器的适配器，如栈、队列、优先队列。

22. **迭代器（iterator）**：

    * 提供了迭代器的概念和实现，用于遍历容器。

23. **多态和动态类型识别（typeinfo）**：

    * 提供了 `typeid` 操作符和 `std::type_info` 类，用于运行时类型识别。

24. **C 库函数的 C++ 封装（cstddef、cstdlib、cstring、ctime 等）**：

    * 提供了 C 语言库函数的 C++ 风格封装。

C++ 标准库的设计目标是提供一组通用的、可重用的组件，以支持高效的软件开发。标准库的组件都经过了精心设计，以确保高效性、可移植性和一致性。