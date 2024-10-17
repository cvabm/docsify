# 关键字

- `gcc` linux 生成.out windows 为.exe
- `auto` 自动推导变量的类型，特别是在处理复杂类型和 STL 容器时更简洁
- `puts "hello"` 不带格式打印
- `printf("Name: %s\n", name);` %s 输入字符串、%d 整数、%f 浮点数、%c 字符
    - 返回值为字符数量
- `scanf("%d", &num);` 从标准输入读取
- `sscanf(input, "%da%d", &a, &b);` 获取从字符串中读取格式化数据
- `std::cout << "hello" <<std::endl;`
- `cout vs cerr `
    - ` cout` 默认缓冲，\n或`std::flush`才会输出
    - `cerr` 直接输出
- `&str`str 内存地址
- `abort();` // 调用 abort()函数，人为引发 SIGABRT 信号
- `~ResourceHolder(){ 释放资源 }` 析构函数，只能有一个，释放资源的作用
- `__LINE__`
    - 当前行号,预定义宏，不用导入直接用
    - `__FILE__`文件名
    - `__DATE__`编译日期
    - `_WIN64` 表示当前为 64 位系统
- `virtual 返回类型 函数名(参数列表) = 0;` 纯虚函数,无实现，派生类必须实现该函数
- `volatile` 当一个变量被多个线程同时访问时，使用 volatile 可以确保对该变量的修改对其他线程是可见的
- 操作符
    - `&x`表示取变量 x 的地址
    - ``解引用操作符，获取指针指向的对象的值
    - `>`用于访问指针指向的对象的成员
    - `sizeof()` 获取对变量或类型的占字节数
    - `typedef int Age` 将 int 类型取个别名为 Age
- 指针
    - `int * p = &num` 指针 p 记录 num 的地址
    - `sizeof(int*)` 获取指针占位，32 位 4 字节，64 位 8 字节
    - `int * a`空指针指向编号为 0 的地址，不能操作
    - `int *pointer; *pointer = 42;`// 野指针：未初始化的指针，试图给未初始化的指针赋值
    - `int& r = i` 引用变量，r 和 i 引用同一块内存空间，相当于同一个变量不同名称
- 其他
    - `a << 2` 左移，相当于`a * 2`
    - `a >> 2` 右移，相当于 `a / 2`
    - `0b1011` 0b 开头的表示为二进制数
    - `0x` 0x 开头为十六进制
- ip 地址和网络地址 IP 地址用于标识和寻址网络中的具体设备，而网络地址则表示划分网络的标识符。IP 地址是设备的独特标识，而网络地址是为了确定特定网络而划分的标识。
- 掩码
- `unsigned` 无符号整数，即满足>=0
- `extern` 它告诉编译器该变量或函数的定义在其他地方，允许在多个源文件之间共享变量或函数
- `strcasestr` 在一个字符串中查找另一个字符串的首次出现
- `getline` 从输入流中读取一行文本

## `algorithm`
C++ 标准库中的 `<algorithm>` 头文件提供了许多常用的算法，这些算法可以用于处理容器中的数据。以下是一些常用的算法：

1. **排序算法**：

   * `std::sort`: 对容器中的元素进行排序。
   * `std::stable_sort`: 稳定排序，保持相等元素的相对顺序。
   * `std::partial_sort`: 对部分元素进行排序。
   * `std::nth_element`: 找到第 n 个元素，并将其放到正确的位置。

2. **查找算法**：

   * `std::find`: 查找容器中第一个匹配的元素。
   * `std::find_if`: 根据给定条件查找元素。
   * `std::binary_search`: 在已排序的范围内查找元素。
   * `std::lower_bound`: 查找第一个不小于给定值的元素。
   * `std::upper_bound`: 查找第一个大于给定值的元素。

3. **操作算法**：

   * `std::copy`: 复制元素。
   * `std::move`: 移动元素。
   * `std::fill`: 用指定值填充范围。
   * `std::transform`: 对范围内的每个元素应用给定的操作。

4. **集合算法**：

   * `std::set_union`: 计算两个集合的并集。
   * `std::set_intersection`: 计算两个集合的交集。
   * `std::set_difference`: 计算两个集合的差集。
   * `std::set_symmetric_difference`: 计算两个集合的对称差集。

5. **其他算法**：

   * `std::accumulate`: 计算范围内元素的总和（需要包含 `<numeric>`）。
   * `std::for_each`: 对范围内的每个元素执行给定操作。
   * `std::count`: 计算范围内特定值的出现次数。
   * `std::unique`: 移除相邻重复的元素。

这些算法可以与标准库中的容器（如 `std::vector`, `std::list`, `std::deque` 等）一起使用，提供了强大的数据处理能力。使用这些算法时，通常需要包含 `<algorithm>` 头文件。
