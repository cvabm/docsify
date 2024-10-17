# c标准库
C 语言标准库是一组预先编写好的函数，它们随着 C 语言一起提供，用于执行常见的任务，如输入输出、字符串处理、数学计算、时间处理、文件操作等。以下是 C 语言标准库中的一些主要部分：
```
stdio.h
string.h
math.h
time.h
stdlib.h
ctype.h 
assert.h
float.h
stdarg.h
unistd.h
dirent.h
pthread.h
signal.h
complex.h
stdint.h
stdbool.h

locale.h 国际化
limits.h 
stddef.h size_t 等变量和宏
<sys/prctl.h>   prctl(PR_SET_NAME, "main"); 设置进程名称为main
```
- `static_cast<char>(tolower(ch))` 强转






1. **标准输入输出库（stdio.h）**：

   * `printf`、`scanf`、`fprintf`、`fscanf`、`sprintf`、`sscanf` 等函数用于格式化输入输出。

2. **字符串处理库（string.h）**：

   * `strcpy`、`strncpy`、`strlen`、`strcmp`、`strncmp`、`strstr`、`strcat`、`strncat` 等函数用于字符串操作。

## string.h
- `strcpy` 拷贝字符串
```c
    char src[] = "aaaaa";
    char dest[5];  //报错，加上字符串后\0字符总共6位

    strcpy(dest, src);
    printf("Copied string: %s\n", dest);
```
- `strcat`
```c
  char str1[50] = "Hello"; //必须设置数组大小
    char str2[] = ", World!";

    strcat(str1, str2);
    printf("Concatenated string: %s\n", str1);
```
- `strcmp`
```c
  int result = strcmp(str1, str2);
    if (result == 0) {
        printf("Strings are equal\n");
    }

```
- `srchr` 查找
```c
    char *ptr = strchr(str, 'o');
    if (ptr != NULL) {
        printf("First occurrence of 'o' found at position: %ld\n", ptr - str);
    }

```





3. **数学库（math.h）**：

   * 提供了三角函数、指数和对数函数、幂函数、圆周率等数学计算函数。

4. **时间处理库（time.h）**：

   * `time`、`difftime`、`asctime`、`ctime`、`gmtime`、`localtime`、`mktime` 等函数用于处理时间和日期。

5. **动态内存分配库（stdlib.h）**：

   * `malloc`、`calloc`、`realloc`、`free` 等函数用于动态内存分配和管理。
   * `atoi`、`atol`、`atof`、`itoa` 等函数用于字符串和数字之间的转换。
   * `rand`、`srand` 等函数用于生成随机数。

6. **字符处理库（ctype.h）**：

   * 提供了字符类型检查和转换函数，如 `isalpha`、`isdigit`、`toupper`、`tolower` 等。

7. **断言库（assert.h）**：

   * `assert` 函数用于调试目的，检查程序中的条件是否为真。

8. **浮点数学库（float.h）**：

   * 定义了浮点数的处理限制和精度。

9. **变量参数库（stdarg.h）**：

   * 允许函数接受可变数量的参数。

10. **系统调用库（unistd.h，仅限 Unix/Linux）**：

    * 提供了访问操作系统服务的函数，如 `read`、`write`、`close`、`fork`、`exec` 等。

11. **目录和文件系统库（dirent.h，仅限 Unix/Linux）**：

    * 提供了目录遍历函数，如 `opendir`、`readdir`、`closedir`。

12. **多线程库（pthread.h，仅限 Unix/Linux）**：

    * 提供了多线程编程的支持。

13. **信号处理库（signal.h）**：

    * 提供了信号处理的函数，如 `signal`、`raise`。

14. **复数数学库（complex.h，C99 标准）**：

    * 提供了复数的数学计算函数。

15. **固定宽度整数库（stdint.h，C99 标准）**：

    * 定义了固定宽度的整数类型。

16. **布尔类型库（stdbool.h，C99 标准）**：

    * 定义了布尔类型 `bool`、`true` 和 `false`。

这些库提供了大量的函数和宏定义，极大地简化了程序的编写。在使用这些库中的函数时，通常需要在程序中包含相应的头文件。