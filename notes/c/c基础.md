# c基础

## 命令行
- `./main &` 当前目录运行main，&表示后台运行，不阻塞命令行
- `#pragma once` 预防头文件被多次包含
- 

### 引用参数传递 vs 指针参数传递
#### 使用引用的示例

```cpp

复制代码已复制
bool GetLocalIp(std::string &result) {
    // 假设获取到的 IP 地址是 "192.168.1.1"
    result = "192.168.1.1";
    return true; // 返回成功
}

// 调用示例
std::string ip;
if (GetLocalIp(ip)) {
    std::cout << "Local IP: " << ip << std::endl;
}
```

#### 使用指针的示例

```cpp

复制代码已复制
bool GetLocalIp(std::string *result) {
    if (result == nullptr) {
        return false; // 检查指针是否为 nullptr
    }
    // 假设获取到的 IP 地址是 "192.168.1.1"
    *result = "192.168.1.1";
    return true; // 返回成功
}

// 调用示例
std::string ip;
if (GetLocalIp(&ip)) {
    std::cout << "Local IP: " << ip << std::endl;
}
```

#### 总结

* **引用**：更简洁和安全，适合大多数情况，尤其是当你不需要处理空值时。
* **指针**：提供了更大的灵活性，但需要额外的空指针检查，适合需要动态内存管理的场景。

在选择使用哪种方式时，可以根据具体的需求和代码风格来决定。一般来说，引用更常用，因为它更简洁且易于理解。


### string vs string.h
```
string c++，自动管理内存，功能更丰富
string.h c，需手动处理内存，较低级
```
###  引用头文件
- <> 包含标准库或第三方库的头文件
- "" 用于包含自定义的头文件或项目中的其他模块的头文件


### 暂停
- windows
    ```
    #include <cstdlib> // 包含 system 函数的头文件
      system("pause");
    ```
- linux
    ```
    std::cout << "Press Enter to continue...";
    std::cin.get();

    ```


## makefile
- makefile 中一条语句这样： .c.o： gcc -c -o $*.o $<

```
.c.o:
这句话的意思就是 %.o : %.c
也就是说，所有的.o文件，依赖于对应的.c文件
比如有三个a.c b.c c.c
那么就会有 a.o b.o c.o
a.o : a.c
b.o : b.c
c.o : c.c
这是makefile依赖的一种简写方法。makefile的依赖关系有很多种写法。这是其中一种。
```

## 十进制-二进制

```
要把一个十进制数转换为二进制数，可以使用以下步骤：
将十进制数除以 2，得到商和余数。
把余数记录下来，然后把商作为新的十进制数重复第一步，直到商为 0。
把记录的余数倒序排列起来，就是这个十进制数对应的二进制数。
例如，将十进制数 19 转换为二进制数：
19 ÷ 2 = 9 余 19 ÷ 2 = 4 余 14 ÷ 2 = 2 余 02 ÷ 2 = 1 余 01 ÷ 2 = 0 余 1
所以 19 的二进制数为 10011。
```

## 常用工具

CodeBlocks - 下载带 mingw 的安装文件，100 多 M 大小

vscode -

clion -

cfree -

devc++ -

## gcc编译过程
    - `gcc -E main.c -o main.i` 预处理:对代码宏展开
    - `gcc -S main.i -o main.s` 编译 ->汇编
    - `gcc -c main.s -o main.o` 汇编 ->二进制
    - `gcc main.o -o hello` 链接，成为可执行文件

## [常用关键字](./keyword.md)


- `函数模板`
- 两个值交换
    
    ```
    加减法交换
     a = a + b;
      b = a - b;
      a = a - b;
    
    异或运算交换
      a = a ^ b;
      b = a ^ b;
      a = a ^ b;
    ```
    

a = a ^ b;：将变量 a 和 b 的值进行异或操作，并将结果赋给 a。异或操作的特性是，对于同一个位，如果两个操作数相应位上的数值相同，则该位结果为 0；如果两个操作数相应位上的数值不同，则该位结果为 1。因此，通过异或操作，a 中存储了 a 和 b 值的异或结果。

b = a ^ b;：将变量 a 和上一步中得到的 a ^ b 进行异或操作，并将结果赋给 b。这个步骤实际上是在将异或结果与原始的 b 进行异或操作，即 a ^ b ^ b，由于异或操作满足交换律和结合律，所以结果是 a ^ 0，即 a 的值。因此，现在 b 中存储了原始的 a 的值。

a = a ^ b;：将上一步中得到的 b（原始的 a 的值）和现在的 a 进行异或操作，并将结果赋给 a。这一步实际上是将 a ^ b ^ a 进行异或操作，最终结果是 b ^ 0，即 b 的值。因此，现在 a 中存储了原始的 b 的值。

void swap(int *p1, int* p2) { *p1 =* p1 ^ *p2;* p2 = *p1 ^* p2; *p1 =* p1 ^ *p2; }

```

```c
// 函数模板
template <typename T>
T getMax(T a, T b) {
  return (a > b) ? a : b;
}
```

- union、struct、class
    - 结构体适合用于表示有不同数据类型的组合对象，每个成员独立存储和访问。
    - 联合适合用于在同一内存位置存储不同类型的数据，各成员共享存储空间。
    - 类是一种更高级的数据结构，可以封装数据和行为，提供更丰富的功能。

### 笔记

C:Files2022.2.5++.exe

- 找到 cmake.exe 设为环境变量
- cmake –build cmake-build-debug –target untitled -j 22

### vscode使用
- 新建文件main.cpp
```
#include <bits/stdc++.h>
using namespace std;
signed main(){
    cout << "hello" << endl;
}
```
- vscode默认命令行位powershell ，有问题,需改为cmd;
    - 点击vscode命令行右边+ 下拉菜单改为cmd
- 执行 g++ main.cpp a.exe
`#define int int64_t` 定义int为64位整数

### 开源库
- https://github.com/mstorsjo/fdk-aac 开源AAC编码器里音质最好的
- https://www.antisip.com/download/exosip2/ 
- https://opus-codec.org/release/stable/2019/04/12/libopus-1_3_1.html
- 

https://github.com/ty6815/AvStackDocs/tree/52c1e04511d3c0908b7028c47566debb63202ae9/stream%20protocol/gb28181/%E5%9B%BD%E6%A0%87%E4%BF%A1%E4%BB%A4%E6%8A%93%E5%8C%85%E7%A4%BA%E4%BE%8B

- #pragma once 为了避免同一个文件被include多次
